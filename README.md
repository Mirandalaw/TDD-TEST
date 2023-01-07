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
