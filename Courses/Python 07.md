# 파이썬과 DB 연동

```PYTHON
import sqlite3

con=sqlite3.connect('user.db')
cursor=con.cursor()

print(con, "연결 성공")

cursor.execute("DROP TABLE IF EXISTS tblAddr") #테이블 삭제
cursor.execute("""CREATE TABLE tblAddr(
    name CHAR(10) PRIMARY KEY,
    phone CHAR(15),
    addr TEXT
)""") #테이블 생성

print("테이블 생성 성공")

cursor.execute("INSERT INTO tblAddr VALUES ('김상형','123-4567','오산')")
cursor.execute("INSERT INTO tblAddr VALUES ('한경은','242-2527','부산')")
cursor.execute("INSERT INTO tblAddr VALUES ('백광민','145-4357','경산')")
print("테이블 추가 성공")

con.commit()

cursor.close()
con.close()
```

```PYTHON
import sqlite3

con=sqlite3.connect('user.db')
cursor=con.cursor()



# DML - CRUD(insert, select, update, delete)
sql1='SELECT * FROM tblAddr'
table=cursor.execute(sql1)

# fetchall(), fetchone(), fetchmany()
table = cursor.fetchall() #테이블 내의 자료 모두 가져오기
for row in table:
    print(row)
print(type(table))
print(table)

>>>

('김상형', '123-4567', '오산')
('한경은', '242-2527', '부산')
('백돌진', '145-4357', '경산')
<class 'list'>
[('김상형', '123-4567', '오산'), ('한경은', '242-2527', '부산'), ('백돌진', '145-4357', '경산')]

```

- fetchall 메소드

  - 모든 레코드 한꺼번에 읽어 리스트로 반환

- fetchone 메소드

  - 순서대로 읽기


> ##### 실습



- 환경설정
  1. docker 설치 

  - docker 클라우드 상에서의 mysql 이미지를 다운받아서 컨테이너로 만든 뒤 그 컨테이너 상에서 작업하기 위함. (별도의 환경설정이 필요없음) 

  2. mysql workbench 설치 (DB 관리 툴)


- 
  cmd 설정 (컨테이너 상에서 test_python DB를 생성)


1. docker run -d -p 3306:3306 -e MYSQL_ALLOW_EMPTY_PASSWORD=true --name mysql mysql:5.7
2. docker exec -it mysql /bin/bash
3. mysql -uroot
4. show databases; -> create database test_python;
5. quit -> exit
6. pip install PyMySQL
7. pip list 



- python과 mysql 연동

```python
import pymysql
#1.connection

conn=pymysql.connect(host='127.0.0.1', user='root', password='', db='test_python', charset='utf8')

cursor = conn.cursor()
```



- workbench 에서 테이블 생성 (DOCKER 컨테이너 상의 DB를 사용)

![](C:\Users\baek\Desktop\capture-20180928-144854.png)



- python에서 해당 테이블로 insert

  ```python
  import pymysql
  #1.connection
  
  conn=pymysql.connect(host='127.0.0.1', user='root', password='', db='test_python', charset='utf8')
  
  cursor = conn.cursor()
  
  insertSql="""INSERT INTO member(id,pwd,name,reg_date) values(
      'admin','1234','Administrator',now()
  )"""
  
  cursor.execute(insertSql)
  conn.commit()
  ```


- workbench에서 삽입된 것 확인

![](C:\Users\baek\Desktop\15.png)



- python - 입력형 select 쿼리생성

```python
import pymysql

conn=pymysql.connect(host='127.0.0.1', user='root', password='', db='test_python', charset='utf8')

cursor = conn.cursor()

inputId= input('아이디를 입력하세요=>')
inputPwd=input('비밀번호를 입력하세요=>')

selectSql="SELECT * FROM member WHERE id='" + inputId + "'AND pwd='" + inputPwd + "'"
print(selectSql)

cursor.execute(selectSql)
row=cursor.fetchone()

if row == None:
    print("로그인 실패! ID나 PWD가 잘못 되었습니다.")
else:
    print('로그인 성공!', row)

cursor.close()
conn.close()


>>>
아이디를 입력하세요=>admin
비밀번호를 입력하세요=>1234
SELECT * FROM member WHERE id='admin'AND pwd='1234'
로그인 성공! (1, 'admin', 'Administrator', '1234', datetime.datetime(2018, 9, 28, 5, 36, 1))

```

- 파라미터 전달 방식으로 쿼리형 작성 (SQL인젝션 공격 방지)

  ```python
  insertSql = 'INSERT INTO member(id,pwd,name,reg_date) VALUES(%s,%s,%s,NOW())'
  cursor.execute(insertSql,('user1','1111','TEST\'s USER'))
  conn.commit()
  
  selectSql = 'SELECT * FROM member WHERE id=%s AND pwd=%s'
  cursor.execute(selectSql, (inputId,inputPwd))
  ```

- 함수없이 데이터 쿼리 명령어만으로 총점 및 내림차순 출력하기

  ```sql
  select idx, name, kor, eng, mat, (kor+eng+mat) as total
  from test_python.sungjuk order by kor desc;
  ```

  ![](C:\Users\baek\Desktop\capture-20180928-155334.png)

  ```sqlite
  select idx, name, kor, eng, mat, (kor+eng+mat) as total,
  (kor+eng+mat)/3 as average
  from test_python.sungjuk order by kor desc;
  ```

  ![](C:\Users\baek\Desktop\aver.png)

- 딕셔너리 형태의 커서 사용 -> 직관적 데이터 관리 가능

  ```python
  cursor = conn.cursor(pymysql.cursors.DictCursor) 
  ```

  ```python
  def displaySungjuk():
      #DB에서 데이터 조회
      rows=selectList()    
      for row in rows:
          print("{0}\t{1}\t{2}\t{3}\t{4}\t{5}".format(
              row['name'],row['kor'],row['eng'],row['mat'],row['total'],row['average']
          ))
  
  
  def selectList():
      selectSql="""SELECT 
          idx,name,kor,eng,mat,(kor+eng+mat) as total, (kor+eng+mat)/3 as average
      FROM sungjuk 
      ORDER BY total DESC"""
      
      cursor.execute(selectSql)
      rows=cursor.fetchall()
      return rows
  ```



- 참고 URL

  https://blog.hanumoka.net/2018/04/29/docker-20180429-docker-install-mysql/