# Python 02

> 반복문

- while 반복문

  - 조건이 만족하는 동안 명령을 계속 실행

  - 루프

    - 반복적으로 처리하는 명령

      ```python
      student=1
      while student <=5:
          print(student, "번 학생의 성적을 처리한다")
          student +=1
      >>>
      1 번 학생의 성적을 처리한다
      2 번 학생의 성적을 처리한다
      3 번 학생의 성적을 처리한다
      4 번 학생의 성적을 처리한다
      5 번 학생의 성적을 처리한다
      ```

      ```python
      num=1
      sum=0
      while num <=100:
          sum+=num
          num+=1
      print("1~100까지의 합", sum)
      >>>
      1~100까지의 합 5050
      ```

      ```python
      num=1
      sum=0
      while num <=100:
          sum+=num
          num+=2
      print("1~100까지 중 홀수의 합", sum)
      >>>
      1~100까지 중 홀수의 합 2500
      ```

      ```python
      # 인수 분해
      user = int(input('숫자 입력'))
      for m in range (int(user/2)+1):
          if m == 0:
              continue
          if user % m == 0:
              print(m)
      >>>
      숫자 입력16
      1
      2
      4
      8
      ```

  - 반복문은 코드 변경이 쉬움

    - 조건식이나 출력문 변경 통해 수정


- for 반복문

  - 컬렉션 요소 순서대로 반복하면서 루프 명령 실행

    ```python
    for student in [1,2,3,4,5]:
        print(student, "번 학생의 성적을 처리한다.")
    >>>
    1 번 학생의 성적을 처리한다.
    2 번 학생의 성적을 처리한다.
    3 번 학생의 성적을 처리한다.
    4 번 학생의 성적을 처리한다.
    5 번 학생의 성적을 처리한다.
    ```

  - range 명령

    - 일정 범위 리스트를 만들고 그 요소를 반복

      ex) 1~100 -> for a in range (1,101):

- break

  - 반복문을 끝내는 명령

  - 특정한 조건에 따라 루프 끝내고 다음 명령으로 이동

- continue

  - 현재 루프만 건너뛰고 나머지는 계속 반복 수행
  - 현재 반복을 중지하고 루프 선두의 조건 점검한 후 반복 재개

- 이중 루프

  - 루프 안 명령 자리에 또 다른 루프가 들어가 중첩된 것

    ```python
    #구구단 예제
    for dan in range (2,10):
        print(dan, " 단")
        for hang in range(1,10):
            print(dan, "*", hang, "=", (dan*hang))
            # print("%d * %d = %d" % (dan,hang,(dan*hang))) -> 패턴 모형, 동일 결과
            # print("{} * {} = {}".format(dan,hang,(dan*hang)))
        print()
    ```

    ```python
    #구구단 예제 세로 출력
    for n in range (1,10):
        for m in range (2,10):
            print("%d*%d=%2d" % (m,n,(m*n)), end='\t')
        print()
    >>>
    2*1= 2  3*1= 3  4*1= 4  5*1= 5  6*1= 6  7*1= 7  8*1= 8  9*1= 9
    
    2*2= 4  3*2= 6  4*2= 8  5*2=10  6*2=12  7*2=14  8*2=16  9*2=18
    
    2*3= 6  3*3= 9  4*3=12  5*3=15  6*3=18  7*3=21  8*3=24  9*3=27
    
    2*4= 8  3*4=12  4*4=16  5*4=20  6*4=24  7*4=28  8*4=32  9*4=36
    
    2*5=10  3*5=15  4*5=20  5*5=25  6*5=30  7*5=35  8*5=40  9*5=45
    
    2*6=12  3*6=18  4*6=24  5*6=30  6*6=36  7*6=42  8*6=48  9*6=54
    
    2*7=14  3*7=21  4*7=28  5*7=35  6*7=42  7*7=49  8*7=56  9*7=63
    
    2*8=16  3*8=24  4*8=32  5*8=40  6*8=48  7*8=56  8*8=64  9*8=72
    
    2*9=18  3*9=27  4*9=36  5*9=45  6*9=54  7*9=63  8*9=72  9*9=81
    ```

- 리스트

  - 여러 개의 값을 나타낼 수 있게 하는 자료형

    - 리스트, 딕셔너리 등

  - 대괄호 []로 생성

  - 각각 사용하려면

    - 리스트 바로 뒤 대괄호 입력

    - 내부에 숫자 (인텍스, Index) 넣음

      ```python
      #리스트 선언
      array = [1,2,3,4,5]
      print(array[0]) #인덱스값 입력 , 1출력
      print(array[-1]) # -1은 제일 마지막 값. 5출력
      ```

  - 리스트 연산자

    - 문자열 경우와 비슷한 연산자와 함수 사용

      ```python
      #리스트 선언
      array = [1,2,3,4,5]
      array2 = [3,4,5,6,7]
      print("array + array2 = ", array+array2) #연결 연산자로 두 리스트를 연결
      >>>
      array + array2 =  [1, 2, 3, 4, 5, 3, 4, 5, 6, 7]
      ```

  - 리스트에 요소 추가하기

    - <리스트>.append(<요소>) #리스트의 뒤에 요소를 추가
    - <리스트>.insert(<위치>,<요소>) #리스트의 중간에 요소를 추가
    - extend : 한번에 여러 요소 추가, 원본 리스트가 변형됨

    ```python
    a = [1,2,3]
    a.append(4)
    print(a)
    >>>
    [1, 2, 3, 4]
    
    a.insert(0,19)
    print(a)
    >>>
    [19, 1, 2, 3, 4]
    
    out = a.extend([1,2,3]) #원본 데이터 변형
    print(a)
    print(out)
    >>>
    [1, 2, 3, 1, 2, 3]
    None
    ```

  - 리스트 제거하기

    ```python
    a = [1,2,3]
    out = a.extend([1,2,3]) # a의 리스트 내부값을 변경
    print(a)
    del a[1] #a리스트의 인덱스1번의 값 제거됨
    print(a)
    >>>
    [1, 2, 3, 1, 2, 3]
    [1, 3, 1, 2, 3] 
    
    a.pop() #마지막 요소 제거
    print(a)
    >>>
    [1, 3, 1, 2] 
    ```

    ```python
    a = [1,2,3,4,5,6]
    del a[1:3] #인덱스 1,2 제거 
    print(a)
    >>>
    [1, 4, 5, 6]
    
    a = [1,2,3,4,5,6]
    del a[3:] #인덱스 3이후부터 전체삭제
    print(a)
    >>>
    [1, 2, 3]
    
    a = [1,2,3,4,5,6]
    del a[:3] #인덱스 3이전까지 전체삭제
    print(a)
    >>>
    [4, 5, 6]
    ```

    ```python
    a = [1,2,3,4,5,6]
    a.remove(2) #인덱스가 아닌 데이터로 삭제하기. 값2만 삭제.
    print(a)
    >>>
    [1, 3, 4, 5, 6]
    
    a = [1,2,3,4,5,6]
    a.clear() #리스트 전체 삭제
    print(a)
    >>>
    []
    ```

- 딕셔너리

  - 문자열을 기반으로 값을 저장하는 것

  - 문자열 : 키(key) / 값 (value)

  - {}로 선언하고 쉼표로 연결

    ```python
    a = {"name": "sisyphus", "age":27,"birth":1992,
    "sum":[1,2,3,4,5]}
    print(a["name"]) #key 값으로 value 도출
    >>>
    sisyphus
    
    #dictionary 전체 value 출력하기
    for key in a.keys():
        print(key, a[key]) 
    >>>
    name sisyphus
    age 27
    birth 1992
    sum [1, 2, 3, 4, 5]
    
    #dictionary key값을 넣어 삭제하기
    del a["name"]
    print(a)
    >>>
    {'age': 27, 'birth': 1992, 'sum': [1, 2, 3, 4, 5]}
    
    # del 명령 후 해당 key 잔존여부 확인
    if "name" in a:
        print("name key is live.")
    else:
        print("name key is dead.")
    >>>
    name key is dead. #완전히 제거됨
    ```

    ```python
    # 성적관리 어플리케이션
    
    # 1. 입력 /전체출력/ 검색 기능
    # 사용자로부터 이름/국어/영어/수학 성적입력
    # 3명 사용자 입력
    # dictionary로 관리
    
    # 2. 전체 출력
    # 전체 데이터를 성적순으로 출력
    
    # 3. 검색
    # 사용자 이름 입력해서 조회
    
    
    sungjuk={}
    while True:
        print("## 현재 등록자 수:", len(sungjuk))
        cmd = int(input("1) 성적입력 2) 성적출력 3)성적조회 (1~3) 4)종료 -> "))
    
        #1.성적입력
        if cmd ==1 :
            for cnt in range(3):
                userdata=input("이름,국어,영어,수학 -> ")
                data = userdata.split(',')
                print(data)
        # sungjuk['name']=['100','80','80']
            #sungjuk[data[0]]=[data[1],data[2],data[3]]
                sungjuk[data[0]]=data[1:]
                print(sungjuk)
    
        #2 성적출력
        elif cmd ==2 :
            print("####################################")
            print('이름\t성적')
            for student in sungjuk:
                print(student, '\t', sungjuk[student])
    
        #3 성적조회
        elif cmd ==3 :
            search=input("검색할 학생이름을 입력하세요. -> ")
            print(sungjuk[search])
    
        else:
            print("종료")
            break
    ```

- reversed 반복

  - for i in reverse(range(10)): -> 9875...순으로 반복

- 리스트 내부 최소값과 최대값 찾기 - min(리스트명), max(리스트명)

  ```python
  a=[100,89,130,13]
  min_value=min(a)
  max_value=max(a)
  
  print("최소값", min_value)
  print("최대값", max_value)
  >>>
  최소값 13
  최대값 130
  ```



> 함수



- 기본 용어들

  - 함수 호출

    - 함수를 사용하는 것

  - 매개 변수 (parameter)

    - 함수 호출 시 괄호 내부에 넣는 여러 자료

  - 리턴값

    - 함수 호출하여 최종적으로 나오는 결과


- 함수 기본

  - 생성기본형 : def <함수 이름>():

  - 코드 집합

    ```python
    def print_3times():
    	print("hello")
    	print("hello")
    	print("hello")
    print_3times()
    >>>
    hello
    hello
    hello
    ```

    ```python
    def print_3times(count,a):
        for i in range(count):
            print(a)
    print_3times(3,'faf')
    >>>
    faf
    faf
    faf
    ```

- 가변 매개 변수 함수

  - 매개변수를 원하는 만큼 받을 수 있는 함수
  - 가변매개변수 뒤에는 일반 매개변수 올 수 없음
  - 가변매개변수는 하나만 사용할 수 있음

  ```python
  def print_n_times(n, *values):
      for i in range(n):
          print(len(values))
          for value in values:
              print(value, end='')
          print()
      
  print_n_times(3, "a","b","c")
  >>>
  3
  abc
  3
  abc
  3
  abc
  ```

  ```python
  def test (a, b=10, c=100):
      print(a+b+c)
  
  test(10,20,30) #60
  test(a=10,b=50,c=60) #120
  test(c=100,a=20,b=30) #150
  test(100,c=200) #a에 100이 들어간다. -> 310
  ```

  ```python
  # factorial 함수
  def factorial(n):
      sum=1
      for i in range (1,n+1): # i값은 1~n
          sum=sum*i
      return sum
          
          
  
  print(factorial(5))
  >>>
  120
  ```


- 재귀함수

  - 자기 자신이 자기를 호출한다.

    ```python
    # factorial 개념 
    # -> n!=n*(n-1)*(n-2)...*1
    ```

    ```python
    # factorial(n)=n*factorial(n-1)(n>=2일때)
    # factorial(1)=1
    ```

    ```python
    # factorial(4)=4*f(3)
    			# =4*3*f(2)
    			# =4*3*2*f(1)
    			# =4*3*2*1
    ```

    ```python
    def factorial(n):
        if n == 1:
            return 1
        elif n>1:
            return n * factorial(n-1)
    print(factorial(1))
    print(factorial(3))
    print(factorial(5))
    >>>
    1
    6
    120
    ```

  - 메모화 (memorize)

    - 재귀 함수 사용으로 인해 발생하는 문제 해결

    - 상황에 따라 같은 것을 과도하게 반복하는 문제 

      - ex) 피보나치수열 1,1,2,3,5,8,13,21..

      ```python
      def fi(n):
          if n == 1 or n == 2:
              return 1
          elif n>=1:
              return fi(n-2) + fi(n-1)
      print(fi(8))
      >>>
      21
      #덧셈의 과도한 반복문제 발생
      ```

      ```python
      dic = {
          1:1,
          2:1
      }
      count = 0
      def fi(n):
          if n in dic:
              return dic[n]
          else:
              global count #함수밖의 count 변수를 가져온다
              count += 1
              output = fi(n-2) + fi(n-1)
              dic[n]=output # 결과값을 dic 안에 넣는다.
              return output
          
      #딕셔너리를 사용하여 메모리 기능을 통해 과도한 계산 생략
      ```

  - 인수

    - 호출원에서 함수로 전달되는 작업거리
    - 함수의 동작에 변화 주어 활용성 높임

  - 리턴값

    - 함수의 실행 결과를 호출원으로 돌려주는 값
    - 리턴값 반환 시 return명령 뒤에 반환할 값을 지정
    - 리턴값이 무조건 있어야 하는 것은 아님

  - 가변인수

    - 고정되지 않은 임의 개수의 인수를 받음

    - *기호를 인수 이름 앞에 붙임

    - 반드시 맨 뒤에 와야 작동한다

      ```python
      def intsum(s, *ints) #무조건 이런 형태로 , 가변인수는 뒤에 위치해야 한다.
      ```


  - 지역변수

    - 함수 내부에서 선언하는 변수
    - 함수 내부에서만 사용되고 밖으로는 적용 안됨

  - 전역변수

    - 함수 바깥에서 선언하는 변수
    - 어디에서나 참조가능

  - docstring

    - 도움말로 사용가능.

    ```python
    def fi(n):
        """이 함수는 피보나치 수열을 구하기 위한 함수입니다."""
        if n in dic:
            return dic[n]
        else:
            global count #함수밖의 count 변수를 가져온다
            count += 1
            output = fi(n-2) + fi(n-1)
            dic[n]=output # 결과값을 dic 안에 넣는다.
            return output
    
    help(fi)
    >>>
    fi(n)
        이 함수는 피보나치 수열을 구하기 위한 함수입니다.
    ```
