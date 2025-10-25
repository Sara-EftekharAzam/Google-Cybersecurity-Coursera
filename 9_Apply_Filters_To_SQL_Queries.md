# **Apply Filters to SQL Queries**

## **Project Description**

In this project, I used SQL to investigate potential security issues related to login attempts and employee information. By applying filters with the `AND`, `OR`, and `NOT` operators, as well as the `LIKE` keyword, I identified suspicious login activities and extracted specific employee data from the organization’s database. This activity demonstrates my ability to use SQL queries to filter, investigate, and analyze cybersecurity-related datasets.

---

## **Retrieve After Hours Failed Login Attempts**

**Query:**

```sql
SELECT event_id, username, login_date, login_time, country, ip_address, success
FROM log_in_attempts
WHERE login_time > '18:00:00'
AND success = FALSE;
```

**Explanation:**
This query retrieves all failed login attempts that occurred **after 18:00 (6 PM)**.

* The condition `login_time > '18:00:00'` filters for login events after business hours.
* The condition `success = FALSE` (or equivalently `success = 0`) filters for failed login attempts.
  By combining both conditions with `AND`, the query identifies unsuccessful login events that happened after work hours, which may indicate suspicious activity.

---

## **Retrieve Login Attempts on Specific Dates**

**Query:**

```sql
SELECT event_id, username, login_date, login_time, country, ip_address, success
FROM log_in_attempts
WHERE login_date = '2022-05-09'
OR login_date = '2022-05-08';
```

**Explanation:**
This query retrieves all login attempts that occurred on **May 8 or May 9, 2022**, when a suspicious event was reported.

* The condition `login_date = '2022-05-09'` filters for logins on May 9.
* The condition `OR login_date = '2022-05-08'` includes logins from the day before.
  The `OR` operator ensures both dates are included in the investigation results.

---

## **Retrieve Login Attempts Outside of Mexico**

**Query:**

```sql
SELECT event_id, username, login_date, login_time, country, ip_address, success
FROM log_in_attempts
WHERE country NOT LIKE '%MEX%';
```

**Explanation:**
This query identifies login attempts that occurred **outside of Mexico**.

* The `LIKE '%MEX%'` condition matches both “MEX” and “MEXICO”.
* The `NOT` operator excludes all entries that match that pattern.
  This filter helps isolate login activity from other countries, which could indicate remote or unauthorized access attempts.

---

## **Retrieve Employees in Marketing**

**Query:**

```sql
SELECT employee_id, device_id, username, department, office
FROM employees
WHERE department = 'Marketing'
AND office LIKE 'East%';
```

**Explanation:**
This query retrieves information about employees in the **Marketing department** who are located in the **East building**.

* The `department = 'Marketing'` condition filters for Marketing staff.
* The `office LIKE 'East%'` condition finds all offices that begin with “East”, such as *East-170* or *East-320*.
  The `AND` operator ensures only Marketing employees located in the East offices are returned.

---

## **Retrieve Employees in Finance or Sales**

**Query:**

```sql
SELECT employee_id, device_id, username, department, office
FROM employees
WHERE department = 'Finance'
OR department = 'Sales';
```

**Explanation:**
This query retrieves all employees who work in the **Finance** or **Sales** departments.

* The `OR` operator is used because the result should include employees from either department.
  This data helps the security team schedule department-specific security updates for those groups.

---

## **Retrieve All Employees Not in IT**

**Query:**

```sql
SELECT employee_id, device_id, username, department, office
FROM employees
WHERE department <> 'Information Technology';
```

**Explanation:**
This query identifies all employees who are **not in the IT department**.

* The condition `department <> 'Information Technology'` excludes IT employees.
* The `<>` operator is the SQL “not equal to” comparison operator.
  This query helps target machines for software updates that were already completed by the IT department.

---

## **Summary**

Through this activity, I used SQL queries to filter and analyze data related to login attempts and employee records. I applied logical operators such as `AND`, `OR`, and `NOT` to narrow down results and used `LIKE` for pattern matching. These queries allowed me to identify failed logins after hours, suspicious activities by date and country, and specific employee groups for system updates. This demonstrates how SQL can be effectively used to support cybersecurity investigations and operational decision-making.
