# TDD-TEST

1. 첫 API 테스트 만들기

  성공
  - 유저 객체를 담은 배열로 응답한다.
  - 최대 limit 갯수만큼 응답한다.

  실패
  - limit이 숫자형이 아니면 400을 응답한다.
  - offset이 숫자형이 아니면 400을 응답한다. (DB를 붙일 시 진행)

2. GET /user/:id

  success
  - id가 1인 유저 객체를 반환한다.
  
  error
  - id가 숫자가 아닐경우 400으로 응답한다.
  - id로 유저를 찾을 수 없을 경우 404로 응답한다.

3. DELETE /users/:id

  success
  - 204를 응답한다.

  error
  - id가 숫자가 아닐경우 400으로 응답한다.

4. POST /users

  success
  - 201 상태코드를 반환한다.
  - 생성된 유저 객체를 반환한다.
  - 입력한 name을 반환한다.

  error
  - name 파라미터 누락시 400을 반환한다.
  - name이 중복일 경우 409를 반환한다.

에러 -> DELETE 테스트에서 이미 '/users/1' 을 삭제했기 때문에
       POST 테스트에서 '/users' .send({name : 'alice'})를 했을 시 테스트에 실패하였습니다. 그래서 alice가 아닌 post로 추가해준 daniel로 바꿔줌.
5. PUT /users/:id

  success
  - 변경된 name을 응답한다

  error
  - 정수가 아닌 id일 경우 400 응답
  - name이 없을 경우 400 응답
  - 없는 유저일 경우 404 응답
  - 이름이 중복일 경우 409 응답

6. 코드 정리
  
  - 역할에 따라 파일로 분리하기
    - api/user/index.js
    - api/user/user.ctrl.js
    - api/user/user.spec.js
   
   * 환경변수 사용 NODE_ENV=test 
    process라는 객체에 할당됨. 
   * 근본적인 문제 app.listen을 지운 이유
    테스트 코드 api/user/user.spec.js 에서 supterTest에서
    Request(app) 내부적으로 express 서버를 구동하여 중복으로 일어나고 있기 때문에 index.js에서 app.listen을 지웠음.

7. Sequlize사용하여 DB 만들기
  
  - DB에 맞춰서 user.ctrl.js 코드 변경