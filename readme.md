IGEARGEEK : Vending Machine Problem 
===

Develop vending machine follow this condition
- Unlimited products
- Unlimited money changes
- Allow only 1 baht, 2 baht, 5 baht and 10 baht coins
- Call API for product detail from balow table

**Example**  

|  | Story | Insert | Total | Selected | Got item | Change|
|---|-------|------------------|------------|-----------|----------|------------|
| 1 |User insert 10 baht and 5 baht coins and select Pepsi Max|10, 5|15|Pepsi Max|true|-|
| 2 |User insert 10 baht, 5 baht, 2 baht and 1 baht coins and select Pepsi Max|10, 5, 2, 1|18|Pepsi Max|true|2, 1|
| 3 |User insert 10 baht, 2 baht coins and select Pepsi Max but can't select because not enough money|10, 2|12|Pepsi Max|false|-|
| 4 |User insert 10 baht, 2 baht baht coins and select Coke Vanilla (S) but can't selected because product not available in machine|10, 2|12|Coke Vanilla (S)|false|-|
| 6 |User insert 10 baht, 10 baht, 2 baht coin but need refund|10, 10, 2|22|-|false|10, 10, 2|


Product information
---

| API | Endpoint | Method |
|-----|----------|--------|
|Drinking list|http://www.mocky.io/v2/5af11f8c3100004d0096c7ed|GET|

Acceptance Agreement
---
1. Fork github project to your repository
2. Move source code to folder `exercise`

Question ๆ 
---
Open Issue for ask question or any suggestion from link below. 

https://github.com/nitipatl/problem-vending-machine/issues
