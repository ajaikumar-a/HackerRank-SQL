# New Companies

Amber's conglomerate corporation just acquired some new companies. Each of the companies follows this hierarchy: 

Given the table schemas below, write a query to print the company_code, founder name, total number of lead managers, total number of senior managers, total number of managers, and total number of employees. Order your output by ascending company_code.

## Solution:

```
SELECT
  c.company_code,
  c.founder,
  COUNT(DISTINCT(l.lead_manager_code)) AS lead_managers,
  COUNT(DISTINCT(s.senior_manager_code)) AS senior_managers,
  COUNT(DISTINCT(m.manager_code)) AS managers,
  COUNT(DISTINCT(e.employee_code)) AS employees
FROM
  Company c
  JOIN Lead_Manager l ON c.company_code = l.company_code
  JOIN Senior_Manager s ON s.lead_manager_code = l.lead_manager_code
  JOIN Manager m ON m.senior_manager_code = s.senior_manager_code
  JOIN Employee e ON e.manager_code = m.manager_code
GROUP BY
  c.company_code, 
  c.founder
ORDER BY
  c.company_code;
  ```


