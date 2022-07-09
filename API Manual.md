### API Manual

#### 사용자

##### 사용자 가입

- 기능

  - 서비스에 사용자를 등록한다. (사용자 신규가입)

- 주소

  - http://devback.gongsacok.com:8080/pub/addUser

- 요청예

  ``` json
  {
      "userid":"aa",
      "passwd":"aa"
  }
  ```

- 응답예

  ``` json
  {
      "status": "success",
      "emsg": null,
      "data": "",
      "page": null
  }
  ```

- 상세설명 및 주의사항

  - 사용자를 추가한다.

##### 로그인

- 기능

  - 서비스에 사용자의 아이디 패스워드를 이용하여 로그인한다.

- 주소

  - http://devback.gongsacok.com:8080/pub/login

- 요청예

  ``` json
  {
      "userid":"testuser",
      "passwd":"testuser"
  }
  ```

- 응답예

  ``` json
  {
      "status": "success",
      "emsg": null,
      "data": {
          "uid": 3,
          "userid": "testuser",
          "jtoken": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ0ZXN0dXNlciIsInJvbGVzIjoiUk9MRV9VU0VSLFJPTEVfQURNSU4iLCJpYXQiOjE2NTcyNTgwODgsImV4cCI6MTY1NzM0NDQ4OH0.V_fPsGNj6ebAbaIpSPGm638_3W6vfV5H3SeWH0dd-KY",
          "userrole": "ROLE_USER,ROLE_ADMIN"
      },
      "page": null
  }
  ```

- 상세설명 및 주의사항

  - 로그인 이후 api 통신을 위하여 jtoken을 사용한다.

##### Api 문서형태

- 기능

- 주소

- 요청예

  ``` json
  data
  ```

- 응답예

  ``` json
  data
  ```

- 상세설명 및 주의사항