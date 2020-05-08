
# CORS  
* Cross Origin Request Sharing  
#### [CORS 완벽 설명](https://www.youtube.com/watch?v=Ka8vG5miErk&t=3s)  


## 1. CORS란?  

* Cross Origin Resource Sharing  

### 1. CORS 이전에 SOP를 먼저 말하고자 한다.   

* Same Origin Policy는 다른 Origin에 대하여 **스크립트를 통한 ajax 실행**을 막는 것입니다.  
이 때, ajax 실행을 막는다는 것은 **요청은 가되, 브라우져에서 이를 보여주지 않는 것**을 의미합니다.  
>> 서버에 요청을 보낼 수 있되, 그 응답(200 OK이더라도) 을 브라우져가 읽지 못 한다.  


* 이 때 Origin은 **[프토토콜 + 도메인 + 포트 ]** 세 가지의 조합으로 식별됩니다.  

### 2. CORS의 필요성  

* 하지만 프론트를 서빙하는 서버와, 데이터를 보내주는 API 서버가 나눠짐에 따라  
SOP는 일종의 걸림돌이 되었고, **다른 출처에 대해서도 요청을 허용하는 방법**이 CORS입니다.  


### 3. CORS 요청의 방식  

#### 3.1. Simple Request  
* 요청의 타입이 GET, POST, HEAD인 경우 등등을 만족하면  
* 서버에서 **응답 헤더에 [Access-Control-Allow-Origin : *]**을 넣어서 보내주면 해석가능.  

![image](https://user-images.githubusercontent.com/62331555/81428694-97238c80-9197-11ea-9d3b-270e10299423.png)  

#### 3.2. Preflight Request  
* Simple Request의 조건을 만족하지 않는 경우  
Preflight Request를 수행한다.  

1. 요청의 헤더에 **Simple request 조건을 만족하지 않는** Content-type : application/json이 있는 경우 "흠, simple request가 아니군..." 이라고 브라우져가 판단한다.  
2. 브라우져는 **OPTION**헤더를 통해 Preflight request를 먼저 보낸다.  

3. 서버는 OPTION 헤더를 처리하는 로직 안에, access-allow 헤더를 통해 **허용되는 오리진**과 **허용되는 header**(이 경우 content-type)를 지정하여 허가한다.  
![image](https://user-images.githubusercontent.com/62331555/81429564-f0d88680-9198-11ea-9a55-4fb05af61971.png)  












