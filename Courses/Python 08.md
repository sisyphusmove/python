# Python 08

> ##### DB와 파이썬 연동 구조



1. 모듈 로딩 (import)
2. DB 연결 (connect) - host, user, password
3. Cursor SQL 명령어 처리 (cursor)
4. 명령어 실행 (execute)
5. SELECT query 일 경우
   - fetchall()
   - fetchone()
   - fetchmany()
6. 리소스 닫기 (close)



> ##### 클래스



- 클래스
  - 객체 지향의 가장 기본적 개념
  - 관련된 <u>속성</u>과 <u>동작</u>을 하나의 범주로 묶어 실세계의 사물을 흉내냄
    - 속성 -  객체의 특성(data) / 동작 - 객체의 기능(function, method)

- 인스턴스
  - 클래스를 기반으로 만들어진 객체

- 모델링

  - 사물 분석하여 필요한 속성과 동작 추출

- 캡슐화

  - 모델링 결과를 클래스로 포장

- 생성자
  - 클래스 선언 형식
  - __init__ 생성자
    - 통상 객체 초기화
- 클레스의 정의 - self
  - 파이썬의 메소드에 사용되는 self 가 가리키는 '자신'

```python
class Student:
    def __init__(self,name,kor,math,eng,sci):
        self.name=name
        self.kor=kor
        self.math=math
        self.eng=eng
        self.sci=sci

    def get_sum(self): #총점 생성 메소드
        return self.kor+self.math+self.eng+self.sci

    def get_avg(self):# 평균 생성 메소드
        return self.get_sum()/4

    def to_string(self):
        return '{0}\t{1}\t{2}'.format(self.name,self.get_sum(),self.get_avg())

    def study(self):
        print('공부를 합니다')


class Teacher:
    # def __init__(self):
    #     pass
    def teach(self):
        print('학생을 가르칩니다')
```

```python
#리스트 형태 객체 생성

stlist=[
    Student('hong',90,90,20,10),
    Student('kim',100,49,10,15),
    Student('lee',80,70,56,15),
    Student('cho',59,15,16,17)
]

print(stlist[0].name)
>>>
hong
```

- 정적 메소드

  - 특정 종속관계없이 그냥 사용가능한 메소드

    ```python
    @staticmethod
    def company_name():
        print('Samsung Multicampus and HP')
            
    if __name__ == '__main__':
        Car.company_name()
    >>>
    Samsung Multicampus and HP
    ```

- instance 멤버 (필드, 메소드)

  - 인스턴스 필요
  - 개별 메모리 사용

- static 멤버

  - 인스턴스 불필요
  - 클래스 이름으로 사용
  - 공용 멤버
  - 메소드에 매개변수 없이 선언
  - @staticmethod

- class 멤버

  - 인스턴스 불필요

  - 클래스 이름으로 사용

  - 공용 멤버

  - 메소드에 매개 변수 전달 가능

    - 첫번 째 매개변수 클래스 객체

  - @classmethod

    ```python
    class InstanceCounter:
        count=0
        def __init__(self):
            InstanceCounter.count += 1
    
        @classmethod
        def print_instance_count(cls):
            print(cls.count)
    ```


- 상속

  - 한 클래스가 다른 클래스로부터 데이터 속성과 메소드를 물려받는 것.

    ```python
    #부모 클래스
    class Person():
        def go2school(self):
            print('학교를 갑니다.')
        def holiday(self):
            print('휴일에는 학교에 가지 않는다')
        def lunch(self):
            print('점심을 먹었다.(12:00-13:00)')
        def go2home(self):
            print('집에 돌아갑니다.')
    
    #자식 클래스1
    class Student(Person):
        def study(self):
            print('공부를 합니다.')
    
    
    #자식 클래스2
    class Teacher(Person):
    
        def teach(self):
            print('학생을 가르친다')
    
    
    s1=Student()
    t1=Teacher()
    
    s1.go2home()
    t1.go2school()
    >>>
    집에 돌아갑니다.
    학교를 갑니다.
    ```

- 액세서

  - 일정한 규칙 마련하여 안전한 액세스 보장
    - 게터 메서드 - 멤버값 대신 읽음
    - 세터 메서드 - 멤버값 변경

- 예제

  - 온라인 쇼핑에 사용되는 회원의 종류를 모델링하기
    - 회원종류: 프리미엄, 일반

    - 회원의 공통 정보
      - 로그인: 모든 회원은 로그인을 한 뒤에 서비스를 사용할 수 있다.
      - 로그아웃: 모든 회원은 로그아웃을 할 수 있다.
      - 상품검색: 전체 상품 검색을 할 수 있다.
      - 장바구니: 장바구니에 상품을 추가할 수 있다.
      - 상품 구매 1): 장바구니의 상품을 구매할 수 있다.
      - 상품 구매 2): 모든 상품은 장바구니를 거치지 않고 직접 구매할 수 있다.
      - 구매 목록: 구매 목록을 확인할 수 있다.
      - 포인트: 모든 구매 상품은 5%의 적립 포인트를 얻을 수 있다.

    - 프리미엄 회원 정보
      - 상품 검색: 프리미엄 회원이 전용 할인 상품을 검색할 수 있다.
      - 포인트:  프리미엄 회원은 총 구매 금액에 대해서 다음과 같이 적용된다.
        - 총 누적금액: 100만원 초과시 10%
        - 총 누적금액: 500만원 초과시 15%
        - 총 누적금액:1000만원 초과시 20%

    - 상품 DB

      | IDX  | ITEM_NAME | ITEM_DETAIL | ITEM_PRICE | ITEM_QTY | ITEM_CATEGORY | ITEM_IMAGE   |
      | ---- | --------- | ----------- | ---------- | -------- | ------------- | ------------ |
      | 1    | 키보드    | 좋은 키보드 | 10000      | 500      | PC            | keyboard.kpg |
      | 2    | 마우스    | 편한 마우스 | 12000      | 1000     | PC            |              |
      |      |           |             |            |          |               |              |

      - item image DB

      | IDX  | ITEM_IDX | FILENAME      | FILESIZE |
      | ---- | -------- | ------------- | -------- |
      | 1    | 1        | keyboard1.png | 128      |
      | 2    | 1        | keyboard2.png | 125      |
