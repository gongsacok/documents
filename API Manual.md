### API Manual

#### 사용자

##### 사용자 가입 (사용자추가)

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
      "data": ""
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
      "data": {
          "uid": 3,
          "userid": "testuser",
          "jtoken": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ0ZXN0dXNlciIsInJvbGVzIjoiUk9MRV9VU0VSLFJPTEVfQURNSU4iLCJpYXQiOjE2NTcyNTgwODgsImV4cCI6MTY1NzM0NDQ4OH0.V_fPsGNj6ebAbaIpSPGm638_3W6vfV5H3SeWH0dd-KY",
          "userrole": "ROLE_USER,ROLE_ADMIN"
      }
  }
  ```
  
- 상세설명 및 주의사항

  - 로그인 이후 api 통신을 위하여 jtoken을 사용한다.
  - 토큰의 유효기간은 1일이다.



##### 사용자 리스트 조회

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
      "data": [
          {
              "uid": 9,
              "userid": "aa",
              "userrole": "ROLE_USER",
              "createTime": "2022-07-09T05:19:51.451155",
              "updateTime": "2022-07-09T05:19:51.451169"
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
      "data": "user detail info written"
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
      "data": {
          "name": "test name!"
      }
  }
  ```
  
- 상세설명 및 주의사항

  - 헤더의 인증 토큰을 포함하여 통신한다.
  - 로그인 한 유저의 상세정보를 가져온다.
  - 보내는 테이터는 Null 이 아닌 빈 json 파일이다.



#### 사업자

##### 사업자 정보 추가 (관리자)

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
      "data": {
          "cid": 4,
          "name": "company 04",
          "createTime": "2022-07-12T15:49:06.144463",
          "updateTime": "2022-07-12T15:49:06.144498"
      }
  }
  ```

- 상세설명 및 주의사항

  - 관리자가 사업자 정보를 추가한다.
  - 입력된 데이터가 응답으로 리턴된다. 이를 이용하여 (cid) 사업자 상세정보 입력 api 를 이용할 수 있다.



##### 사업자 리스트 조회 (관리자)

- 기능

  - 관리자가 사업체의 리스트를 조회한다.
  - 사업체의 상세정보는 등록한 업체의 아이디 값을 이용하여 별도의 api 를 이용하여 등록,수정한다.

- 주소

  - http://devback.gongsacok.com:8080/admin/listCompany

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
      "data": [
          {
              "cid": 5,
              "name": "company 05",
              "createTime": "2022-07-12T07:50:22.116937",
              "updateTime": "2022-07-12T07:50:22.116944"
          },
          {
              "cid": 4,
              "name": "company 04",
              ......................
          }
      ],
      "page": {
          "totalElements": 5,
          "totalPages": 2
      }
  }
  ```

- 상세설명 및 주의사항

  - 시작위치(페이지X한페이지의 크기 : offset) 와 한페이지의 크기(size)을 전송한다.
  - 리스트 반환시 조건에 맞는 전체 레코드의 갯수(totalElements)와 전송된 사이즈를 이용한 전체 페이지(totalPages) 값을 리턴한다.



##### 사업자 상세정보 업데이트 (관리자)

- 기능

  - 등록한 사업자의 상세 정보를 추가한다.
  - 등록한 사업자의 아이디(cid)를 이용하여 상세정보를 입력한다.

- 주소

  - http://devback.gongsacok.com:8080/admin/setCompanyDetailInfo

- 요청예

  ``` json
  {
      "rcid":1,
      "name":"test company 01",
      "comment":"사업자 간단 소개",
      "location":"신정동",
      "address":"서울시 양천구 사업장 주소",
      "registration":"01-30331-12345",
      "workTime":"09:00 ~ 18:00",
      "offer":"우리 회사의 제공 서비스 소개글은 어쩌구 저쩌구 이며\n 어쩌구 저쩌구 한 내용으로 어쩌고 저쩌고 한다.",
      "titleImg":1,
      "imgs":"1,3,4,5",
      "longitude":135084848,
      "latitude":382384233,
      "telnum":"02-1234-1234",
      "mobilenum":"010-1234-1234",
    	"email":"test@email.com",
    	"extnum":"080-1234-1234",
      "keywords":"내부분류 01",
      "tags":"테스트분류01,테스트분류02,테스트",
      "useFlag":1
  }
  ```

- 응답예

  ``` json
  {
      "status": "success",
      "data": {
          "cdid": 1,
          "name": "test company 01",
          "comment": "사업자 간단 소개",
          "location": "신정동",
          "address": "서울시 양천구 사업장 주소",
          "registration": "01-30331-12345",
          "workTime": "09:00 ~ 18:00",
          "offer": "우리 회사의 제공 서비스 소개글은 어쩌구 저쩌구 이며\n 어쩌구 저쩌구 한 내용으로 어쩌고 저쩌고 한다.",
          "titleImg": 1,
          "imgs": "1,3,4,5",
          "longitude": 13508484,
          "latitude": 3823842,
          "telnum":"02-1234-1234",
          "mobilenum":"010-1234-1234",
          "email":"test@email.com",
          "extnum":"080-1234-1234",
          "keywords": "내부분류 01",
          "tags": "테스트분류01,테스트분류02,테스트",
          "useFlag": 1,
          "rcid": 1,
          "createTime": "2022-07-19T13:23:48.101372",
          "updateTime": "2022-07-19T13:23:48.101419"
      }
  }
  ```

- 상세설명 및 주의사항

  - 상세 정보를 입력하고자 하는 id를 먼저 가져와서 해당 아이디를 rcid 값에 설정하고 상세정보를 입력한다.
  - 이름 항목은 사업자 정보와 다름에 주의한다.
  - 타이틀이미지(titleImg)는 이미지의 번호를 이용한다.
  - 여러개의 이미지(imgs)는 쉼표로 구분된 번호의 리스트를 사용한다.
  - 이미지의 번호 (이미지 아이디)는 이미지 업로드 후 반환된다.
  - 경도(longitude)와 위도(latitude)는 소수점 다섯자리까지 정수형태( * 100000) 로 이용한다.




##### 사업자 상세정보 조회 (관리자)

- 기능

  - 사업자의 상세정보를 조회한다.
  - 사업자 아이디 번호를 이용하여 해당 상세정보를 지정한다.

- 주소

  - http://devback.gongsacok.com:8080/admin/getCompanyDetailInfo

- 요청예

  ``` json
  {
      "rcid":1
  }
  ```

- 응답예

  ``` json
  {
      "status": "success",
      "data": {
          "cdid": 1,
          "name": "test company 01",
          "comment": "사업자 간단 소개",
          "location": "신정동",
          "address": "서울시 양천구 사업장 주소",
          "registration": "01-12345678-12345",
          "workTime": "09:00 ~ 18:00",
          "offer": "우리 회사의 제공 서비스 소개글은 어쩌구 저쩌구 이며\n 어쩌구 저쩌구 한 내용으로 어쩌고 저쩌고 한다. 그래서 좋은 회사다.",
          "titleImg": 1,
          "imgs": "1,3,4,5,11",
          "longitude": 135084848,
          "latitude": 382384233,
          "telnum": "02-1234-1234",
          "mobilenum": "010-1234-1234",
          "email": "test@email.com",
          "extnum": "080-1234-1234",
          "keywords": "내부분류 01",
          "tags": "테스트분류01,테스트분류02,테스트",
          "useFlag": 1,
          "rcid": 1,
          "createTime": "2022-07-19T16:11:41.011005",
          "updateTime": "2022-07-19T16:11:41.011028"
      }
  }
  ```

- 상세설명 및 주의사항

  - 각 항목은 상세정보 업데이트 항목을 참고 하도록 한다.




#### 이미지

##### 이미지 업로드

- 기능

  - 일반적인 form-data 전송모드를 이용하여 이미지 한장 또는 여러장을 업로드 한다.

- 주소

  - http://devback.gongsacok.com:8080/svc/upImages

- 요청예

  ``` json
  form name = "imgs"
  ```

- 응답예

  ``` json
  {
      "status": "success",
      "data": [
          {
              "iid": 9,
              "storagePath": "https://gongsacok-dev.s3.ap-northeast-2.amazonaws.com/1658314185_KakaoTalk_Photo_2022-06-10-12-38-12.jpeg"
          },
          {
              "iid": 10,
              "storagePath": "https://gongsacok-dev.s3.ap-northeast-2.amazonaws.com/1658314185_photo-1554469384-e58fac16e23a.jpeg"
          }
      ]
  }
  ```

- 상세설명 및 주의사항

  - 업로드 된 이미지의 저장소 url을 storagePath 변수를 이용해 리턴한다.
  - 이미지의 iid를 리턴한다.
  - 저장된 이미지를 다시 가져오는 경우 리턴된 iid 를 이용하여, 이미지 url을 조회할 수 있다.



##### 이미지 url 조회

- 기능

  - 저장된 이미지를 이미지 아이디를 이용하여 url을 가져온다.

- 주소

- 요청예

  ``` json
  {
      "imgs":"5,9,990"
  }
  ```

- 응답예

  ``` json
  {
      "status": "success",
      "data": [
          {
              "iid": 5,
              "storagePath": "https://gongsacok-dev.s3.ap-northeast-2.amazonaws.com/1658313764_KakaoTalk_Photo_2022-06-10-12-38-12.jpeg"
          },
          {
              "iid": 9,
              "storagePath": "https://gongsacok-dev.s3.ap-northeast-2.amazonaws.com/1658314185_KakaoTalk_Photo_2022-06-10-12-38-12.jpeg"
          }
      ]
  }
  ```

- 상세설명 및 주의사항

  - 이미지 아이디 여러개 또는 한개를 보낼수 있다.
  - 여러개의 이미지를 요청하는 경우 중간에 없는 아이디가 있더라도, 결과가 있다면, 리턴함.



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