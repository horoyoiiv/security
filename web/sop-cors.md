

# SOP  
[Ref](https://okky.kr/article/406000)  


## Same Origin Policy  
* 웹 보안에 사용되는 정책  
1. 동일한 출처에 대해서만 자원의 요청을 허가하는 것.  

1. 동일한 출처가 아닌 경우 **AJAX 요청**을 하지 못한다.  
2. <img>, <link> 태그를 통한 다른 출처로의 자원 요청은 허용.  
3. <form> 태그를 통한 GET, POST의 다른 출처로의 요청도 허용.  

* **오로지 AJAX만 막는다.**  


### 1. 요청 자체가 가지 않는 것인가?  
* 요청은 서버로 가지만 응답을 브라우져에서 읽지만 못 하는 것이다.  
[보낼 수 있다. 하지만 읽을 수 없다.](https://security.stackexchange.com/questions/145013/when-does-the-same-origin-policy-prevent-a-request-from-being-sent)  

요청에 대한 응답으로 200 OK가 올 수 있다.  
하지만 헤더 내에 [Access-Control-Allow-Origin : * ]가 없는 **등**의 이유로 브라우져가 응답을 읽지 못함.  

![image](https://user-images.githubusercontent.com/62331555/81428457-3d22c700-9197-11ea-9dd7-01e1e6042c17.png)  


### 2. 출처란?  
* 출처는 **프로토콜**, **도메인**, **포트번호**로 식별된다.  
* **세 가지**다.  
```
https://www.github.com:443
```

### 3. 쿠키에 대한 출처  

* 쿠키에 한하여 출처는 **Domain**과 **Path**로 식별된다.  


## CSRF  
* Cross-Site Request Forgery  

### 1. 란?  
* SOP가 허용하는 범위인 **이미지, 폼 등 HTML 태그를 악용**하여 서버에 malicious한 요청을 보내는 것.  
* 이는 **해커가 만든 사이트에 방문**하게 하여 동작한다.  

### 2. <이미지> 태그를 이용  
* 해커의 사이트에 다음과 같은 코드가 인젝션되어있으면, GET 요청이 간다.  
```
<img src="http://bank.benzen.io/api/exit">
```
#### [방지] : GET 요청에 대해서 서버에 "사이드 이펙트"를 발생을 제한한다.  

### 3. <form> 태그를 통한 POST 요청  
* hidden type 등을 삽입하여 전송한다.  
```
<form name="hack" method="post" action="http://bank.benzen.io/api/exit">
   <input type="hidden" name="amount" value="100만원"/>
</form>
<script>document.forms.hack.submit();</script>
```

#### [방지] : 서버가 form태그 포함한 html 응답할 때, hidden 타입으로 **csrf token**을 미리 주입한다.   
csrf토큰이 유효한 경우에만 POST 요청을 인정.  


#### [방지] : SameSite  
* **쿠키의 속성에 SameSite를 추가**하면, 다른 오리진이 해당 쿠키를 전송하는 것을 막는다.  

![image](https://user-images.githubusercontent.com/62331555/80872044-816f1c80-8cea-11ea-84ff-e94471deca3b.png)  














### 대응








