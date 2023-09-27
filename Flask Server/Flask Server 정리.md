## [[Flask 예시]]

### request 모듈의 args 변수
👉 "?var1=val1&var2=val2"같은 URL parameter를 parsing한 결과를 사전으로 가지고 있음

### get() 메소드 활용
👉 위의 사전에서 해당하는 파라미터를 찾아옴
get({URL 파라메터의 변수이름}, {기본값})
```
name = request.args.get("name", "Guest")
workplace = request.args.get("workplace", "None")
```
-> 

// f-string (python 기능)
변수1, 변수2가 있을 때, 
변수들을 출력하기 함해 %-formatting 방식을 쓰거나
str.format() 메소드 방식을 사용하는데 가독성 문제가 발생함
-> f-string 방식은 f'{string}' 형태로 사용됨 (내용이 복잡 할수록 가독성이 좋아짐짐