


## SSL Certificate  
[Ref](https://jusths.tistory.com/134)  

#### 1. **certificate**은 SSL handshake과정에서 서버에서 -> 클라이언트로 보내진다.  
#### 2. 클라이언트의 브라우저 혹은 OS는 **Root CA의 Certificate**을 가진다.
* linux에서는 **/etc/ssl/certs 디렉토리** 아래에 soft link 등으로 .crt 파일이 있다.  
.pem 은 인증서를 나타내는 확장자. (base64로 인코딩된 ASCII)    
.crt 는 유닉스/리눅스 기반에서의 인증서 확장자.
#### 3. Root CA의 인증서는 OS가 관리한다.  
![image](https://user-images.githubusercontent.com/62331555/80817835-20bde200-8c0d-11ea-92f5-85a26ed27a4d.png)  
스스로를 서명했으니, 인증서 그 자체를 가지고 있다가 

나중에 특정 인증서의 issuer가 Root면 (OS에 있는) Root CA의 인증서에서 **Public KEY**를 빼내준다.  


#### 4. **Intermeidate CA의 인증서**는 서버가 자신의 인증서를 발급 받을 때 같이 받으므로 클라이언트에 두 개를 준다.  
자신의 인증서와 자신을 발급해준 CA의 인증서  


#### 5. Chain of Trust  
Root CA - Intermidiate  CA - Server  
* 서로 모르는 두 명이 서로 아는 한명을 매개로 서로를 신뢰하게 되는 방법.  
* Root CA가 Intermediate CA를 인증해줬다면, Intermediate CA로부터 인증받은 서버는  
자신의 인증서와, 자신을 인증해준 Intermediate의 인증서를 동시에 클라이언트보내어 연쇄적으로 인증되게 하는 것.  


### 1. Certificate 발급 과정  

1. 서버A는 CA에게 인증서 발급을 요청한다.  
이 때, 자신의 public key를 제공한다.  

2. CA는 서버A를 조사한 후 신뢰성있다면 인증서를 발급해준다.  
서버A의 public key와 서버A의 도메인 주소(CN) 등의 정보를 **SHA256**을 통해 **HMAC** 생성.  
이 MAC 값을 **CA의 private key**로 암호화한 값이 **Signature**다.  

3. 인증서는 [ 서버A의 정보를 암호화한 값 + CA의 서명 ]  

![image](https://user-images.githubusercontent.com/62331555/80817011-91fc9580-8c0b-11ea-8afe-d1d4625ce6d6.png)  




### 1. Certificate 구성요소  

* 1. CN(Common Name) : server의 domain 이름  
* 2. 유효기간  
* 3. 서명  
* 4. 서버의 Public key  
-  RSA 방식으로 대칭키 교환 시에는 서버의 Public Key로 PMK를 감싸서 전송했지만
이제는 DH에서는 **인증**의 용도로만 사용?  



