
# cookie  

* 서버로부터 생성되어, 클라이언트에서 저장되는 정보.  

## 1. 쿠키의 헤더   

* 서버의 응답  
**Set-Cookie** 헤더 필드에 그 값을 채워서 보낸다.  
```
HTTP/1.1 200 OK
Set-Cookie: session-id=123123; 
```

* 클라이언트의 쿠키 전송  
**Cookie** 헤더 필드에 그 값을 채워서 보낸다.  
```
GET http://www.google.com/ HTTP/1.1
Cookie: session-id=123123;
```

## 2. 쿠키의 구조  
* 쿠키는 key, value, domain, path, expire time 등이 저장된다.  
```
Name          Value         Domain                  Path          expire time
---------------------------------------------------------------------------------
session-id    123123        github.com            /horoyoii
```

## 3. 쿠키의 유효범위  

#### domain 필드  
**서버가 도메인을 명시**하는 경우 .github.com 으로 앞에 .(닷)이 붙게 된다.  

이 때, 이러한 쿠키는 **서브도메인**으로 요청에도 유효하게 전송된다.  
ex) sub.github.com 

#### path 필드   
서버가 패스를 명시하는 경우 그 **패스**와 **하위 패스**까지가 유효범위가 된다.  
  
path= /horoyoii 로 지정했다면  
github.com/horoyoii  
github.com/horoyoii/profile  
까지 유효하게 쿠키가 같이 전송된다.  
  
github.com  
은 안된다.  


```
Name          Value         Domain                  Path          expire time
---------------------------------------------------------------------------------
session-id    123123        github.com            /horoyoii
```








