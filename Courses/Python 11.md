# Python 11

> 정규표현식



- 텍스트에 포함된 특정 문자열을 검색하는 것

  ```python
  # 비정규표현식
  
  data = "123456-1234567"
  converted_data=''
  
  if len(data) == 14 and data[:6].isdigit() and data[7:].isdigit() and data[6:7] == '-':
      converted_data=data[:6]+"-"+"*******"
  print(converted_data)
  >>>
  123456-*******
  ```

  ```python
  # 정규표현식
  
  import re
  data = """
  123456-1234567
  700000-8000000
  123445-1414414
  """
  pattern=re.compile("(\d{6})[-](\d{7})")
  print(pattern.sub("\g<1>-*******",data))
  >>>
  123456-*******
  700000-*******
  123445-*******
  ```



- re 모듈



  - 파이썬에서 정규표현식 지원
  - compile을 사용하면 패턴 객체(p)를 재사용 가능 -> 시간 단축
  - re.compile() - 정규식 패턴을 파이썬이 사용할 수 있는 정규식 객체로 컴파일
  - match(), search()와 같은 메소드를 통해 사용됨
  - 검색,반환,위치,변경,분리 관련 된 작업을 지원



- 메타 문자



  - 원래 그 문자가 가진 뜻이 아닌 특별한 용도로 사용되는 문자

  -  특수문자

    . 

     개행문자(\n)를 제외한 문자 1개를 나타냄. re.DOTALL이 설정돼있으면 개행도 포함

    ^

     문자열의 시작. re.MULTILINE이 설정돼있으면 매 라인마다 매치됨

    $

     문자열의 종료.  re.MULTILINE이 설정돼있으면 매 라인마다 매치됨

    [] 

     문자열의 집합을 나타냄. 가령 [abcd]면 a b c d 중에 한 문자와 매치되고 [a-d]로 쓸 수도 있다. [^a]는 a를 제외한 모든 문자이다

    | 

     a|b. a 또는 b

    () 

     괄호 안의 정규식을 그룹으로 만듦. 괄호 자체를 매칭시킬려면 '\(', '\)'나 '[(]', '[)]'로 나타내면 됨

    *

     문자가 0번 이상 반복

    \+ 

     문자가 1번 이상 반복

    ?

     문자가 0번 혹은 1번 반복 , 콤마로 나뉘어짐

    {m} 

     문자가 m번 반복 

    {m,n} 

     문자가 m회부터 n회까지 반복되는 모든 경우의 수 

    {m,} 

     문자가 m회부터 무한 반복되는 모든 경우의 수 

    ex) 010-4856-9123을 정규표현식으로

    ```python
     (\d{3})[-](\d{3,4})[-](\d{4})
    ```

    - [] 안에 올수 있는 메타문자

    \w 

     유니코드인 경우 숫자, 밑줄을 포함하는 모든 언어의 표현 가능한 문자. 아스키코드인 경우 '[a-zA-Z0-9_]'와 동일

    \W 

     유니코드인 경우 숫자, 밑줄과 표현 가능한 문자를 제외한 나머지 문자. 아스키코드인 경우 '[^a-zA-Z0-9_]'와 동일

    ```PYTHON
    import re
    p = re.compile('a')
    source = "Dowon Lee 010-222-3333 dewon@hgmail.com"
    
    result1 = re.findall('\w',source)
    result2 = re.findall('\w+',source)
    result3 = re.findall('\W+',source)
    
    print('result1=',result1)
    print('result2=',result2)
    print('result3=',result3)
    
    >>>
    
    result1= ['D', 'o', 'w', 'o', 'n', 'L', 'e', 'e', '0', '1', '0', '2', '2', '2', '3', '3', '3', '3', 'd', 'e', 'w', 'o', 'n', 'h', 'g', 'm', 'a', 'i', 'l', 'c', 'o', 'm']
    result2= ['Dowon', 'Lee', '010', '222', '3333', 'dewon', 'hgmail', 'com']
    result3= [' ', ' ', '-', '-', ' ', '@', '.']
    ```

    \d 

     유니코드인 경우 [0-9]를 포함하는 모든 숫자. 아스키 코드인 경우 [0-9]와 동일

    \D 

     유니코드인 경우 숫자를 제외한 모든 문자. 아스키코드인 경우 [^0-9]와 동일

    \s 

     유니코드인 경우 [ \t\n\r\f\v]를 포함하는 공백 문자. 아스키 코드인 경우에도 동일.

    \S 

     유니코드인 경우 공백 문자를 제외한 모든 문자. 아스키코드인 경우 [^ \t\n\r\f\v]와 동일

    \b 

     단어의 시작과 끝의 빈 공백

    \B 

     단어의 시작과 끝이 아닌 빈 공백 

    \\ 

     역슬래시 문자 자체 

    \[숫자] 

     지정도니 숫자만큼 일치하는 문자열을 의미 

    \A 

     문자열의 시작

    \Z

     문자열의 끝 


- match 객체의 메소드

  - match : 문자열의 처음부터 정규식과 매치되는 지 조사

  - search: 문자열 전체를 검색하여 정규식과 매치되는지 조사

  - findall: 정규식과 매치되는 모든 문자열(substring)을 리스트로 리턴

  - split: 패턴으로 나누기

  - sub: 패턴 대체하기

    ```python
    import re
    source = "Patterns are very important for validating check."
    
    pattern1 = re.compile('are')
    
    match = pattern1.match(source)
    search = pattern1.search(source)
    
    if match: #첫 단어가 very로 시작하는지 아닌지만 검색
        print("match:",match.group())
    
    if search: # 첫단어뿐 아니라 다른 단어도 계속 검색
        print('search:',search.group())
    >>>
    search: are
    ```

    ```python
    import re
    source = "Patterns are very important for validating check."
    
    pattern = re.compile('[a-z]+')
    result = pattern.finditer(source)
    
    for el in result:
        if el:
            print(el)
            print(el.start(),el.end())
            
            
    >>>
    
    <_sre.SRE_Match object; span=(1, 8), match='atterns'>
    1 8
    <_sre.SRE_Match object; span=(9, 12), match='are'>
    9 12
    <_sre.SRE_Match object; span=(13, 17), match='very'>
    13 17
    <_sre.SRE_Match object; span=(18, 27), match='important'>
    18 27
    <_sre.SRE_Match object; span=(28, 31), match='for'>
    28 31
    <_sre.SRE_Match object; span=(32, 42), match='validating'>
    32 42
    <_sre.SRE_Match object; span=(43, 48), match='check'>
    43 48
    
    ```

    ```python
    p=re.compile('[a-z]+')
    m=p.match('python')
    print('m.group()=',m.group())
    print('m.start()=',m.start())
    print('m.end()=',m.end())
    print('m.span()=',m.span())
    >>>
    m.group()= python
    m.start()= 0
    m.end()= 6
    m.span()= (0, 6)
    ```


