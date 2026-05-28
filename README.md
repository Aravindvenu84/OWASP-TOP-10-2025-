# OWASP Top 10 (2025) 
## Introduction

The OWASP Top 10 is a globally recognized security awareness document published by OWASP (Open Worldwide Application Security Project). It lists the most critical web application security risks based on real-world attack data, security research, and industry experience.

The OWASP Top 10 helps:
- Developers build secure applications
- Security teams identify vulnerabilities
- Organizations improve cybersecurity practices
- Students learn modern web security concepts

---

# A01: Broken Access Control

## Description
Broken Access Control occurs when users can access resources, data, or functions beyond their intended permissions.

Access control ensures:
- Users only access their own data
- Regular users cannot access admin functions
- Sensitive operations require proper authorization

When these controls fail, attackers can bypass restrictions.

---

## Common Causes
- Missing authorization checks
- Predictable URLs or IDs
- Improper role validation
- Insecure API endpoints
- Forced browsing

---

## Real-World Impact
Attackers may:
- View private user information
- Modify or delete data
- Access administrator features
- Take over accounts
- Escalate privileges

---

## Example

A user changes:

```bash
/user/profile/101
```

to:

```bash
/user/profile/102
```

and gains access to another user's account.

---

## Prevention
- Implement role-based access control (RBAC)
- Deny access by default
- Validate permissions server-side
- Use secure session management
- Perform authorization checks for every request

---

# A02: Cryptographic Failures

## Description
Cryptographic Failures happen when sensitive data is not properly protected using encryption.

This includes:
- Weak encryption algorithms
- Plaintext password storage
- Improper HTTPS usage
- Weak key management

---

## Common Causes
- Using outdated cryptography
- Storing passwords without hashing
- Weak SSL/TLS configurations
- Exposed encryption keys

---

## Real-World Impact
Attackers may steal:
- Passwords
- Credit card information
- Personal data
- Medical records
- Financial information

---

## Example

A website sends login credentials over HTTP instead of HTTPS.

---

## Prevention
- Use HTTPS everywhere
- Use strong encryption standards
- Store passwords using bcrypt or Argon2
- Secure encryption keys properly
- Disable outdated SSL/TLS versions

---

# A03: Injection

## Description
Injection vulnerabilities occur when untrusted user input is interpreted as commands or queries.

Types include:
- SQL Injection
- NoSQL Injection
- Command Injection
- LDAP Injection

---

## Common Causes
- Unsanitized user input
- Dynamic query construction
- Lack of parameterized queries

---

## Real-World Impact
Attackers can:
- Read databases
- Delete records
- Execute system commands
- Bypass authentication

---

## Example

SQL Injection:

```sql
SELECT * FROM users WHERE username = 'admin' OR '1'='1';
```

---

## Prevention
- Use prepared statements
- Validate and sanitize inputs
- Use ORM frameworks safely
- Apply least privilege to databases

---

# A04: Insecure Design

## Description
Insecure Design refers to security weaknesses caused by poor application architecture or missing security controls during development.

This is not a coding bug but a design problem.

---

## Common Causes
- Lack of threat modeling
- Missing rate limiting
- Poor authentication flow
- No security planning

---

## Real-World Impact
Applications become vulnerable even if the code itself is technically correct.

Attackers may exploit:
- Weak business logic
- Poor workflows
- Missing protections

---

## Example

A banking application allows unlimited password reset attempts without account lockout.

---

## Prevention
- Apply secure software development lifecycle (SSDLC)
- Perform threat modeling
- Use secure design patterns
- Implement rate limiting
- Conduct security reviews during design phase

---

# A05: Security Misconfiguration

## Description
Security Misconfiguration occurs when systems, servers, cloud services, or applications are configured insecurely.

---

## Common Causes
- Default credentials
- Open cloud storage
- Unnecessary services enabled
- Debug mode left active
- Improper permissions

---

## Real-World Impact
Attackers may:
- Gain unauthorized access
- Discover sensitive files
- Exploit exposed services
- Gather system information

---

## Example

An admin dashboard is publicly accessible using:

```text
admin/admin
```

---

## Prevention
- Remove default accounts
- Disable unnecessary services
- Use hardened configurations
- Keep environments properly separated
- Continuously audit configurations

---

# A06: Vulnerable and Outdated Components

## Description
Applications often rely on third-party libraries, frameworks, and software packages. If these components contain known vulnerabilities, attackers can exploit them.

---

## Common Causes
- Old dependencies
- Unsupported software versions
- Unpatched vulnerabilities
- Unknown component inventory

---

## Real-World Impact
Attackers may:
- Execute remote code
- Gain server access
- Steal data
- Crash systems

---

## Example

Using a vulnerable version of Apache Log4j affected by Log4Shell.

---

## Prevention
- Regularly update dependencies
- Remove unused libraries
- Use vulnerability scanners
- Monitor security advisories
- Maintain software inventory

---

# A07: Identification and Authentication Failures

## Description
This risk involves weak authentication or session management mechanisms.

Authentication verifies user identity.

---

## Common Causes
- Weak passwords
- No multi-factor authentication (MFA)
- Insecure session IDs
- Poor password reset mechanisms

---

## Real-World Impact
Attackers may:
- Hijack user accounts
- Perform credential stuffing
- Bypass login systems
- Steal sessions

---

## Example

Common weak passwords:

```text
123456
password
admin
```

---

## Prevention
- Enforce strong passwords
- Enable MFA
- Secure session management
- Limit failed login attempts
- Use secure authentication protocols

---

# A08: Software and Data Integrity Failures

## Description
Software and Data Integrity Failures happen when applications trust software updates, plugins, libraries, or CI/CD pipelines without verification.

---

## Common Causes
- Insecure software updates
- Compromised CI/CD pipelines
- Unsigned code
- Untrusted dependencies

---

## Real-World Impact
Attackers may:
- Inject malicious code
- Distribute malware
- Compromise software supply chains

---

## Example

Installing a modified package from an untrusted repository.

---

## Prevention
- Verify digital signatures
- Secure CI/CD pipelines
- Use trusted repositories
- Monitor software integrity
- Apply dependency verification

---

# A09: Security Logging and Monitoring Failures

## Description
Applications that fail to log, monitor, and detect suspicious activity cannot properly respond to attacks.

---

## Common Causes
- Missing security logs
- Poor monitoring systems
- No alerting mechanisms
- Incomplete audit trails

---

## Real-World Impact
Attackers may remain undetected for long periods.

Organizations may:
- Miss active attacks
- Fail incident response
- Lose forensic evidence

---

## Example

Multiple failed login attempts occur without triggering alerts.

---

## Prevention
- Enable centralized logging
- Monitor suspicious activity
- Create security alerts
- Retain audit logs securely
- Use SIEM solutions

---

# A10: Server-Side Request Forgery (SSRF)

## Description
SSRF occurs when an attacker tricks a server into making requests to unintended locations.

The server becomes a proxy for the attacker.

---

## Common Causes
- User-controlled URLs
- Improper input validation
- Open internal network access

---

## Real-World Impact
Attackers may:
- Access internal systems
- Scan private networks
- Retrieve cloud metadata
- Bypass firewalls

---

## Example

A vulnerable server processes:

```text
http://localhost/admin
```

allowing access to internal services.

---

## Prevention
- Validate and sanitize URLs
- Block internal IP ranges
- Use allowlists
- Disable unnecessary outbound requests
- Segment internal networks

---

# Conclusion

The OWASP Top 10 represents the most important web application security risks developers and organizations should understand.

Modern applications face increasing threats due to:
- Cloud computing
- APIs
- Containers
- Microservices
- CI/CD pipelines
- Supply chain attacks

Understanding these vulnerabilities helps developers:
- Build secure systems
- Reduce attack surfaces
- Protect sensitive data
- Improve cybersecurity awareness

Security should be integrated into every stage of software development rather than treated as an afterthought.

---

# References

- https://owasp.org/www-project-top-ten/
- https://owasp.org/
- https://cheatsheetseries.owasp.org/
