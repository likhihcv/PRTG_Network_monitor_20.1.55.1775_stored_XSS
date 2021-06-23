# PRTG Network Monitor v20.1.55 to 21.2.68.1492 - stored XSS
Stored XSS (Cross Site Scripting) on PRTG Network Monitor version 20.1.55 to 21.2.68.1492

Exploit Title: Stored XSS (Cross Site Scripting)
Date: 10/06/2021  
Exploit Author: Likhith CV  
Vendor Homepage: https://www.paessler.com/  
Software Link: https://www.paessler.com/prtg  
Test on Version: 20.1.55.1775+ and 21.2.68.1492+    
Affected Versions: not tested on other versions  

## Observation
Stored cross site scripting vulnerability was observed on the PRTG Network Monitor version 20.1.55 to 21.2.68.1492. Any authenticated user can create a map with stored XSS payload by using Map Designer.

Severity: High

### Steps To reproduce:

Login to PRTG Network monitor

Click on Add Map
![1](https://user-images.githubusercontent.com/36541248/122042772-9f62e800-cdeb-11eb-8db8-12c58ce89ec7.png)

Enter Name of the map and select "Allow Public Access" (it will allow Map with our XSS payload accessible to anyone)
![2](https://user-images.githubusercontent.com/36541248/122042778-a12cab80-cdeb-11eb-98fa-c76b2cdcfe35.png)

Drag and drop an Icon and paste XSS payload in "HTML After" property 

```javascript
<img src=x onerror=alert(1337)//">

```

![4](https://user-images.githubusercontent.com/36541248/122042787-a2f66f00-cdeb-11eb-9947-98fbd12e9c76.png)

XSS payload gets executed whenever any user access this Map's public URL or if any admin logins and check the map
![xss](https://user-images.githubusercontent.com/36541248/122042789-a4279c00-cdeb-11eb-8965-4fe60665e8be.png)


Since this version is also vulnerable to CSRF, normal users can elevate their privileges to PRTG Administrators, by tricking Admin




### Tested on  20.1.55.1775+ and 21.2.68.1492+   

![uasi_version](https://user-images.githubusercontent.com/36541248/122043872-e6051200-cdec-11eb-812e-70b27e31319d.png)


![image](https://user-images.githubusercontent.com/36541248/122044072-22d10900-cded-11eb-90cd-35d72a25bd6e.png)

