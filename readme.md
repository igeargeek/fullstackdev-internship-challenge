IGEARGEEK : Vending Machine Problem 
===

Follow this condition
- Unlimited products. 
- Unlimited changes. 
- Allow insert 1 baht, 2 baht, 5 baht and 10 baht coin only. 
- API calling to get product listing. 
- Design User Interface of vending machine based on good user experience. 
- We focus on good code quality. (Bonus point)
  - Readability, consistency — how easy it is to read and understand sections of the code; this includes code clarity, simplicity, and documentation.
  - Predictability, reliability, and robustness — software behavior should be predictable, and not prone to hidden bugs.
  - Maintainability and extensibility — fixing, updating and improving software should be as simple as possible, not inherently complex.
  Ref: https://medium.com/@mkt_43322/why-is-code-quality-such-a-big-deal-for-developers-91bdace85d44
- You can add more cool features. (Bonus point)

**Example**  

|   | Story | Insert | Total | Selected | Got item? | Change |
|---|-------|------------------|------------|-----------|----------|------------|
| 1 |User insert 10 baht and 5 baht coins and select Pepsi Max|10, 5|15|Pepsi Max|true|-|
| 2 |User insert 10 baht, 5 baht, 2 baht and 1 baht coins and select Pepsi Max|10, 5, 2, 1|18|Pepsi Max|true|2, 1|
| 3 |User insert 10 baht, 2 baht coins and select Pepsi Max but can't select because not enough money|10, 2|12|Pepsi Max|false|-|
| 4 |User insert 10 baht, 2 baht baht coins and select Coke Vanilla (S) but can't selected because product not available in machine|10, 2|12|Coke Vanilla (S)|false|-|
| 6 |User insert 10 baht, 10 baht, 2 baht coin but need refund|10, 10, 2|22|-|false|10, 10, 2|


Product listing
---

| API | Endpoint | Method |
|-----|----------|--------|
|Product listing|http://www.mocky.io/v2/5af11f8c3100004d0096c7ed|GET|

Acceptance Agreement
---

1. Fork github project to your account
2. Move your code to `exercise` folder

Have any question?
---
Open Issue for question or any suggestion from this link below

https://github.com/nitipatl/problem-vending-machine/issues
