## 설치방법
- [Node.js](https://nodejs.org/ko/) 홈페이지에서 설치

## 실행
- 윈도우키 + R 로 '실행'을 열어 cmd(터미널)에 접속
- node \-v 또는 node --version : 버전체크(설치유무 확인)
- npm -v 또는 npm --version : 버전체크
	- npm : node.js의 플러그인, 라이브러리(nodejs를 설치하면 자동으로 설치됨)

## Nodejs
- nodejs도 콘솔창을 이용해 디버깅을 함
- dir/w : 디렉토리를 보여줌

### 원하는 디렉토리(파일)로 들어오기
1. 터미널에서 접속 : 단, 한단계씩 들어가야함
```
cd 디렉토리명
```

2. 직접 접속 : 원하는 디렉토리에 들어가서 주소창에 cmd를 입력해서 접속

- hello.js
```
console.log('Hello world');
console.log(1+10);
```
- 실행
```
node hello.js
```
- 결과
```
Hello world
11
```
> 작성한 코드를 node.js를 통해서 실행시킴<br/>node.js의 런타임(환경)이 해당파일을 읽어서 코드를 해석해 출력해줌

- `node`를 입력하면 노드환경이 실행돼 직접입력해서 출력할 수 있음 (개발자도구의 콘솔창과 같음)
- `Ctrl + C : 노드환경에서 빠져나감`
