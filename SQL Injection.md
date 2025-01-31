### SQL Injection: Overview and Implementation

**SQL Injection (SQLi)** is a common attack vector in which malicious SQL queries are injected into a web application’s input fields to manipulate or bypass the backend database. This can allow attackers to view, modify, or delete sensitive data, or even gain administrative access to the application.

### 1. **Types of SQL Injection Attacks**
There are several types of SQL injection attacks, including:

#### a. **Classic (In-band) SQL Injection**
This type occurs when the attacker can see the result of the injected query directly in the application's response.

- **Union-based SQLi**: Uses the `UNION` SQL operator to join malicious queries with legitimate ones.
- **Error-based SQLi**: Exploits error messages returned by the database to gather information.

#### b. **Blind SQL Injection**
This occurs when an application is vulnerable but doesn't directly show the result of the query. Attackers rely on the application's behavior to infer information.

- **Boolean-based blind SQLi**: The attacker sends queries that return true or false, and observes the application’s behavior to deduce data.
- **Time-based blind SQLi**: Delays are introduced in SQL queries to infer data based on the time taken for a response.

#### c. **Out-of-band SQL Injection**
The attacker triggers a query to send data to a remote server. This method is less common but can occur if an application allows DNS lookups or HTTP queries.

---

### 2. **SQL Injection Example: Vulnerability and Exploit**

#### **Vulnerable Scenario**
Suppose we have a basic login form that checks a username and password against a database:

```sql
SELECT * FROM users WHERE username = '$username' AND password = '$password';
```

Here, the variables `$username` and `$password` are taken directly from user input. If not properly sanitized, an attacker can inject SQL commands to manipulate this query.

#### **Basic SQL Injection Attack**
If the attacker inputs the following in the username field:

```sql
' OR '1'='1
```

And leaves the password field empty, the SQL query becomes:

```sql
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '';
```

Since `'1'='1'` is always true, this query will return all users in the database, potentially granting access without a valid username and password.

---

### 3. **SQL Injection Exploit: UNION-Based SQL Injection**

**Union-Based SQL Injection** allows an attacker to execute a second query and combine it with the original query's result. Here's an example:

#### Original Query:
```sql
SELECT name, email FROM users WHERE id = '$user_id';
```

If an attacker inputs the following payload for `$user_id`:

```sql
1 UNION SELECT username, password FROM admin;
```

The SQL query becomes:

```sql
SELECT name, email FROM users WHERE id = '1' UNION SELECT username, password FROM admin;
```

This query fetches data from the `admin` table and combines it with the result from the `users` table, potentially exposing sensitive admin credentials.

---

### 4. **Preventing SQL Injection**

To prevent SQL injection attacks, the following best practices are recommended:

#### a. **Parameterized Queries (Prepared Statements)**
The most effective way to prevent SQL injection is to use **parameterized queries** or **prepared statements**. These statements separate SQL code from data, ensuring that user input is treated strictly as data, not executable code.

##### Example in PHP (Using Prepared Statements with PDO):
```php
// Create a connection using PDO
$conn = new PDO('mysql:host=localhost;dbname=mydb', $username, $password);

// Prepare a SQL statement with placeholders
$stmt = $conn->prepare("SELECT * FROM users WHERE username = :username AND password = :password");

// Bind user input to the placeholders
$stmt->bindParam(':username', $username);
$stmt->bindParam(':password', $password);

// Execute the query
$stmt->execute();
```

In this example, the user input is bound to the placeholders `:username` and `:password`, ensuring that even if malicious SQL is injected, it won't be executed as part of the query.

#### b. **Stored Procedures**
Stored procedures can also reduce the risk of SQL injection by separating SQL logic from user input.

##### Example:
```sql
CREATE PROCEDURE GetUser(
    IN p_username VARCHAR(50),
    IN p_password VARCHAR(50)
)
BEGIN
    SELECT * FROM users WHERE username = p_username AND password = p_password;
END;
```

When user input is passed to the stored procedure, it does not alter the SQL logic itself.

#### c. **Input Validation and Sanitization**
While parameterized queries are the most effective, it's also important to validate and sanitize user inputs. For instance:
- **Whitelist Input**: Only allow expected characters (e.g., letters, numbers) and reject dangerous characters like quotes (`'`), semicolons (`;`), or hyphens (`--`).
- **Escaping Special Characters**: For older codebases that may not use parameterized queries, you can escape special characters to prevent SQL injection. However, this method is not as reliable as prepared statements.

#### d. **Least Privilege Database Permissions**
Ensure that your application's database account has the least amount of privilege necessary. For example, an application shouldn't use an account with admin privileges if it only needs to read data.

#### e. **Web Application Firewalls (WAFs)**
A WAF can help detect and block SQL injection attempts. It acts as a filter between users and the web application, analyzing incoming requests for malicious patterns.

---

### 5. **SQL Injection Attack Example: Implementation**

#### Vulnerable PHP Code Example:

```php
<?php
$connection = new mysqli('localhost', 'user', 'password', 'database');

// Retrieving user input (vulnerable to SQL Injection)
$username = $_POST['username'];
$password = $_POST['password'];

// SQL query with no parameterization (vulnerable)
$query = "SELECT * FROM users WHERE username = '$username' AND password = '$password'";

// Execute query
$result = $connection->query($query);

if ($result->num_rows > 0) {
    echo "Login Successful!";
} else {
    echo "Invalid Credentials!";
}
?>
```

**Attack Example**:

If an attacker inputs the following into the username field:
```sql
' OR '1'='1
```

The SQL query becomes:
```sql
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '';
```

This query will bypass authentication, and the attacker will be logged in.

#### Secured PHP Code Example:

```php
<?php
$connection = new mysqli('localhost', 'user', 'password', 'database');

// Prepare a statement to prevent SQL Injection
$stmt = $connection->prepare("SELECT * FROM users WHERE username = ? AND password = ?");
$stmt->bind_param("ss", $username, $password);

// Retrieve and bind user input
$username = $_POST['username'];
$password = $_POST['password'];

// Execute the statement
$stmt->execute();
$result = $stmt->get_result();

if ($result->num_rows > 0) {
    echo "Login Successful!";
} else {
    echo "Invalid Credentials!";
}
?>
```

In this secure version, prepared statements ensure that user input is treated as data, not part of the SQL query, effectively preventing SQL injection.

---
