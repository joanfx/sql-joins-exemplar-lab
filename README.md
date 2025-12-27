# Relational Data Correlation & Asset Auditing (SQL)

### Technical Objective: Correlating Disparate Datasets for Incident Response  

---

## Scenario
As a security analyst, I was tasked with performing a comprehensive audit of the organization's assets and user access logs. By utilizing INNER, LEFT, and RIGHT JOINS, I correlated employee data with machine assignments to identify critical security gaps, such as unregistered devices and hardware not currently assigned to authorized personnel.

For this exercise, I used different types of joins (`INNER`, `LEFT`, and `RIGHT`) to reveal both matching and non-matching data across tables.

---

## Task 1: Verifying Authorized Asset Assignments
**Goal:** Display all employees matched with the machines they use.  
**Fix:** Used an `INNER JOIN` to retrieve rows that exist in both the `employees` and `machines` tables.

**Command:**
```sql
SELECT *
FROM machines
INNER JOIN employees ON machines.device_id = employees.device_id;
```

---

## Task 2: Identifying Unassigned/Rogue Machines
**Goal:** Display all machines, even those not currently assigned to an employee.  
**Fix:** Used a `LEFT JOIN` so all machines appear, regardless of whether they match a record in `employees`.

**Command:**
```sql
SELECT *
FROM machines
LEFT JOIN employees ON machines.device_id = employees.device_id;
```

---

## Task 3: Auditing Employees Without Provisioned Hardware
**Goal:** Retrieve employees who don’t currently have assigned machines.  
**Fix:** Used a `RIGHT JOIN` so all employees are included, even those without a corresponding record in `machines`.

**Command:**
```sql
SELECT *
FROM machines
RIGHT JOIN employees ON machines.device_id = employees.device_id;
```

---

## Task 4: Correlating User Identities with Login Events
**Goal:** Combine the `employees` table with `log_in_attempts` to correlate users with their login data.  
**Fix:** Used an `INNER JOIN` on the `username` field.

**Command:**
```sql
SELECT *
FROM employees
INNER JOIN log_in_attempts ON employees.username = log_in_attempts.username;
```

---

## Key Takeaways
Through this lab, I practiced using **SQL joins** to correlate information across multiple datasets.  
This skill helps analysts detect inconsistencies or anomalies, such as:
- Employees using unregistered devices
- Machines not tied to any user
- Login attempts from unexpected accounts

**Operators used:**
- `INNER JOIN` → Returns only matched records  
- `LEFT JOIN` → Returns all from left table + matched from right  
- `RIGHT JOIN` → Returns all from right table + matched from left  

---

## What I Learned
- How to merge datasets efficiently for cybersecurity analysis  
- How different join types impact investigation results  
- Why joins are vital in identifying correlations between systems and users

---

**Author:** Joan

---
