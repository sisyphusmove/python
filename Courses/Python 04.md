# Python 04

> ##### 사전 (Dictionary)



- 키와 값의 쌍을 저장하는 대용량 자료구조
- get 함수로 value 가져오기 + 예외 처리 구문 만들기
- get사용 시, 데이터 검색 속도가 원래 방식보다 느려진다



```python
dic = {'boy':'소년','school':'학교', 'book':"책"}

print(dic)
print(dic.get('boy'))
print(type(dic.get('boy')))
>>>
소년
<class 'str'>

print(dic.get('girl'))
print(type(dic.get('girl')))
>>>
None
<class 'NoneType'>

print(dic.get('girl','사전에 존재하지 않는 단어입니다')) #none값 나올 시 출력되는 메세지 지정
print(type(dic.get('girl')))
>>>
사전에 존재하지 않는 단어입니다
<class 'NoneType'>

```

- 사전관리

  - 실행 중 삽입, 삭제, 수정 등 편집 가능

  - del : 해당 키를 찾아 값과 함께 삭제

  - items: 자료형을 튜플로 전환

    ```python
    dic = {'boy':['소년1','소년2'],
           'school':['학교','공부하는 곳'],
           'book':['책','정보를 얻을 수 있는 것']}
           
    for i in dic.items():
        print(i)
        print(i[0],i[1][0], i[1][1])
    
    print(type(i))
    >>>
    ('boy', ['소년1', '소년2'])
    boy 소년1 소년2
    ('school', ['학교', '공부하는 곳'])
    school 학교 공부하는 곳
    ('book', ['책', '정보를 얻을 수 있는 것'])
    book 책 정보를 얻을 수 있는 것
    <class 'tuple'>
    ```

  - update : 기존에 없는 데이터는 추가하고 있는 데이터는 변경

    ```python
    dic = {'boy':['소년1','소년2'],
           'school':['학교','공부하는 곳'],
           'book':['책','정보를 얻을 수 있는 것']}
    
    dic2 = {'student':['학생','공부하는 사람'],
            'teacher':['선생님', '가르치는 사람'],
            'book': ['교과서','공부하기 위한 도구']}
    
    dic.update(dic2) #기존에 없는 데이터는 추가하고 있는 데이터는 변경
    print(dic)
    print(len(dic))
    
    >>>
    {'boy': ['소년1', '소년2'], 'school': ['학교', '공부하는 곳'], 'book': ['교과서', '공부하기 위한 도구'], 'student': ['학생', '공부하는 사람'], 'teacher': ['선생님', '가르치는 사람']}
    5
    ```

  - dict : 리스트를 딕셔너리 형태로 변환

    - key자리에 있는 값은 정수형이건 문자형이건 상관이 없다. 그러나 단일값이어야 한다. (리스트형x)

    ```python
    myList=[['boy','남자아이'],['school','공부하는 곳'],['book','공부하기 위한 도구']]
    
    dic=dict(myList)
    print(dic)
    
    >>>
    {'boy': '남자아이', 'school': '공부하는 곳', 'book': '공부하기 위한 도구'}
    ```

- 집합 정의

  - 여러 가지 값의 모임 (중복 요소 자동 제거)

  ```python
  asia={'korea','china','japan','korea'}
  print(asia)
  >>>
  {'korea', 'china', 'japan'} #중복값 korea 제거됨
  ```

  - set (): 집합을 만들어주는 명령어.

    ```python
    print(set('bkm'))
    print(set([7,14,1,6]))
    print(set(('python','html','blockchain')))
    print(set({'boy':'소년','girl':'소녀'}))
    print(set())
    
    >>>
    {'b', 'm', 'k'} #일반 문자열은 한 글자씩 쪼개진다
    {1, 6, 14, 7}
    {'python', 'blockchain', 'html'} #순서가 없이 랜덤으로 출력됨
    {'boy', 'girl'} #key값만 저장
    set()
    ```

    ```python
    asia={'korea','china','japan','korea'}
    asia.add('usa')
    asia.add('china') #중복요소는 추가되지 않는다
    asia.remove('japan') #set요소 제거
    print(asia)
    
    >>>
    {'korea', 'china', 'usa'}
    
    asia.update({'sigapore','hongkong','korea'})
    >>>
    {'china', 'korea', 'usa', 'sigapore', 'hongkong'}
    
    twox={2,4,6,8,10,12}
    threex={3,6,9,12,15}
    
    print("교집합", twox & threex)
    print("합집합", twox | threex)
    print("차집합", twox - threex)
    >>>
    교집합 {12, 6}
    합집합 {2, 3, 4, 6, 8, 9, 10, 12, 15}
    차집합 {8, 2, 10, 4}
    ```


> ##### 컬렉션 관리 함수

- enumerate

  - 순서값과 요소값을 한꺼번에 구하는 내장함수

  ```python
  score=[88,95,70,100,99]
  
  for no, s in enumerate(score,1):
      print(str(no)+"번 학생 점수:", s)
  >>>
  1번 학생 점수: 88
  2번 학생 점수: 95
  3번 학생 점수: 70
  4번 학생 점수: 100
  5번 학생 점수: 99
  
  ```

- zip

  - 여러 개 컬렉션 합쳐 하나로 만듦sssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssss
  - 두 리스트의 대응되는 요소끼리 짝지어 튜플 리스트 형성

  ```python
  days = ['월','화','수','목','금','토','일']
  food = ['갈비탕','설농탕','순대국','칼국수']
  menu = zip(days, food)
  
  for f in menu:
      print(f)
  >>>
  ('월', '갈비탕')
  ('화', '설농탕')
  ('수', '순대국')
  ('목', '칼국수')
  
  for d, f in menu:
      print(d, '메뉴:', f)
  >>>
  월 메뉴: 갈비탕
  화 메뉴: 설농탕
  수 메뉴: 순대국
  목 메뉴: 칼국수
  
  ```

- filter

  - 리스트 요소 중 조건에 맞는 것만을 골라냄
  - 첫번째 인수: 조건 지정하는 함수
  - 두번째 인수: 대상 리스트

  ```python
  score=[55,34,88,95,70,100,99]
  
  def underD(s):
      return s < 60
  
  for s in filter(underD, score):
      print(s)
  >>>
  55
  34
  
  for s in filter(lambda a:a<60, score): #lambda식으로도 가능
      print(s) 
  >>>
  55
  34
  ```

- map

  - 개별적인 요소에 추가적인 연산이 필요할 때 사용.

    ```python
    def multipy(a):
        return a * 2
    
    for s in map(multipy, score):
        print(s)
    >>>
    110
    68
    176
    190
    140
    200
    198
    
    score=[55,34,88,95,70,100,99]
    bonus=[5,4,1,3,5,8,9]
    
    
    def total(s, b):
        return s+b
    
    for s in map(total, score, bonus):
        print(s)
    >>>
    60
    38
    89
    98
    75
    108
    108
        
     
    ```

- copy 함수

  - 컬렉션의 사본을 만든다.

  - deepcopy 기능을 써야 독립적 사본을 만들 수 있다.

    ```python
    list1=[1,2,3]
    list2=list1.copy()
    
    list2[1]=100
    print(list1)
    print(list2)
    >>>
    [1, 2, 3]
    [1, 100, 3]
    ```

    ```python
    list0=['a','b']
    list1=[list0,1,2]
    list2=list1.copy()
    
    print(list2)
    
    for d in list2:
        print(d)
    >>>
    [['a', 'b'], 1, 2]
    ['a', 'b']
    1
    2
    
    ```

    ```python
    import copy
    
    list0=['a','b']
    list1=[list0,1,2]
    list2=copy.deepcopy(list1)
    list2[0][1]="c"
    
    print(list1)
    print(list2)
    
    >>>
    [['a', 'b'], 1, 2]
    [['a', 'c'], 1, 2]
    
    ```


> ##### 예외 처리



- 오류

  - 구문오류

    - 프로그램 실행 전 발생하는 오류 (SyntaxError)

  - 런타임 오류

    - 프로그램 실행 중 발생하는 오류

- 예외

  - 프로그램 코드는 이상이 없으나 실행 중에 불가피하게 발생하는 문제

- 예외 처리

  - 조건문 활용

  ```python
  index =5 #user input
  list_a = [1,2,3,4,5]
  print(list_a[1])
  
  if index >= len(list_a):
      print('error!')
  else:
      print(list_a[index])
  ```

  - try - except 구문 활용

    - try - 예외 미발생 시 출력 코드

    - except -  예외 발생시 출력 코드, except: pass로 지정할 경우 그대로 예외처리된다.

    - else -  try 출력 시 else 구문 작동

      - 예외 발생 가능성있는 코드만 try 구문에

    - finally - 예외 미발생 , 발생 시 모두 출력

      ```python
      a=input("반지름을 입력하세요. -> ")
      
      try:
          num =  int(a)
          print("반지름", num)
          print("둘레", (3.14*2*num))
          print("원 넓이:", (3.14*num*num))
      
      except:
          print("입력값이 잘못 되었다")
          
      
      ```

      ```python
      myList=['100','90','89','70','test','60','66']
      newList=[]
      
      for item in myList:
          
          # if item.isdigit()== True :
          #     newList.append(item)
          # else:
          #     print(item,'은(는) 숫자가 아닙니다.')
          
          try:
              int(item)
              newList.append(item)
          except:
              print(item,'은(는) 숫자가 아닙니다.')
      
      print(newList)
      >>>
      test 은(는) 숫자가 아닙니다.
      ['100', '90', '89', '70', '60', '66']
      ```

      ```python
      for item in myList:
          try:
              int(item)
              newList.append(item)
          except:
              pass
          finally:
              print("항상 실행")
      print(newList)
      >>>
      항상 실행
      항상 실행
      항상 실행
      항상 실행
      항상 실행
      항상 실행
      항상 실행
      ['100', '90', '89', '70', '60', '66']
      ```

  - 예외 객체 (Exception Object)

    - 예외 정보 저장

    ```python
    while True:
        i = input("반지름")
        try:
            num=int(i)
        except Exception as ex: #exception 객체
            print("type(ex)",type(ex))
            print("exception:",ex)
            print(ex)
            print("error")
            continue
        else:
            print("반지름",num)
        finally:
            print("항상 실행")
    >>>
    반지름sdf
    type(ex) <class 'ValueError'>
    exception: invalid literal for int() with base 10: 'sdf'
    invalid literal for int() with base 10: 'sdf'
    error
    항상 실행
    ```

    - 다중 except as 구문
    - raise - 고의적으로 예외 발생시킴

  ```python
  score=[80,10,141,1515,69]
  
  userData=input("Index를 입력하세요->")
  
  try:
      num=int(userData)
      if num < 0 or num >4: 
          #raise 명령어 사용하여 정상범위도 강제로 IndexError로 간주하기.
          raise IndexError
      print("{}째 점수는: {}".format(num,score[num]))
  
  except ValueError as ex:
      print("TYPE(exception):", type(ex))
      print("Exception message", ex)
      print("############# 정수만 입력해주세요")
  
  except IndexError as ex:
      print("TYPE(exception):", type(ex))
      print("Exception message", ex)
      print("############# 입력가능한 범위는 0~4니다.")
      
  except Exception as ex: # value, index error 제외한 모든 error에 대한 출력 메시지
      print("예기치 못한 에러가 발생했습니다")
  ```

  - assert 조건 , 출력문

    - 조건 불만족시 출력문 실행되고 AssertionError 발생

    ```python
    score = 111
    
    try:
        assert score <= 100, "점수는 100이하여야 합니다"
    
    except AssertionError as ex:
        print(ex)
        
    else:
        print(score)
    >>>
    점수는 100이하여야 합니다
    
    ```


