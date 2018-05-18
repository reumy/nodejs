## Node-mysql
- javascript를 이용해 mysql을 제어할때 사용
- 서버는 정보를 응답하고 클라이언트는 정보를 요청하며 서버와 클라이언트는 상대적이다.<br/>우리 앱은 MySQL에게 정보를 요청하는 입장에서 클라이언트지만, 웹브라우저로 접속한 사용자에게는 서버가 된다.


## Node-mysql 접속
- [Node-mysql 메뉴얼](https://github.com/mysqljs/mysql) 참고
1. 설치
```
npm install node-mysql --save
```

2. 가져오기
database_mysql.js
```
var mysql = require('mysql');
var conn = mysql.createConnection({
  host     : 'localhost',    // mysql 서버의 위치
  user     : 'root',         // 접속 아이디 
  password : '****',         // 비밀번호
  database : 'o2'            // db 이름
});
```

3. 연결 (커넥트)
```
conn.connect();
```

4. 코드작성
- 기본코드
```
conn.query('SELECT 1 + 1 AS solution', function (error, results, fields) {
  if (error) throw error;
  console.log('The solution is: ', results[0].solution);
});
```
- 변경
```
var sql = 'SELECT * FROM topic';
conn.query(sql, function(err, rows, fields){
  if(err){
    console.log(err);
  } else {
    console.log('rows', rows);
    console.log('fields', fields);
  }
});
```
> row는 배열로 출력됨
- 코드분석
```
conn.query(sql, function(err, rows, fields){...});
```
> query는 변수 conn이 가르키는 접속에 해당하는 서버를 대상으로 query(지리)를 보냄<br/>첫번째 인자로 sql 문서가 전달되고 서버가 받아서 작업을 처리한 후 처리가 끝나면 mysql 모듈이 콜백 function을 호출함

- `fields : column 목록`

5. 연결끊기
```
conn.end();
```
> 작업이 끝나면 커넥션을 끊어 접속을 끊음 (ctrl+c가 자동으로 되는것과 같음)

- 실제로는 이렇게 직접 호스트의 비밀번호를 작성하면 안되고 별도의 파일로 빼서 다른사람과 공유하지않는 코드를 관리해야함
