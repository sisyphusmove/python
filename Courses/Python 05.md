# Python 05

> ##### 들어가기 전



- 함수 설계 시 고려사항



  - 하나의 함수는 한 가지 역할만 해야 한다

  - 서술적인 이름을 사용해야 한다 (길고 서술적인 이론이 짧고 어려운 이름보다 좋다)
  - 이름을 붙일 때 일괄성이 있어야 한다



  - 함수 인수

    - 이상적인 인수 개수는 0개이다
    - 3개는 가능한 피하는 편이 좋다
    - 4개 이상은 특별한 이유가 필요하다
    - 테스트 관점에서 인수가 없는 것이 훨씬 용이하다


- 변수

  - 변수는 내버려두면 계속 늘어난다
  - 변수를 덜 사용하고 최대한 '가볍게'만들어 가독성을 높인다


- 주석
  - 나쁜 코드에 주석을 달지 말고 새로 짜라
  - 잡음을 줄이고 의도를 명확하게
  - 가능하면 코드로 의도를 표현하라



> ##### Git



- 버전관리 시스템



- 팀 개발을 위한 전용 툴은 아니다
- 개인 이용 목적으로도 Git을 사용하는 것을 추천
- 타임머신과 같은 것
  - 원하는 과거로 들어갈 수 있다
  - 어디가 변경되었는지, 변경 점도 쉽게 알 수 있음
  - 보다 효과적인 개발 가능
- 여러 명이 수정한 내용을 정리하고 합체할 수 있다

- 변경 내용을 작은 단위로 기록할 수 있기 때문에, 누가 무엇 떄문에 수정을 했는지 이력을 보면 알 수 있다



- github.com & bitbucket.org

  - git 에서 관리하고 있는 파일의 백업장소로 사용할 수 있는 장소
  - 커뮤니케이션의 장소로 사용 가능

- SourceTree란?

  - gui 환경의 git vsc



> ##### 모듈과 패키지



- import 명령

  - 외부의 모듈을 가져와 사용
    - 필요 기능에 따라 선택
  - 파이썬에는 자주 사용하는 기능이 표준 모듈로 함께 설치되어 있음
    - 표준 라이브러리
  - from 모듈 import 함수명
    - ex) from math import sqrt
    - 이 경우 sqrt 외 math 에 속한 다른 함수는 사용 불가

- math 모듈

  - 정교한 계산 기능 제공

- time 모듈

  - 날짜와 시간 관련 기능 제공

    ```python
    t = time.time()
    print(t)
    print(time.ctime(t))
    print(time.localtime(t))
    now = time.localtime(t)
    print(now)
    print(type(now))
    print("%d년 %d월 %d일" % (now.tm_year, now.tm_mon, now.tm_mday))
    print("{0}:{1}:{2}".format(now.tm_hour, now.tm_min, now.tm_sec))
    >>>
    1537497402.0409462
    Fri Sep 21 11:36:42 2018
    time.struct_time(tm_year=2018, tm_mon=9, tm_mday=21, tm_hour=11, tm_min=36, tm_sec=42, tm_wday=4, tm_yday=264, tm_isdst=0)
    time.struct_time(tm_year=2018, tm_mon=9, tm_mday=21, tm_hour=11, tm_min=36, tm_sec=42, tm_wday=4, tm_yday=264, tm_isdst=0)
    <class 'time.struct_time'>
    2018년 9월 21일
    11:36:42
    ```


- 모듈

  - 두 개의 소스 파일로 만드는 하나의 프로그램 의미
  - 독자적인 기능을 갖는 구성 요소
  - 파이썬에서는 개별 소스 파일을 일컫는다
  - 표준 모듈
    - 파이썬과 함께 따라오는 모듈
  - 사용자 생성 모듈
    - 프로그래머가 직접 작성한 모듈
  - 서드 파티 모듈
    - 파이썬 재단도, 프로그래머도 아닌 다른 프로그래머, 또는 업체에서 제공하는 모듈

- 난수

  - import random

  - random.choice() : 리스트에서 랜덤으로 요소 출력 , 리스트로 범위를 랜덤범위를 한정할 때 사용.

    ```python
    import random
    
    lang = ['python','java','c','javaScript','golang']
    
    print(lang)
    for i in range(5):
        print(random.choice(lang))
    >>>
    c
    c
    golang
    javaScript
    java
    ```

  - random.shuffle(): 리스트 요소들을 섞는다.

    ```python
    lang = ['python','java','c','javaScript','golang']
    
    random.shuffle(lang)
    >>>
    ['python', 'javaScript', 'golang', 'java', 'c']
    ```

  - random.sample(리스트명,뽑을 요소의 수)

    ```python
    lang = ['python','java','c','javaScript','golang']
    
    print(random.sample(lang,2))
    >>>
    ['golang', 'python']
    ```

- sys 모듈

  - 파이썬 해석기가 실행되는 환경과 해석기의 여러 기능 조회 및 관리

  - 명령행 인수

    - 파이썬에서 실행 파일 뒤에 인수를 전달할 수 있음


> ##### 파일 입출력 / 파일 관리 / 데이터베이스



- 파일쓰기
  - 파일
    - 정보를 저장하는 기본단위
    - 문서 이미지 멀티미디어 자료 등 모두 보관
  - 파일 입출력
    - 오픈
    - -open (파일경로, 모드)
    - 모드
    - -파일로 무엇을 할 것인지 지정 (r,w,a,x)
- open  함수
  - 파일 입출력 준비 및 파일 객체 반환
  - 출력할 데이터 인수로 전달하여 write 메소드 호출
  - 파일 사용 후 close 메소드로 닫기
- readline 함수
  - 한 줄씩 읽기
  - 파일 마지막에 빈 문자열 반환







