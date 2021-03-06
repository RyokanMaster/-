# 네트워크 서비스와 어플리케이션 
*written by sohyeon, hyemin 💡*

<br>

### 글 목차
### [1. 어플리케이션 계층이란?](#1-어플리케이션-계층이란-1)
### [2. HTTP 프로토콜](#2-http-프로토콜-(hyperText-transfer-protocol)-1)
### [3. 이메일 프로토콜](#3-이메일-프로토콜-1)
### [4. 기타 프로토콜](#4-기타-프로토콜-1)

- - - 

## 1. 어플리케이션 계층이란?

`어플리케이션 계층`은 사용자가 직접 사용하며 체감할 수 있는 서비스를 제공한다.  

<img src="./resources/applicationLayer.jpg" width="500px">

네트워크 계층 모델 중 트랜스포트 계층 이하 계층들은 데이터 전송을 담당하고 있으므로  
데이터 전송 관련 계층을 제외한 모든 영역이 어플리케이션 계층의 범주이다.  

### 2) 프로토콜

- 사용자가 직접 사용하는 프로토콜

|프로토콜|동작방식|
|:---:|:---:|
|HTTP|웹 클라이언트와 웹 서버 사이에서 웹 페이지 데이터를 주고 받음|
|POP, SMTP, IMAP|메일을 송수신하고 보관|
|SMB, AFP|LAN 안에서 파일을 공유|
|FTP|서버를 통해 파일을 주고 받음|
|Telnet, SSH|원격에서 서버를 제어|

- 사용자가 간접적으로 사용하는 프로토콜

|프로토콜|동작방식|
|:---:|:---:|
|DNS|도메인명과 IP 어드레스의 정보를 서로 변환할 때 사용|
|DHCP|LAN 내의 컴퓨터에게 IP어드레스를 할당할 때 사용|
|SSL/TLS|통신 데이터를 암호화하여 주요 정보를 안전하게 주고받을 때 사용|
|NTP|네트워크에 연결된 장비들의 시스템 시간을 동기화할 때 사용|
|LDAP|네트워크에 연결된 자원(사용자, 장비)의 통합관리에 필요한 디렉터리 서비스를 제공할 때 사용|


## 2. HTTP 프로토콜 (HyperText Transfer Protocol)

인터넷 상에서 데이터를 주고 받기 위한 서버-클라이언트 모델을 따르는 프로토콜

`웹 브라우저`가 `웹 서버`로 특정 `웹 페이지`를 요청하면  
웹 서버가 해당 페이지의 내용을 `HTML`형식으로 응답한다.  

웹 브라우저는 이 데이터를 해석해 웹 페이지 화면을 그린 후 사용자에게 보여줌  
웹 페이지에는 HTML형식 외에 화면 구성에 필요한 각종 파일들의 정보도 함께 포함되어 있다.  
(HTML, CSS, JAPE, Javascript ..)

### 1) 동작 방식

클라이언트와 서버들은 데이터스트림과 대조적으로 개별적인 메시지 교환에 의해 통신한다.  
브라우저인 클라이언트에 의해 전송되는 메시지를 `요청(request)`이라고 부르고,  
그에 대한 서버의 응답 메시지를 `응답(responses)`이라고 한다.  

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FUcQRY%2FbtqwN2z0cDP%2FDHzD3NeoEgxQM92JoHJXV0%2Fimg.png" width="700px">

HTTP는 `Connectless` 방식으로 작동한다.  
서버 연결 후 요청에서 응답을 받으면 연결을 끊는다.    
필요한 자원하나에 대해서 하나의 연결을 만들게 된다.  

`Connectionless`로 인해 서버는 클라이언트를 식별할 수가 없는데,  
이렇게 상태 정보를 저장하지 않는 통신 형태를 `Stateless`라고 한다.

### 2) 메시지 구조

|메시지 구조|
|:---:|
|요청 정보 행(request line)/</br>응답 정보 행(response line)|
|헤더</br>(header)|
|빈 줄</br>(blank line)|
|메시지 바디</br>(message body)|

- 요청 정보행/응답 정보 행

메시지의 종류나 상태를 표시

- 헤더

메시지에 대한 상세한 정보가 포함

- 메시지 바디

응답인 경우 이 부분에 HTML데이터가 들어감

### 3) URL

인터넷 상의 자원의 위치를 말하며, 특정 웹 서버에서 특정 파일 접근을 위한 경로 혹은 주소를 말한다.  
웹상에서 문서, 이미지, 동영상 등 어떤 자원에 접근하고자 할때  
이 URL을 통해 자원의 위치를 확인하고 자원을 얻게 된다.  

```
https://www.hyem-study.tistory.com/entry/14
```

보통 URL은 위 처럼 생겼다.

- https -> 자원에 접근하기 위한 프로토콜
- www -> 호스트 (서버의 이름 혹은 역할을 명시)
- hyem-study.tistory.com -> IP주소 또는 도메인 이름 (서버를 운영하는 조직 명시)
- /entry/14 -> 문서의 경로, 자원의 이름

이렇게 구성되어 있다.

### 4) 메서드 (Method)

메서드는 요청의 종류를 서버에게 알려주기 위해서 사용된다.

- GET : 정보를 요청하기 위해서 사용한다. (SELECT)
- POST : 정보를 밀어넣기 위해서 사용한다. (INSERT)
- PUT : 정보를 업데이트하기 위해서 사용한다. (UPDATE)
- DELETE : 정보를 삭제하기 위해서 사용한다. (DELETE)

- HEAD : (HTTP)헤더 정보만 요청한다.  
해당 자원이 존재하는지 혹은 서버에 문제가 없는지를 확인하기 위해서 사용한다.

- OPTIONS : 웹서버가 지원하는 메서드의 종류를 요청한다.

- TRACE : 클라이언트의 요청을 그대로 반환한다.  
예컨데 echo 서비스로 서버 상태를 확인하기 위한 목적으로 주로 사용한다.

GET, POST 만으로도 모든 종류의 요청을 표현하고 웹 서비스 개발에 큰 문제는 없다.  
하지만 Restful API 서버의 경우에는 GET, POST, DELETE, PUT을 명시적으로 구분한다.  

자원의 위치 뿐만 아니라 자원에 할 일 까지 명확히 명시할 수 있기 때문에  
Open API서버를 만들기 위해서 널리 사용된다.  

### 5) 쿠키

HTTP는 무상태 프로토콜이기 때문에 요청과 응답 과정에서 상태정보를 저장하지 않는다.  
따라서 여러 건의 요청이 들어올 때 동일 요청자인지 다른 요청자인지 판단하지 못한다.  

여러건의 요청 처리를 동일한 사용자 접속 세션으로 인식할 수 있도록 `쿠키`를 사용한다.  

-> 사이트가 사용자를 추적하게 해줌  

## 3. 이메일 프로토콜

이메일 송수신에는 SMTP, POP, IMAP과 같은 여러 프로토콜이 사용된다.  
`송신`과 `수신`에 서로 다른 프로토콜을 사용한다.  

* 송신 - SMTP
* 수신 - POP, IMAP

### 1) SMTP

SMTP 프로토콜은 클라이언트 PC가 메일 서버로 메일을 보낼 대만 사용되는 것이 아니라,  
발신자의 메일 서버에서 수신자의 메일 서버로 메일을 중계할 때도 사용된다.  

`stateful` 프로토콜이기 때문에 전송 종료 명령이 보내져야 통신을 종료한다.  

* SMTP의 인증

SMTP에는 POP와 같은 사용자 인증 체계가 없기 때문에 스팸 메일 방송 등에 악용되곤 한다.  
따라서,

- POP 서버의 인증기능을 활용
- 다른 네트워크로부터의 SMTP 접근을 제한
- SMTP Auth 프로토콜 활용 (SMTP에 사용자 인증 기능이 추가된 확장 프로토콜)

등의 방법으로 인증 체계를 구축한다.  


### 2) POP

SMTP 프로토콜을 통해 전송된 메일은 최종적으로 수신자의 메일 서버에 저장된다.  
이후 메일 서버에 저장된 메일을 확인할 때는 `POP` 프로토콜을 사용한다.  
메일을 수신하는 것 외에도 수신한 메일 건수나 용량 확인, 메일 삭제와 같은 처리에도 사용한다.  

#### 단점

클라이언트가 메일을 수신하면 메일 서버에 보관된 메일을 삭제하게 되어있다.
메일을 오랫동안 보관하려면 클라이언트 PC에 메일을 보관할 저장 공간을 확보해 두어야 한다. 

### 3) IMAP

POP와 달리 클라이언트 PC가 메일을 수신하더라도 메일 서버에서 수신한 메일을 지우지 않고 보관하게 되어 있다.  
메일 저장 공간이 충분하지 않은 스마트폰 등의 휴대기기에서 많이 활용된다.  

## 4. 기타 프로토콜

### 1) P2P (peer to peer)

특별히 공유를 위한 서버를 별도로 준비하지 않고 공유할 컴퓨터끼리 네트워크에 접속해 파일을 공유한다. 
각각의 피어가 서버/클라이언트 역할들 둘 다 한다.  

### 2) FTP (File Transport Protocol)

`FTP`는 파일 전송 프로토콜이다.  
주로 인터넷에 연결된 서버에 파일을 전송할 때 사용된다.  

두가지 접속 형태가 있다.  
- 데이터 커넥션 : 파일을 주고 받기 위한 접속
- 컨트롤 커넥션 : 명령어를 보내기 위한 접속

이렇게 접속 형태가 분리되어 있어  
파일 전송 중에도 명령을 줄 수 있어서 전송 중인 파일을 중단시키는 것이 가능하다.  

<br> 

## Reference & Additional Resources

> TCP/IP 쉽게, 더 쉽게
