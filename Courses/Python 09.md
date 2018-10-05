# Python 09

> 정적 메소드

- 클래스에 포함되는 단순 유틸리티 메소드
- 특정 객체에 소속되거나 클래스 관련 동작하지 않음
- @staticmethod



> 연산자 오버로딩



- 연산자 오버로딩 : 연산자와 특수 메소드(이미 파이썬에서 정의해놓은 메소드)

| **연산자/함수(Operator/Function)** | **메소드(Method)**        | **설명(Description)** |
| ---------------------------------- | ------------------------- | --------------------- |
| +                                  | __add__(self, other)      | 덧셈                  |
| *                                  | __mul__(self, other)      | 곱셈                  |
| -                                  | __sub__(self, other)      | 뺄셈                  |
| /                                  | __truediv__(self, other)  | 나눗셈                |
| %                                  | __mod__(self, other)      | 나머지                |
| <                                  | __lt__(self, other)       | 작다(미만)            |
| <=                                 | __le__(self, other)       | 작거나 같다(이하)     |
| ==                                 | __eq__(self, other)       | 같다                  |
| !=                                 | __ne__(self, other)       | 같지 않다             |
| >                                  | __gt__(self, other)       | 크다(초과)            |
| >=                                 | __ge__(self, other)       | 크거나 같다(이상)     |
| [index]                            | __getitem__(self, index)  | 인덱스 연산자         |
| in                                 | __contains__(self, value) | 멤버 확인             |
| len                                | __len__(self)             | 요소 길이             |
| str                                | __str__(self)             | 문자열 표현           |

- 특수 메소드

  - 특정한 구문에 객체 사용될 경우 미리 약속된 작업 수행

    | [index] | __getitem__(self, index)  | 인덱스 연산자 |
    | ------- | ------------------------- | ------------- |
    | in      | __contains__(self, value) | 멤버 확인     |
    | len     | __len__(self)             | 요소 길이     |
    | str     | __str__(self)             | 문자열 표현   |

- Decimal

  - 정수 혹은 문자열 실수로 초기화
  - 오차 없이 정확하게 10진 실수를 표현
    - 컴퓨터에서는 이진 실수로 십진 실수를 정확하게 표현하기가 어려움

- Fraction

  - 유리수를 표현

    - 분모와 분자를 따로 전달하여 분수형태 숫자 표현

      ```python
      from fractions import *
      
      a= Fraction(1,3)
      b= Fraction(8,10)
      print(a)
      print(b)
      >>>
      1/3
      4/5
      ```

- array 모듈

  - 동일 타입 집합인 배열을 지원
  - 대량 자료를 메모리 낭비 없이 저장 및 고속 액세스 가능

- 외부 모듈의 목록

  - 서드파티 모듈

    - 파이썬 외 회사 단체가 제작하여 배포하는 모듈

      ```python
      from bs4 import BeautifulSoup
      from urllib import request
      
      # BS4로 외부 링크 사용해보기
      # request.openurl() 기상청 날씨정보 취득
      target = request.urlopen("http://www.weather.go.kr/weather/forecast/mid-term-rss3.jsp?stnld=108")
      
      # BeautifulSoup 클래스는 웹페이지 분석을 위한 클래스
      
      soup = BeautifulSoup(target, 'html.parser')
      
      for location in soup.select('location'): #select, select_one 원하는 값 추출
          if location.select_one('city').string == '서울':
              print('도시:',location.select_one('city').string)
              print('\t날씨:',location.select_one('wf').string)
              print('\t최저기온:', location.select_one('tmn').string)
              print('\t최고기온:', location.select_one('tmx').string)
              print()
      >>>
      도시: 서울
      	날씨: 구름조금
      	최저기온: 15
      	최고기온: 24
      ```
