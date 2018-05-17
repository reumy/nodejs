## Supervisor
- nodejs를 자동으로 재시작해줌
- `왓치기능 : 변경된 사항을 보고있다가 변경이 일어나면 자동으로 노드를 내부적으로 껐다켜서 실행을 시켜줌`
- npm 홈페이지 - supervisor 검색 - [설치방법과 메뉴얼](https://www.npmjs.com/package/supervisor) 참고
```
npm install supervisor -g
```
> 설치
```
supervisor app.js
```
> 실행

- 이제는 javascript 코드변경 후 저장하면 자동적으로 node를 재시작해줌 
