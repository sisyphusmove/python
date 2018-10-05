# Python 01

> #### 들어가기 전



- stackoverflow.com : 코딩에 대한 질문과 답을 주고 받는 사이트



- 엔지니어의 단계

  1. 죽은 프로그래머 -> 다익스트라, 도널드 커누스

  2. 성공적인 프로그래머 -> 빌 게이츠, 존 카맥 (게임엔진 무료 배포), DHH (루비 제작자)

  3. 유명한 프로그래머

  4. 일하는 프로그래머

  5. 평균적인 프로그래머

  6. 아마추어 프로그래머

  7. 알려지지 않은 프로그래머

  8. 나쁜 프로그래머 -> 만든 코드가 협업에 방해가 되는 경우


- 질문하기 전에 왜 에러가 나는 지 다시 한번 고민해보기



> #### 파이썬



- 프로그래밍 언어 - 프로그램 작성하는 도구의 일종

  - 컴파일 언어
    - 모든 명령을 일괄 번역, 실행 
    - 속도 빠른 반면 구조 복잡
  - 인터프리터 언어
    - 명령어 만날 때마다 즉시 번역하여 실행
    - 속도 느리지만 단순하고 쉬움.


- 파이썬 소개
  - Guido van Rossum이 1991년 개발
  - 현재 2.x 세대와 3.x 세대 공존
  - 여러 가지 변형 존재
  - 주요 특징
    1. 배우거나 사용하기 쉬움
    2. 어느 OS에서나 사용 가능
    3. 기본 패키지만으로도 각종 작업 처리 가능
    4. 객체지향적 & 클래스 지원
    5. C언어와의 접착성이 좋아 혼합 프로그래밍 가능
  - 활용 분야
    1. 유틸리티 제작
    2. 웹 프로그래밍
    3. 임베디드
    4. 데이터베이스 작성
    5. 프로그래밍 교육



> #### 파이썬 실습



- 대화식 모드 (Interactive)
  - console 명령 입력시 즉시 값이 출력
  - 복잡한 코드 작성시 불편

```python
2+3
>> 5
```

```python
for y in range(1,10): #콜론-코드의 다음 줄이 있을 것이라는 표시. 
    for x in range(y):
        print('*', end = '') #x의 영역
    print() #y의 영역. 들여쓰기 라인만 맞으면 중괄호가 필요가 없다.
```



- 스크립트 모드

  - 저장 기능으로 인해 수정 및 편집 용이
  - 파이썬 기본제공 IDLE만으로도 문법 실습에 충분

- 소스의 형식

  - 일정한 규칙에 따라 스크립트 파일 코드를 작성
  - 들여쓰기(Indent)
    - [Tab] 혹은 4개 공백
    - 조건문, 반복문 등 여러 개 문장이 블록 구성하는 경우 사용
  - 한 줄에 하나의 명령을 작성
  - 대문자와 소문자를 구분
  - '#' 문자로 주석 처리 가능

- 출력

  - print 명령
    - 여러 개 출력 결과를 공백이나 구분자(separator) 사용하여 구별

```python
print(a, b, seq = ',')
12, 34
```

```python
s = '서울'
d = '대전'
g = '대구'
b = '부산'
print(s, d, g, b, sep=', ')

>>>서울, 대전, 대구, 부산
```

- input 명령
  - 변수 = input('질문 내용')
    - 입력 후 엔터를 누르면 변수에 입력값이 대입된다
    - input은 기본적으로 문자형이다

```python
a = input('당신의 나이는?')
print('당신의 나이는 '+a+'살입니다.')
>>> 당신의 나이는?
# 15 입력 후 엔터
>>> 당신의 나이는 15살입니다.
```

```python
a = int(input('당신의 나이는?')) #casting을 통해 input의 자료형을 정수형으로 변환.
print('당신의 5년 뒤는',a+5,'살입니다')
>>> 당신의 나이는?
# 45 입력
>>> 당신의 5년 뒤는 50 살입니다.
```

- 변수

  - 메모리에 이름 붙이고, 그 메모리 할당 공간에 값을 저장하는 것
  - 규칙
    - 키워드(if,in,range 등), 내장 함수(print), 표준 모듈명은 사용 불가
    - 모든 명칭은 대소문자를 구분
    - 알파벳, 밑줄문자, 숫자 등으로 구성 (공백, +, - 등 사용 불가)
    - 첫 글자로 숫자 사용 불가
    - 한글이나 한자 사용 불가

  - 상수(const)를 쓰는 이유 = 바뀌지 않아야 하는 고정 데이터의 변경 방지

  - 파이썬 변수는 별도 타입(형)을 지정하지 않음

    - 최초 대입하는 값에 의해 자료형이 결정된다. (동적)


- 명칭 (Identifier)

  - 변수가 다른 것과 구분되도록 이름 붙인 것


- 정수형

  - 가장 간단한 수치형

  - 소수점 이하 값은 표현 불가

  - 10진수 아닌 정수는 앞에 접두 붙여 진법 지정

    - 16진법 (0x) / 8진법(0o) / 2진법 (0b)

      ```python
      a=0x1a
      print(a)
      >>>26
      ```

      ```python
      print(int('10'))
      print(hex(26)) # 26의 16진수
      print(oct(26)) # 26의 8진수
      print(bin(13)) # 26의 2진수
      
      >>>
      10
      0x1a
      0o32
      0b1101
      ```

- 실수형

  - 소수점 이하 정밀한 값 표현
  - 아주 크거나 작은 값은 부동 소수점 방식으로 표기

- 문자형

  - 일련의 문자를 따옴표로 감싸 나열한 것
  - 각종 문자, 기호, 숫자 등 포함 가능

- 확장열

  - 따옴표 안에 오기 힘든 다양한 문자들

  - \ 문자 뒤에 특별한 기호로 표기 (\n,\t, 등)

    ```python
    print("I SAY \"HELP\" TO YOU") # \" : "출력
    >>> I SAY "HELP" TO YOU
    ```

    ```python
    a="first\nsecond" #\n : 다음 줄로 개행
    print(a)
    >>> first
    >>> second
    ```

  - 긴 문자열

    ```python
    s = "안녕하세요. \
    파이썬 첫시간이에요. \
    문자열과 숫자열에 대해서 공부한다." #화면 상에서는 개행을 해서 입력. But 출력은 붙여서.
    print(s)
    >>> 안녕하세요. 파이썬 첫시간이에요. 문자열과 숫자열에 대해서 공부한다.
    ```

    ```python
    s = """안녕
    파이썬
    공부할게요.""" # 3따옴표 : 특별한 문자없이 개행 공백을 인식시킬 수 있다.
    print(s)
    >>>
    안녕
    파이썬
    공부할게요.
    ```

    ```python
    s= ("korea"
        "japan"
        "2002")
    print(s)
    s="korea" "japan" "2002"
    print(s) 
    # 두가지 변수의 결과값은 같다. 그러나 시작과 끝이 알아보기 쉬운 것은 괄호형식이다.
    >>>
    koreajapan2002
    koreajapan2002
    ```

    ```python
    print('a')
    print(ord('a')) # 소문자 a의 아스키 코드 값.
    print(chr(97)) # 아스키 코드값을 문자로 치환.
    >>>
    a
    97
    a
    ```

    ```python
    #A~Z ASCII 값 출력
    for c in range(ord('A'),ord('Z')+1):
        print(chr(c),'=',c)
    >>>
    A = 65
    B = 66
    C = 67
    D = 68
    E = 69
    F = 70
    G = 71
    H = 72
    I = 73
    J = 74
    K = 75
    L = 76
    M = 77
    N = 78
    O = 79
    P = 80
    Q = 81
    R = 82
    S = 83
    T = 84
    U = 85
    V = 86
    W = 87
    X = 88
    Y = 89
    Z = 90
    
    #A~Z ASCII 값 한 줄로 출력
    for c in range(ord('A'),ord('Z')+1):
        print(chr(c),'=',c, end='') #print함수의 기본개행을 생략시킨다.
    >>>A = 65B = 66C = 67D = 68E = 69F = 70G = 71H = 72I = 73J = 74K = 75L = 76M = 77N = 78O = 79P = 80Q = 81R = 82S = 83T = 84U = 85V
    = 86W = 87X = 88Y = 89Z = 90
    ```


- 함수

  - 글자 뒤에 괄호 있는 경우
  - 괄호에 문자열 등 자료 입력


- 문자열 반복 연산자 / 문자열 선택 연산자

```python
print("안녕"*3) #문자열 반복 연산
>>>안녕안녕안녕

print("안녕"[0])
print("안녕"[1]) #문자열 선택 연산 / 문자열을 배열로 취급
>>>
안
녕
```

- 배열

  - 리스트 : 추가,수정,삭제,조회

  - 튜플 : 조회만 가능

    ```python
    #리스트 형태
    member = ['사과','바나나','오렌지','포도']
    print(member[0]) #사과
    print(member[1],member[2])  #바나나, 오렌지
    print(member[2:3])
    >>>
    사과
    바나나 오렌지
    ['오렌지']
    
    for m in member:
        print(m)
    >>>
    사과
    바나나
    오렌지
    포도
    ```

- 산술 연산자

  - +,-,*,/
  - ** 거듭제곱, // 정수나누기 , % 나머지
  - +=,-=,*= 복합연산자 : 우변의 값이나 수식을 계산하여 좌변에 대입.


- round 함수

  - 반올림 연산 시 사용

    ```python
    print(int(2.54)) #str -> int, float(큰) -> int(작은) (데이터 손실)
    print(round(2.54))
    print(round(2.54, 1))
    print(round(12345, -3))
    >>>
    2
    3
    2.5
    12000
    
    score=78.1234
    print(round(score,2))
    >>>
    78.12
    ```

- if 조건문

  - 비교연산자 (==,!=,<,>,<=.>=)

    - 두 값의 상등 여부나 대소관계 비교하여 참, 거짓 반환

    - if문이 이 평가 결과에 따라 명령 실행 여부 결정

      ```python
      a=3
      if a==3: #비교 연산
          print("true")
      >>>
      true
      ```

  - 논리연산자

    - 두 개 이상의 조건을 한꺼번에 점검하는 경우 사용

      ```python
      a=3
      b=4
      if a==3 and b==4:
          print("ok")
      >>>
      ok
      ```

  - 블록 구조

    - 블록: 한꺼번에 실행되는 명령 묶음

  - else 문

    - 조건 진위에 따라 실행할 명령을 선택
    - 각 자리에 2개 이상의 명령을 넣을 수 있다.

  - elif 문

    - else if의 약어. if else문에서 조건 불만족 시 세부 조건을 추가 점검

      ```python
      age = 20
      if age <19:
          print('ok')
      elif age > 22:
          print('yes')
      else:
          print('no')
      >>> no
      ```

  - 반복문, 분기문 연습

    - while문과 if문을 활용한 랜덤 넘버 맞추기 게임

      ```python
      import random
      com_num = random.randrange(1,100) # 1~100까지 랜덤수 생성
      count = 0
      score = 0
      print(com_num)
      while True: # while 무한반복문
      
          user_num=int(input("숫자를 입력하세요(1~100)"))
          count+=1 #정답 입력횟수
      
          if user_num < 1 or user_num > 100:
              print("1~100 사이의 숫자를 입력하세요") #숫자 유효성 검사
          else:
              if com_num < user_num:
                  print("보다 작은 숫자를 입력해보세요.")
                  
                  
              elif com_num > user_num:
                  print("보다 큰 숫자를 입력해보세요")
              else :
                  print("정답입니다")
                  break # 조건 만족 시, 근접해 있는 Loop 실행 종료
      print("======================")
      print("축하합니다. 총",count,"번만에 맞추었습니다.")
      ```

    - 가위바위보 게임

      ```python
      # 가위바위보 게임 만들기
      # 지면 게임 종료 및 상금 상실
      # 비기면 다시 입력
      # 이기면 게임 계속 or 종료
      # 게임 계속시 상금 x 2
      # 게임 종료시 해당 상금만 받도록
      
      import random
      
      cnt=0 # 상금 총액
      a=1 # 상금 액수
      while True :
          com=random.randrange(1,3)
          print(com)
          user=int(input("가위(1),바위(2),보(3)"))
          if user<1 or user>3:
              print("다시 입력하세요")
              continue # 가장 인접한 Loop의 조건식으로 이동
          else:
              #게임 룰 계산
              if com == 1: #컴퓨터가 가위일 경우
                  if user == 2:
                      print("you win")
                      cnt=cnt+a
                      ask=input("regame?(y or n)")
                      if ask == 'y':
                          a=a*2
                          continue
                      elif ask == 'n':
                          print("your point is",cnt)
                          break
                  elif user ==3:
                      print("you lose your point is",cnt)
                      break
                  else:
                      print("draw, regame")
                      continue
              elif com == 2: #컴퓨터가 바위일 경우
                  if user == 3:
                      print("you win")
                      cnt=cnt+a
                      ask=input("regame?(y or n)")
                      if ask == 'y':
                          a=a*2
                          continue
                      elif ask == 'n':
                          print("your point is",cnt)
                          break
                  elif user ==1:
                      print("you lose your point is",cnt)
                      break
                  else:
                      print("draw, regame")
                      continue
              elif com == 3: #컴퓨터가 보일 경우
                  if user == 1:
                      print("you win")
                      cnt=cnt+a
                      ask=input("regame?(y or n)")
                      if ask == 'y':
                          a=a*2
                          continue
                      elif ask == 'n':
                          print("your point is",cnt)
                          break
                  elif user ==2:
                      print("you lose your point is",cnt)
                      break
                  else:
                      print("draw, regame")
                      continue
      ```




