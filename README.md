# Relational Data Correlation & Asset Auditing (SQL)

### Technical Objective: Correlating Disparate Datasets for Incident Response  

---

## Scenario:
As a security analyst, I was tasked with performing a comprehensive audit of the organization's assets and user access logs. By utilizing `INNER`, `LEFT`, and `RIGHT JOINS`, I correlated employee data with machine assignments to identify critical security gaps, such as unregistered devices and hardware not currently assigned to authorized personnel.

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

## What I Learned
- Cross-Platform Data Correlation: Used `INNER`, `LEFT`, and `RIGHT JOINS` to merge security datasets into a single, actionable investigative view.
  
- Asset Integrity Auditing: Developed a logical workflow for identifying "shadow IT" by isolating machines that lack valid employee assignments in the relational database.
  
- Identity Mapping: Successfully correlated user identities with login events to provide full-stack visibility into which specific personnel accessed hardware during incident windows.
  
- Gap Analysis: Leveraged specific join types to detect unprovisioned employees, ensuring that all active personnel are mapped to authorized organizational assets.

- Operational Forensics: Gained hands-on experience in how relational data structures serve as the backbone for incident response and hardware lifecycle management.

---

**Author:** Joan

---
