- Fork
  - 다른 사람이 공개한 리모트 리포지토리를 자신의 계정으로 복사
- Clone
  - 클라우드에서 로컬로 다운받는 것 
- Branch
  - 독립적으로 어떤 작업을 진행하기 위한 개념. 필요에 의해 만들어지는 각각의 브랜치는 다른 브랜치의 영향을 받지 않기 때문에, 여러 작업을 동시에 진행 가능. Pointer 개념.
  - 체크아웃 - branch의 이동. 지금 자신이 있는 branch는 * 마크가 붙어있음.

> 반복자

- 열거 가능 객체

  - for 반복문

    - 객체 요소를 순서대로 읽는 제어문

    - 컨테이너 순회

      - iter 메소드 호출하여 반복자 구하고,

      - 이것이 next 메소드 호출하여 컨테이너 요소 읽으며 이동

        ```python
        nums=[11,22,33]
        for n in nums:
            print(n)
        print('-'*20)
        
        it = iter(nums) # index -> next()
        print(next(it))
        print(next(it))
        print(next(it))
        
        >>>
        
        11
        22
        33
        --------------------
        11
        22
        33
        ```

        ```python
        while True:
            try:
                num=next(it)
            except StopIteration:
                break
                
            print(num)
            
        >>>
        11
        22
        33
        ```

- 일급시민 - 함수 자체를 파라미터로 전달

  ```python
  def add(a,b):
      print(a+b)
  
  plus = add 
  plus(10,20)
  >>>
  30
  ```

  ```python
  def calc(op,a,b):
      op(a,b)
  
  def add(a,b):
      print(a+b)
  
  def subtract(a,b):
      print(a-b)
  
  calc(add, 10,20)
  
  >>>
  30
  ```

- 로컬함수 - 함수 내의 함수, 함수의 종속성을 제거할 수 있다

  ```python
  def calcsum(n):
      def add(a, b):
          return a + b
      sum=0
      for i in range(n+1):
          sum = add(sum, i)
      return sum
  
  print("1~10=",calcsum(10))
  >>>
  1~10= 55
  ```

- 함수 데코레이터 - 함수에 원하는 코드 추가하는 기법

  - 함수 래핑 - 원하는 코드 추가 및 원래 함수 대리호출하여 기능 확장

    ```python
    def inner():
        print('결과입니다.')
    def outer(func):
        print('-' * 15)
        func()
        print('-' * 15)
    
    outer(inner)
    >>>
    ---------------
    결과입니다.
    ---------------
    ```

    ```python
    def inner():
        print('결과입니다.')
    
    def outer(func):
        def wrapper():
            print('-' * 15)
            func()
            print('-' * 15)
    
        return wrapper
    
    my_inner = outer(inner)
    my_inner()
    >>>
    ---------------
    결과입니다.
    ---------------
    ```

- 클래스 데코레이터

  - 객체를 괄호 붙여 호출할 경우 call 특수 메소드가 자동 호출

- eval - 실행 가능한 문자열(1+2, 'hi' + 'a' 같은 것)을 입력으로 받아 문자열을 실행한 결과값을 리턴하는 함수이다.

  ```python
  result = eval("2+3*5")
  print(result)
  
  a=2
  print(eval("a*3"))
  
  city = eval("['seoul','new york','paris']")
  for c in city:
      print(c,end=',')
     
  >>>
  
  17
  6
  seoul,new york,paris,
  ```

- repr - 객체로부터 문자열 표현식을 생성

  - 해석기를 위한 표현식이라는 점에서 str 함수와 차이

  - 이 표현식으로 다시 객체 만들 수 있어야

  - 따옴표까지 문자열에 함께 담아야

- exec

  - 파이썬 코드를 직접 실행하는 함수
  - eval 함수는 표현식 평가하나 문장을 실행하는 것은 아님



