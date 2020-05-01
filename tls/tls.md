

# TLS  
* 네트워크 상에서 주고 받는 데이터에 대한 **암호화 및 복호화를 수행하는 레이어**로서, **대칭키 방식**으로 암호화를 수행하되, 그 대칭키는 **비대칭키 방식**으로 주고받는다.  
* SSL 1.3에서 표준이 되면서, TLS 1.0으로 명명.  
* TLS 1.2의 취약점으로 TLS 1.3이 사용됨.  

## 1. 주요 기능  

#### 1. 클라이언트-서버 간의 서로에 대한 **인증**(Authentication)  
* 3rd party에 의한 인증서 기반으로 서로가 인증된다.    

#### 2. Message Integrity 확인  
* HMAC이 메세지와 함께 암호화되면서...  

#### 3. 암호화 및 복호화  

## 2. 개요  

#### 1. 여러 프로토콜 레이어로 구성됨.  
* **1. Handshake Protocol** : tcp 3-way 후 ssl session을 수립하는 프로토콜     
* **2. TLS Record Protocol** : 메세지에 대한 암-복호화를 진행하는 프로토콜  

#### 2. Record Protocol의 간략한 동작  
![image](https://user-images.githubusercontent.com/62331555/80805935-45f22680-8bf4-11ea-9192-e9732742bd56.png)  
1. **단편화** 수행  
2. **압축** 수행 optional  
3. 압축된 메세지에 대한 **MAC** 생성  
4. [ 압축된 메시지 + MAC ] 에 대한 **암호화** 적용 + 헤더  

* MAC : Message Authentication Code  
1. 메세지 변조 확인 등 Integrity확인을 위해 사용된다.  
2. 그 한 종류로서 HMAC이 있다. Hash based MAC  
3. 그리고 HMAC에는 **MD5**와 **SHA**가 있다.  


## 3. TLS 1.2  
#### 1. **RSA**를 **Key Exchange**로 사용하게 될 때  

![image](https://user-images.githubusercontent.com/62331555/80807615-a71bf900-8bf8-11ea-9d07-4177f5a7c5d0.png)  
* 1. client hello ->: ssl 게시 요청 / session id / client가 지원하는 **암호화 방식 목록**(Cipher Suite)  
* 2. <- server hello : 목록에서 선택한 암호화 방식 하나  
* 3. <- certificate : 서버의 공개키가 포함된 인증서 signed by CA  
* 4. -> ClientKeyExchange : **PMS**를 서버의 공개키로 암호화하여 전송, PMS로부터 대칭키 생성됨.  

#### 2. **DH**를 **Key Exchange**로 사용하게 될 때  
* 다른 점 : **서버 측에서 자신의 DH 공개키와 DH 매개변수**를 전송  
![image](https://user-images.githubusercontent.com/62331555/80807928-58bb2a00-8bf9-11ea-89b0-847ee92f4be2.png)  


## 4. TLS 1.3  
[*Goood](https://b.luavis.kr/server/tls-1.3)  

### 1. TLS 1.2와의 차이  
#### 1. TLS 1.2는 2-RTT로 느리다.  
* 1-RTT  
* ClientHello의 "Key Share"필드에 DH의 공개키를 바로 보낸다.  
* 이를 통해 서버는 ServerHello에 자신의 DH 공개키를 보내면서, 바로 암호화 게시됨.  

* 0-RTT : PSK(Preshared key)를 공유하여, 세션을 다시 사용 시 PSK와 함께 바로 암호화된 데이터를 보낼 수 있다.  


#### 2. 키 교환방식의 RSA 사용은 보안취약점이 발생 - **Perfect Forward Secrecy**  
PFS는 향후에 키가 노출되었을 때 모두 해독되어 버리는 상황  
RSA방식은 서버의 pub key로 대칭키를 전송하기에, 향후 서버의 private key가 노출되면 PFS가 보장안됨.  

* **그래서 여러 방식이 제거됨**  
1. 키 교환에서의 RSA | 인증서에 대한 인증에는 여전히 사용  
2. MD5, SHA-1, DES 등 제거  

**키교환** : 일시적 디피 헬만  
**인증** : RSA  
**암호화** : AES  




























 

 



