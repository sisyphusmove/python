# Python 03

> 문자열 분리

- 첨자

  - 문자의 위치
  - 리스트 개념으로 사용가능

  ```python
  s="python"
  print(s[2])
  >>>
  t
  ```

- 슬라이스

  - 범위 지정하여 부분 문자열을 추출
  - [begin,end,step]

  ```python
  file = "20180919-104830.jpg"
  print("촬영 날짜 : " + file[4:6] + "월 " + file[6:8] + "일")
  print("촬영 시간 : " + file[11:13] + "시 " + file[13:15] + "분")
  print("확장자 : " + file[16:20])
  >>>
  촬영 날짜 : 09월 19일
  촬영 시간 : 48시 30분
  확장자 : jpg
  ```

- 메소드

  - 클래스에 소속된 함수
  - 객체에 특화된 작업 수행

  ```python
  p="I like python better than java"
  
  print(len(p)) # 문자열 길이 출력
  
  # 검색 메소드
  print(p.find('e')) # 맨 앞에서부터 e를 찾아 index 값 반환
  print(p.rfind('e')) # 맨 뒤에서부터 e를 찾아 index 값 반환
  print(p.index('e')) # find 메소드와 동일
  print(p.count('e')) # e의 총 개수
  
  >>>
  30
  5
  18
  5
  3
  --------------------
  
  #in - 특정 문자가 문자열에 들어있는지 확인
  print('a' in p)
  print('b' not in p)
  >>>
  True
  False
  
  # 진위 여부 메소드
  print(p.isalpha()) # 모든 문자가 알파벳인지
  print(p.islower()) # 모든 문자가 소문자인지
  print(p.isupper()) # 모든 문자가 대문자인지
  print(p.isalnum()) # 모든 문자가 알파벳 또는 숫자인지
  print(p.isnumeric()) # 모든 문자가 숫자인지
  
  >>>
  False
  False
  False
  False
  False
  
  # 출력 메소드 (원본 문자형이 변경되는 것은 아니다.)
  print(p.upper()) # 전부 대문자로 출력. 
  print(p.lower()) # 전부 소문자로 출력.
  print(p.swapcase()) 
  print(p.capitalize()) # 첫 글자만 대문자
  print(p.title()) #각 단어 첫 글자 대문자
  
  >>>
  I LIKE PYTHON BETTER THAN JAVA
  i like python better than java
  i LIKE PYTHON BETTER THAN JAVA
  I like python better than java
  I Like Python Better Than Java
  
  # 공백 제거 메소드
  s=" angel "
  print(s + "님")
  print(s.lstrip()+ "님") #왼쪽 공백제거
  print(s.rstrip()+ "님") #오른쪽 공백제거
  print(s.strip()+ "님") #모든 공백제거
  >>>
   angel 님
  angel 님
   angel님
  angel님
  
  #분할 메소드
  s="a,b,c,s,d,fsadf" #, 기준으로 요소로 묶어서 리스트로 출력
  print(s.split())
  >>>
  ['a,b,c,s,d,fsadf'] 
  
  
  #결합 메소드
  s=".-."
  print(s.join("파이썬 프로그래밍")) # 글자와 글자 사이에 s 문자열이 결합된다.
  >>>
  파.-.이.-.썬.-. .-.프.-.로.-.그.-.래.-.밍
  
  #대체 메소드
  s="java, web, python"
  print(s.replace('java','node.js')) #바꿀 단어 지정 , 새로운 단어 지정
  >>>
  node.js, web, python
  
  s="java\nweb\npython"
  print(s)
  print(s.replace('\n',''))
  print(s.replace('\n','<br/>').replace('j','a')) #체인으로 이어서 연속 변경가능
  >>>
  java
  web
  python
  javawebpython
  aava<br/>web<br/>python
  
  #정렬 메소드
  s='PYTHON'
  print(s+":"+str(len(s)))
  print(s.rjust(10)+":"+str(len(s.rjust(10)))) #rjust 오른쪽정렬
  print(s.ljust(10)+":"+str(len(s.ljust(10)))) #ljust 왼쪽정렬
  >>>
  PYTHON:6
      PYTHON:10
  PYTHON    :10
      
  s="""PYTHON is life 
    come togeter
    summer"""
  s3=s.splitlines() #줄 개행 메소드
  for line in s3:
      print(line.center(3)) # 줄마다 가운데 정렬
  >>>
  PYTHON is life 
    come togeter
    summer
  
  ```

- 포맷팅

  ```python
  s="%d년 %d월 %d일"
  for m in range (1,7):
      print(s % (2018, m, 1))
  >>>
  2018년 1월 1일
  2018년 2월 1일
  2018년 3월 1일
  2018년 4월 1일
  2018년 5월 1일
  2018년 6월 1일
  
  # %nd 포맷 : 자릿수 조정 기능
  
  price=[30,50,15000]
  for p in price:
      print("가격:%d원" % (p))
      print("가격:%7d원" % (p)) #7자리의 자릿수를 고정
  >>>
  가격:30원
  가격:     30원
  가격:50원
  가격:     50원
  가격:15000원
  가격:  15000원
  ```

- 튜플형 데이터

  ```python
  s1 = (100,200,300)
  print(s1)
  s2 = 100,200,300
  print(s2)
  s3 = 100
  print(s3)
  s4 = 100,
  print(s4)
  >>>
  (100, 200, 300)
  (100, 200, 300)
  100 #s3제외 모두 튜플형 자료다.
  (100,)
  ```

- 실수형 데이터

  ```python
  pie=3.14159265
  print("%10f" % pie)
  print("%10.8f" % pie) #소수점 아래 8자리까지 오른쪽 정렬하여 출력
  print("%10.5f" % pie) #소수점 아래 5자리까지 오른쪽 정렬하여 출력
  >>>
    3.141593
  3.14159265
     3.14159
  print("%-10.5f" % pie) # - :왼쪽 정렬하여 출력
  >>>
  3.14159
  
  ```



> ##### 리스트



- 자료의 집합

  - 리스트는 여러 개의 값을 집합적으로 저장

  - 요소(Element)

    - 리스트에 소속되는 각각의 값
    - 리스트에는 주로 같은 타입 요소를 모음

    ```python
    s=[0,1,2,3,4,5,6,7,8,9]
    s[2]=50
    print(s)
    s[2:5]=[10,20,30]
    print(s)
    s[6:8]=[100,200,300,400,500]
    print(s)
    >>>
    [0, 1, 50, 3, 4, 5, 6, 7, 8, 9]
    [0, 1, 10, 20, 30, 5, 6, 7, 8, 9]
    [0, 1, 10, 20, 30, 5, 100, 200, 300, 400, 500, 8, 9] #삽입의 효과
    ```

- 이중 리스트

  - 리스트의 요소로 리스트 넣어서 중첩 가능

    ```python
    s=[[1,2,3],[4,5],[6,7,8,9]]
    print(s[0])
    print(s[2][1])
    >>>
    [1, 2, 3]
    7
    ```

- 리스트 Comprehension

  - 수식 for 변수 in 리스트 if 조건

- 삽입

  - append, insert
  - 범위에 리스트 대입하여 여러 요소 한꺼번에 삽입가능

  ```python
  nums=[1,2,3,4]
  nums[2:2]=[90,92,93]
  print(nums)
  
  nums[2]=[90,92,93]
  print(nums)
  >>>
  [1, 2, 90, 92, 93, 3, 4] #범위(:)를 지정하면 정수로 추가된다
  [1, 2, [90, 92, 93], 92, 93, 3, 4] #범위를 지정안할 시 리스트 그대로 추가된다
  ```

- 삭제

  - remove(인수로 전달받은 요소값 찾아 삭제)
  - del (순서값 지정하여 삭제)
  - clear(리스트 모든 요소 삭제)
  - 빈 리스트 대입 (일정 범위 요소 전부 삭제  )

- 검색

  - index (특정 요소 위치 찾기)
  - count (특정 요소값의 개수 조사)

- 정렬

  - sort

    ```python
    result=[('hong',100,90),('goon',19,14),('lee',50,55)]
    print(result)
    result.sort(key=lambda element : element[1])  
    #lambda 1회성 함수 사용하여 기준을 첫번째 요소로 지정
    print(result)
    >>>
    [('hong', 100, 90), ('goon', 19, 14), ('lee', 50, 55)]
    [('goon', 19, 14), ('lee', 50, 55), ('hong', 100, 90)]
    ```

- 단일 데이터가 명함이라면 리스트는 명함을 모아두는 명함집



> ##### 튜플



- 불변 자료 집합

  - 튜플은 초기화한 후 편집할 수 없다는 점에서 리스트와 차이
  - 소괄호 사용하여 정의

- 두 개 이상 값을 반환

  - 내부에 요소 포함하는 튜플 사용

- 변수 다중 할당 가능

  ```python
  city, latitude, longitude = 'seoul', 37.541, 126.986
  print(city)
  print(latitude)
  print(longitude)
  >>>
  seoul
  37.541
  126.986
  ```


> ##### 딕셔너리



- 사용법 측면에서 리스트와 비슷

  - 리스트처럼 첨자를 이용해서 요소에 접근

- 딕셔너리는 문자열과 숫자를 비롯해서 변경이 불가능한 형식이면 어떤 자료형이든 사용

  - 딕셔너리의 첨자는 key
  - key가 가리키는 슬롯에 저장된 데이터가 value

  ```python
  dic = {}
  
  dic['파이썬'] = 'www.python.org'
  dic['마이크로소프트'] = 'www.microsoft.com'
  dic['애플']='www.apple.com'
  
  
  print(dic.keys()) # key값만 출력
  print(dic.values()) # value값만 출력
  print(dic.items()) #key & value를 한쌍의 tuple로 묶는다.
  
  >>>
  dict_keys(['파이썬', '마이크로소프트', '애플'])
  dict_values(['www.python.org', 'www.microsoft.com', 'www.apple.com'])
  dict_items([('파이썬', 'www.python.org'), ('마이크로소프트', 'www.microsoft.com'), ('애플', 'www.apple.com')])
  ```
