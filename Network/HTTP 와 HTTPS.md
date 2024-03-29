# HTTP (Hyper Text Transfer Protocol)
```
서버/클라이언트 모델을 따라 데이터를 주고 받기 위한 프로토콜. HTTP 는 애플리케이션 레벨로 TCP/IP 위에서 작동한다.
상태를 가지고 있지 않는 Stateless 프로토콜이며 Method, Path, Version, Headers, Body 등으로 구성된다.
```
![](https://images.velog.io/images/sangwoo24/post/5ac121e4-9ca2-4de0-886c-ec608105213f/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-05-08%20%EC%98%A4%ED%9B%84%2011.57.12.png)
<br><br>

## HTTP 의 문제점
#### 1. HTTP 는 평문 통신이기 때문에 도청이 가능하다.
> TCP/IP 구조의 통신은 전부 통신 경로 상에서 엿볼 수 있다. 패킷을 수집하는 것만으로도 도청할 수 있다. 평문으로 통신 할 경우 메세지의 의미를 파악할 수 있기 때문에 암호화하여 통신해야 한다.

##### 보완 방법
1. 통신 자체를 암호화 `SSL (Secure Socket Layer)` or `TLS (Transport Layer Security)` 라는 다른 프로토콜을 조합함으로써 HTTP 통신 내용을 암호화한다.
2. HTTP 메세지에 포함되는 콘텐츠만 암호화한다. 수신측에서는 그 암호를 해독하여 출력하는 처리가 필요하다.
<br><br>

#### 2. 통신 상대를 확인하지 않기 때문에 위장이 가능하다.
> HTTP 에 의한 통신에는 상대가 누구인지 확인하지 않기 때문에 누구든지 Request 를 보낼 수 있다. IP 주소나 포트 등에서 그 웹 서버에 엑세스 제한이 없는 경우, Request 가 오면 상대가 누구든지 무언가의 Response 를 반환한다.

##### 보완 방법
1. SSL 로 상대를 확인할 수 있다. SSL 은 상대를 확인하는 수단으로 **증명서** 를 제공하고 있다. 증명서는 신뢰할 수 있는 **제 3자 기관에 의해** 발행되는 것이기 때문에, 서버나 클라이언트가 실재하는 사실을 증명한다.
<br><br>

#### 3. 완전성을 증명할 수 없기 때문에 변조가 가능하다.
> 완전성이란, **정보의 정확성** 을 의미한다. 서버 또는 클라이언트에서 수신한 내용이 송신측에서 보낸 내용과 일치한다라는 것을 보장할 수 없는 것이다. Request 나 Response 가 발신된 후에 상대가 수신하는 사이에 누군가에 의해 변조되더라도(중간자 공격 = Man in the Middle) 이 사실을 알 수 없다.

##### 보완 방법
1. HTTPS 를 사용한다. SSL 에는 인증이나 암호화, 다이제스트 기능을 제공하고 있다.
<br><br><br><br>

# HTTPS
```
인터넷 상에서 정보를 암호화하는 SSL 프로토콜을 이용해 클라이언트와 서버가 자원을 주고 받을 때 쓰는 통신 규약.
공개키 암호화 방식으로 텍스트를 암호화한다.
```
<br>

- HTTP 는 텍스트 교환이므로, 누군가 네트워크에서 신호를 가로채면 내용이 노출되는 보안 이슈가 존재한다. 이런 보안 문제를 해결해주는 프로토콜이 **HTTPS** 이다.
- 새로운 애플리케이션 계층의 프로토콜이 아닌, HTTP 통신을 하는 소켓부분을 `SSL` or `TLS` 라는 프로토콜로 대체하는 것 뿐이다.
- HTTP 는 원래 TCP 와 직접 통신했지만, HTTPS 에서 **HTTP 는 SSL 과 통신**하고, **SSL 이 TCP 와 통신**을 하게 된다.
<br><br>


## HTTPS 의 문제점
- 평문 통신에 비해서 암호화 통신은 CPU 나 메모리 등 `리소스` 를 더 많이 요구한다.
- 통신할 때마다 암호화를 하면 추가적인 리소스를 소비하기 때문에 **서버 한 대당 처리할 수 있는 리퀘스트의 수가 상대적으로 줄어들게 된다.**
