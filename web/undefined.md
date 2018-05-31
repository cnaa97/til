# 웹의 동작 과정

브라우저에서 주소 입력 후 엔터쳤을 때 어떤 일이 일어날까

두 가지로 나누어 볼 수 있다. 먼저 **HTTP 통신을 하는 네트워크 프로세스**와 브라우저 단에서 문서가 **랜더링**되는 과정이다. 

### 네트워크 \(http\)

1. 브라우저에 입력된 주소는, DNS 서버를 통해 IP로 변환된다.
2. 포트번호가 있다면 추출한다.
3. 웹서버와 TCP 커넥션을 맺는다.
4. 서버에 HTTP 요청을 보낸다.
5. 브라우저에 HTTP 응답을 전달한다.
6. 커넥션이 닫히면 브라우저는 해당 문자 타입에 맞는 양식으로 출력한다.

### 브라우저

![&#xBE0C;&#xB77C;&#xC6B0;&#xC800; &#xB79C;&#xB354;&#xB9C1;](../.gitbook/assets/image.png)

1. 돔 트리 구축을 위한 html 파싱
2. 랜더 트리 구축
3. 랜더 트리 배치 \(layout\)
4. 랜더 트리 그리기

---

#### 참고

[**브라우저는 어떻게 동작하는가?**](https://d2.naver.com/helloworld/59361)
