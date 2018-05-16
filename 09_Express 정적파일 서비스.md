## 동적인 정보, 정적인 정보
- 동적인 정보 : 프로그래밍적으로 만들어진 정보
- 정적인 정보 : 사람이 한번 작성해 만들어진것과 같이 언제나 똑같이 보이는 정보


## 정적파일 서비스하기
1. 정적인 파일이 위치할 디렉토리를 지정하는 코드를 입력함
```
app.use(express.static('디렉토리명'));
```
> public 디렉토리를 정적인 파일들이 위치한 디렉토리로 지정함

- 디렉토리명은 관습적으로 public을 많이 사용

2. 해당 디렉토리에 서비스할 정적인 파일을 담음

- 코드작성
```
app.use(express.static('public'));

app.get('/route', function(req, res){
	res.send('Hello Router, <img src="/reumy.jpg">')
});
```
> app.js 파일에 위에 코드를 추가함

- 실행
```
node app.js
```
- 접속
```
localhost:3000/route
```
- 결과

![결과](img/node14.png)<br/>

- Network

![결과](img/node15.png)
> 웹페이지에서 로드하는 내용을 볼 수있음
