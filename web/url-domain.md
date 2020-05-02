

# URL 과 Domain  

* URL 은 Uniform Resource Location의 약자로서, 네트워크에서 자원을 고유하게 식별한다.  
* URI는 URL과 URN으로 구현된다.  
각각 자원에 대한 **위치** 혹은 **이름**을 통해 자원을 식별하는 메커니즘을 가진다.  

## 1. URL의 구조    

* **URL**은 [ **통신 프로토콜** + **도메인** + **포트** + **path** + **쿼리 스트링** ] 까지 포함된다.  

![image](https://user-images.githubusercontent.com/62331555/80870772-a8762000-8ce3-11ea-8409-07036f671492.png)  


## 2. 도메인의 구조  

* 도메인은 URL의 구성요소이다.  
* 도메인은 **여러 도메인의 합**이다.  

```
www.github.com
```
과 같이 있다면 

**1. ,** : **root** 맨 뒤에 생략된 .(닷)은 루트 도메인  
**2. com** : com은 Top Level Domain  
**3. github** : **Primary Domain**  
**4. www** : **서브도메인**  

## 3. 서브도메인  

```
https://www.skku.edu
```
* 위의 예에서의 **서브도메인**은 **www**이다.  

```
https://cs.skku.edu
```
* 하지만 위와 같이 다른 서브도메인을 쓴다면 **www는 없어진다.**  

만일 https://www.cs.skku.edu 로 하면 www가 다시 서브도메인이 되어, 없는 주소가 된다.  
































































