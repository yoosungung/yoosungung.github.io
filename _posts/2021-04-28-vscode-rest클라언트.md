---
layout: posts
title: VS Code RestClient 사용법
categories: [tool]
tags: [vscode, rest]
---

1. VSCode의 Rest Client 확장을 설치합니다.  

2. 확장자가 http인 파일을 생성합니다.

3. 파일을 편집합니다.   
 - 각 request는 '###'로 시작 합니다.
 - GET POST PUT DELETE로 시작하고 경로(url)을 입력 합니다.
 - 아래 header정보를 입력 합니다.
 - body는 한줄 띄고 여러줄로 입력합니다.
 - 변수 선언은 @이름 = 값을 입력 합니다.
   변수 사용은 {{ 변수 }}로 사용 합니다.

4. 예시
 - url을 변수로 처리
 
```
###
//@hostURL = http://172.21.237.115:3000/
@hostURL = http://localhost:3000
```

 - 권한 토근 저장
 
```
###
# @name signin
POST {{hostURL}}/sign/in
content-type: application/json

{
  "id": "user",
  "password": "password"
}

###
@authToken = {{signin.response.headers.x-access-token}}
```

 - 권한 토큰을 이용한 rest 호출
 
```
###
GET {{hostURL}}/api/summary/master/opportunity?visible=owner
content-type: application/json
x-access-token: {{authToken}}

###
GET {{hostURL}}/state/machines
content-type: application/json
x-access-token: {{authToken}}

###
# @name createmachine
POST {{hostURL}}/state/machines/test
content-type: application/json
x-access-token: {{authToken}}

{
  "id": "body",
  "initial": "pending",
  "states": {
    "pending": {},
    "resolved": {},
    "rejected": {}
  }
}
```

 - response body 값을 이용한 rest 호출
 
```
###
@txmachineId = {{createmachine.response.body.$.insertId}}

###
GET {{hostURL}}/state/machines/{{xmachineId}}
content-type: application/json
x-access-token: {{authToken}}

###
# @name start
POST {{hostURL}}/state/machines/start/{{xmachineId}}
content-type: application/json
x-access-token: {{authToken}}

{}

###
@xstate = {{start.response.body.$}}

###
POST {{hostURL}}/state/interpreter/{{xmachineId}}
content-type: application/json
x-access-token: {{authToken}}

{{xstate}}

###
DELETE {{hostURL}}/state/machines/{{xmachineId}}
content-type: application/json
x-access-token: {{authToken}}
```
