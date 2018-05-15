## 웹서버를 node로 직접 구현하기
- nodejs를 이용해서 웹서버를 만드는 코드
```
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```
- 코드 해석
```
const http = require('http');
```
> 웹서버가 되기위해서는 node 모듈중에 http 모듈을 사용해야 함
```
const server = http.createServer();
또는
var server = http.createServer();
```
> 서버를 만들어 서버를 제어할 수 있도록 객체를 리턴하고 그 리턴한 값을 변수에 담음<br/>이 변수로 서버를 제어가능
```
server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
또는
server.listen(port, hostname, function(){
  console.log(`Server running at http://${hostname}:${port}/`);
});
```
> 서버를 만들고 첫번째 인자로 그 서버가 특정한 포트를 바라보게 함<br/>사용자가 해당 서버로 접속할때 어떤 IP를 이용해 들어온 사용자를 수용할 것인가를 두번째 인자로 정함
> listen은 시간이 걸릴 수 있기때문에 Callback을 이용해 비동기적으로 처리함<br/>즉, listen이 완료됐을 때 세번째 인자인 Callback 함수를 실행하게 함
> 서버가 리스닝에 성공하면 코드를 출력함
- 즉, 이 서버가 어떻게 들어온(hostname) 사용자의 응답(callback)을 받을것인가를 바라보게(listen)(=port)하는 것
- 정리 : 리스닝이 수립되면 웹서버는 특정포트를 바라보게되고, 이곳으로 사용자가 들어왔을때 어떤내용을 출력할것인지는 인자값으로 익명함수를 줌
- 정리2 : 특정포트가 웹서버를 바라보고 있게 설정하면, 웹서버의 포트를 통해서 웹서버로 접근할 수 있게됨
```
const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});
또는
var server = http.createServer(function(req, res){
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});
```
> 어떤 정보를 요청한 사용자에게 응답할것인가에 대한 값은 응답과 관련된 객체를 담고있는 두번째 매개변수(res)를 사용<br/>응답할값은 응답(res)을 가지고 있는 함수에서 진행

- `req(request) : 요청과 관련된 정보를 담고있는 객체`
- `res(response) : 응답과 관련된 정보를 담고있는 객체`

- 실행
```
node webserver2.js
```
- 결과
```
Server runnig at http://127.0.0.1:3000/
```
- 해당주소로 접속
```
Hello Wold
```



## 웹 프레임워크 (Express)
- [Express](expressjs.com/ko/)
- node를 직접 사용해서 웹에플리케이션을 구축하는것도 좋지만 node를 사용해 만들어진 프레임워크를 사용하면 서버쪽 에플리케이션을 좀 더 쉽게 구축할 수 있다.


### Express 설치
- 홈페이지접속 - 시작하기 메뉴 - [설치방법](http://expressjs.com/ko/starter/installing.html) 참고
1. 프로젝트를 위치시킬 디렉토리 설정
2. 해당 디렉토리에 `npm init`을 통해 npm이 관리하는 패키지로 선언
3. `npm install express --save`으로 npm이 express 패키지를 다운받아 프로젝트 폴더에 위치시킴
> 이미 init을 통해 package.json 파일이 존재한다면 설치만하면 됨
- 이것으로 express 프레임워크를 프로젝트에서 사용할 수 있는 상태가 됨
