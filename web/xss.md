

# XSS  

* Cross Site Scripting  
* CSRF가 html 태그를 통한 요청이였다면 XSS은 웹 게시판 등에 **Script**를 삽입하여 해킹을 시도하는 것.  
[Good Site](https://stupidsecurity.tistory.com/17)  


## What  
![image](https://user-images.githubusercontent.com/62331555/81004932-1fe4b480-8e88-11ea-88f9-da63f398c678.png)  

* 웹 어플리케이션에서 **사용자의 입력값을 제대로 필터링**하지 않으면 **Malicious Script Code**가 웹 서버에 삽입된다.  
  
  
* 이후 이 스크립트 코드가 다른 유저의 요청에 대한 결과의 일부로 전송되면서 그 유저의 브라우져에서 실행되는 것.  

1. Reflected XSS  
2. Stored XSS  
3. DOM-based XSS  

## 1. Reflected XSS  
* **URL의 일부(query string의 value 등)에 script를 삽입**하여 해킹하는 것.   

![image](https://user-images.githubusercontent.com/62331555/81005349-c16c0600-8e88-11ea-80a0-5fc3e1f04943.png)  


## 2. Stored XSS  
* 해커는 서버에 **게시글** 등을 저장하여, 서버의 DB에 Malicious Script를 저장시킨 후 유저가 그 페이지를 요청했을 때 동작하게 한다.  

![image](https://user-images.githubusercontent.com/62331555/81005656-422b0200-8e89-11ea-8406-509b067ec645.png)  


## 3. Dom-base XSS  
* URL의 **Fragment** 등에 Script가 삽입되어, **서버에는 그 스크립트가 가지 않고** 브라우저에서 실행된다.  

![image](https://user-images.githubusercontent.com/62331555/81006162-02b0e580-8e8a-11ea-80de-2bfc671bf0e6.png)  


## 대응  

1. **서버에서 요청에 대한 입력값을 필터링**해야 한다.  













