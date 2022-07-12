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
  - 토큰의 유효기간은 1일이다.



##### 사용자 상세정보 업데이트

- 기능

  - 사용자의 아이디에 맞추어 상세정보를 업데이트 한다.

- 주소

  - http://devback.gongsacok.com:8080/svc/setUserDetail

- 요청예

  ``` json
  {
      "name":"test name!"
  }
  ```

- 응답예

  ``` json
  {
      "status": "success",
      "emsg": null,
      "data": "user detail info written",
      "page": null
  }
  ```

- 상세설명 및 주의사항

  - 헤더의 인증 토큰을 포함하여 통신한다.
  - 사용자 정보를 보내면, 로그인한 유저의 상세 정보를 수정한다.



##### 사용자 상세정보 가져오기

- 기능

  - 사용자의 상세정보를 가지고 온다.

- 주소

  - http://devback.gongsacok.com:8080/svc/getUserDetail

- 요청예

  ``` json
  {
  }
  ```

- 응답예

  ``` json
  {
      "status": "success",
      "emsg": null,
      "data": {
          "udid": null,
          "name": "test name!",
          "ruid": null,
          "useFlag": null,
          "createTime": null,
          "updateTime": null
      },
      "page": null
  }
  ```

- 상세설명 및 주의사항

  - 헤더의 인증 토큰을 포함하여 통신한다.
  - 로그인 한 유저의 상세정보를 가져온다.
  - 보내는 테이터는 Null 이 아닌 빈 json 파일이다.

##### 사용자 리스트 가져오기

- 기능

  - 등록된 사용자의 리스트를 가지고 온다.

- 주소

  - http://devback.gongsacok.com:8080/admin/listUser

- 요청예

  ``` json
  {
      "offset":0,
      "size":2
  }
  ```

- 응답예

  ``` json
  {
      "status": "success",
      "emsg": null,
      "data": [
          {
              "uid": 9,
              "userid": "aa",
              "passwd": null,
              "jtoken": null,
              "userrole": "ROLE_USER",
              "createTime": "2022-07-09T05:19:51.451155",
              "updateTime": "2022-07-09T05:19:51.451169",
              "udid": null,
              "name": null,
              "ruid": null,
              "useFlag": null,
              "udcreateTime": null,
              "udupdateTime": null
          },
          {
              "uid": 8,
            	......................
          }
      ],
      "page": {
          "totalElements": 7,
          "totalPages": 3
      }
  }
  ```

- 상세설명 및 주의사항

  - 헤더의 인증 토큰을 포함하여 통신한다.
  - 시작위치(페이지X한페이지의 크기 : offset) 와 한페이지의 크기(size)을 전송한다.
  - 리스트 반환시 조건에 맞는 전체 레코드의 갯수(totalElements)와 전송된 사이즈를 이용한 전체 페이지(totalPages) 값을 리턴한다.



#### 사업자

##### 사업자 정보 추가

- 기능

  - 관리자가 사업체를 등록한다.
  - 사업체의 상세정보는 등록한 업체의 아이디 값을 이용하여 별도의 api 를 이용하여 등록, 수정한다.

- 주소

  - http://devback.gongsacok.com:8080/admin/addCompany

- 요청예

  ``` json
  {
      "name":"company 04"
  }
  ```

- 응답예

  ``` json
  {
      "status": "success",
      "emsg": null,
      "data": {
          "cid": 4,
          "name": "company 04",
          "ruid": null,
          "createTime": "2022-07-12T15:49:06.144463",
          "updateTime": "2022-07-12T15:49:06.144498"
      },
      "page": null
  }
  ```

- 상세설명 및 주의사항

  - 관리자가 사업자 정보를 추가한다.
  - 입력된 데이터가 응답으로 리턴된다. 이를 이용하여 (cid) 사업자 상세정보 입력 api 를 이용할 수 있다.




#### Api 문서형태

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