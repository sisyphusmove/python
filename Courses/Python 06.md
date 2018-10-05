# 파일 입출력

- 입출력 위치

  - 순차접근
  - 임의접근

  ```python
  f=open('my_test.txt','rt')
  f.seek(12,0)  #(건너뛸 byte수,{0,1,2}) 0=처음부터/1=현재위치/2=뒤에서부터
  print(f.tell()) #현재 몇번째 위치(포인터)인지 출력
  text=f.read()
  f.close()
  print(text)
  >>>
  12
  34567890123456
  ABCDEFGHIJKLMNOPQRSTUVWXYZ
  HELLO
  ```



- 내용 추가

  - a 모드 : 기존 내용 그대로 유지하고 뒤에 덧붙임

    ```python
    f=open('my_test.txt','at')
    f.write("\n\n파이썬 파일읽기 쓰기 예제")
    f.close()
    >>>
    ABCDEFGHIJKLMNOPQRSTUVWXYZ
    HELLO
    
    파이썬 파일읽기 쓰기 예제
    ```

  - w 모드: 파일 이미 있는 경우 덮어씀

    ```python
    f=open('my_test.txt','wt')
    f.write("\n\n파이썬 파일읽기 쓰기 예제")
    f.close()
    >>>
    
    
    파이썬 파일읽기 쓰기 예제s
    ```

- 파일 복사

  - 실행 시 <원본 파일명> <복사될 파일명>

    - ex) filedemo_02.py my_text.txt new_test.txt

  - 읽기

    - read(), readlines()

  - 쓰기

    - write()

  - shutil.copy(a,b) : 디렉토리를 복사한다. 서브 디렉토리까지 전부 복사한다.

  - shutil move(a,b) 

    ```python
    import shutil
    shutil.copytree('source','target_new')
    shutil.move('source','new source')
    print('파일 복사 성공')ㅇ
    ```

- SQLite

  - 데이터베이스 관리시스템(DBMS)
  - 무료 이용 가능
  - WWW.SQLITE.ORG



- 테이블 생성

  - 스크립트로 DB생성
  - connect 메소드
    - DB파일과 연결하여 데이터베이스 열기
  - cursor 메소드
    - 커서 객체 구함
  - execute 메소드
    - SQL 명령 수행

- DB 연동

  ```PYTHON
  import sqlite3
  
  con=sqlite3.connect('user.db')
  cursor=con.cursor()
  print(con, "연결 성공")
  cursor.close()
  con.close()
  >>>
  <sqlite3.Connection object at 0x000001BB2D17B2D0> 연결 성공
  ```