# security
security

## Web  

#### 1. [Cookie](/web/cookie.md)  
#### 2. [URL & Domain](/web/url-domain.md)  
#### 3. [SOP - CSRF](/web/sop-cors.md)  
* **SOP**(Same Origin Policy) : AJAX에 대하여 다른 Origin으로의 요청의 결과를 막는 것.  
* **CSRF**(Cross Site Request Forgery) : <img>, <form> html 태그를 통하여 GET, POST 방식으로 위조된 요청을 보내는 것.  

#### 4. [XSS - Cross Site Sscripting](/web/xss.md)  
* CSRF는 html 태그를 악용했다면, XSS는 Script를 삽입하여 해킹.  
#### 5. [CORS](/web/cors.md)  
* 출처가 다른 서버에 스크립트를 통한 요청을 보내는 것을 허용하는 방법.  
* Simple request 와 Preflight request로 나뉜다.    


## TLS  
* Transport Layer 위에서, Application Layer 아래에서 동작하며, 상위에서 받은 페이로드를 암호화하고,  
밑에서부터 받은 세그먼트를 복호화하는 방식으로 보안 기능을 제공.  
* TLS는 대칭키, 비대칭키 두 가지 방식을 혼용. 대칭키 방식의 암복호화 퍼포먼스가 빠르기에 데이터 그 자체는 대칭키 방식으로 수행.  
* 문제는 대칭키를 주고 받는 것이고, 대칭키를 생성하기 위하여 비대칭키(RSA 혹은 디피-헬만) 방식 사용.  
그러나 TLS 1.3부터 RSA은 Perfect Foward Secrecy가 부족하여 배제.  

[1. TLS 1.2 and TLS 1.3](/tls/tls.md)  
[2. 인증서 동작](/tls/certificate.md)  
3. PKI (Public key Infrastructure)  
 * 공개 키 기반구조  
 * 보안에 취약한 인터넷을 공개키-비밀키인 비대칭키 방식으로 안전하게 한다?  
 * 공개키 방식은 **인증**에도 사용되고, **대칭키**를 교환하는데도 사용되니.  



