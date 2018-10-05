```python
###### ###### 과제 ###### ######

#단어 검출 개수 출력 => 공백으로 데이터 parsing
#모든 특수문자 제외
#순수한 알파벳 데이터만 추출
#많이 사용된 단어순으로 sort (MAX->MIN)
#처리속도가 채점 기준

import sys
import re
import time
import operator

start=time.time() # 시작 시간

file=open('2.txt')
text=file.read()

parse = re.sub('[-=,.#/!?:;$''""()\'\n1234567890]','',text) #순수 알파벳 데이터 추출
parse=parse.lower()
words=parse.split(' ')  #공백 한 칸 기준으로 요소 생성 및 리스트 출력

#리스트를 딕셔너리 형태로 다시 담기
wordscount={}

for a in words:
    try: wordscount[a] +=1
    except: wordscount[a]=1

#많이 사용된 단어순으로 sort
sortwordscount=sorted(wordscount.items(), key=operator.itemgetter(1), reverse=True)
print(sortwordscount)

end=time.time() # 끝 시간
print("Elapsed time:", str((end-start))) #총 소요시간 출력
```

