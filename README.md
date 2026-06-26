# OWASP Top 10: 2025

---

# A01: Broken Access Control

## Description

Broken Access Control occurs when an application fails to properly enforce restrictions on what authenticated or unauthenticated users are allowed to access or perform.

This includes:

* Vertical privilege escalation
* Horizontal privilege escalation
* Insecure Direct Object References (IDOR)
* Forced browsing
* Privilege abuse
* Access control bypass

## Common Causes

* Missing authorization checks
* Insecure API endpoints
* Predictable object identifiers
* Improper role validation
* Client-side access control
* Default administrative accounts

## Real-World Impact

Attackers may gain access to:

* Other users' accounts
* Sensitive files
* Administrative functions
* Financial records
* Customer information
* Internal application resources

## Example

A normal user changes:

```
/user/profile?id=1001
```

to

```
/user/profile?id=1002
```

and successfully views another user's information.

## Case Study

Numerous applications have suffered **IDOR** vulnerabilities where attackers accessed confidential user data simply by modifying object identifiers in URLs without proper authorization checks.

## Prevention and Mitigation

* Enforce server-side authorization
* Implement Role-Based Access Control (RBAC)
* Deny access by default
* Validate every request
* Use indirect object references
* Log unauthorized access attempts
* Perform regular access control testing

---

# A02: Security Misconfiguration

## Description

Security Misconfiguration occurs when security settings are improperly configured, left at default values, or unnecessary services and features remain enabled.

This includes:

* Default credentials
* Debug mode enabled
* Directory listing
* Excessive error messages
* Open cloud storage
* Unnecessary services

## Common Causes

* Default configurations
* Missing security hardening
* Improper permissions
* Misconfigured HTTP headers
* Outdated server configurations
* Forgotten development settings

## Real-World Impact

Attackers may obtain:

* Server information
* Configuration files
* Database credentials
* Internal paths
* Administrative access
* Sensitive application data

## Example

A production web server displays detailed stack traces whenever an application error occurs.

## Case Study

Numerous cloud storage buckets were left publicly accessible, exposing millions of sensitive customer records due to incorrect permission settings.

## Prevention and Mitigation

* Remove default accounts
* Disable unnecessary services
* Hide detailed error messages
* Configure secure HTTP headers
* Apply security hardening guides
* Regularly review configurations
* Automate configuration management

---

# A03: Software Supply Chain Failures

## Description

Software Supply Chain Failures occur when attackers compromise software through third-party libraries, dependencies, package managers, CI/CD pipelines, or build systems.

This includes:

* Vulnerable dependencies
* Malicious packages
* Compromised CI/CD pipelines
* Dependency confusion
* Typosquatting
* Build server compromise

## Common Causes

* Outdated dependencies
* Blind trust in third-party packages
* No integrity verification
* Insecure CI/CD pipelines
* Missing dependency scanning
* Poor package management

## Real-World Impact

Attackers may:

* Execute malicious code
* Compromise software updates
* Steal sensitive data
* Infect customer systems
* Gain persistent access

## Example

A developer accidentally installs a malicious package from a public repository that has the same name as an internal package.

## Case Study

The **SolarWinds** supply chain attack compromised software updates, affecting thousands of organizations worldwide.

## Prevention and Mitigation

* Scan dependencies regularly
* Verify package integrity
* Use trusted repositories
* Secure CI/CD pipelines
* Implement Software Bill of Materials (SBOM)
* Monitor third-party components
* Digitally sign software releases

---

# A04: Cryptographic Failures

## Description

Cryptographic Failures occur when sensitive information is not properly protected using encryption.

This includes:

* Weak encryption algorithms
* Improper password storage
* Insecure data transmission
* Poor key management
* Missing encryption

## Common Causes

* Weak cryptographic algorithms
* Plaintext password storage
* Weak TLS configuration
* Hardcoded encryption keys
* Missing HTTPS

## Real-World Impact

Attackers may steal:

* Passwords
* Credit card details
* Personal information
* Medical records
* Financial data

## Example

A website sends login credentials over HTTP instead of HTTPS.

## Case Study

Large breaches exposed millions of user passwords because applications stored passwords using weak hashing algorithms such as MD5 and SHA-1.

## Prevention and Mitigation

* Use HTTPS everywhere
* Use TLS 1.2/1.3
* Store passwords using Argon2 or bcrypt
* Secure encryption keys
* Encrypt sensitive stored data
* Disable outdated SSL/TLS versions
* Use trusted cryptographic libraries

---

# A05: Injection

## Description

Injection vulnerabilities occur when untrusted input is interpreted as commands or queries by an interpreter.

This includes:

* SQL Injection
* Command Injection
* NoSQL Injection
* LDAP Injection
* XPath Injection
* Template Injection

## Common Causes

* Unsanitized input
* Dynamic query construction
* Missing parameterized queries
* Poor input validation
* Unsafe system command execution

## Real-World Impact

Attackers may:

* Read databases
* Modify records
* Delete data
* Execute operating system commands
* Gain server access

## Example

```
' OR '1'='1
```

bypasses authentication in a vulnerable SQL query.

## Case Study

Many major breaches resulted from SQL Injection vulnerabilities exposing millions of customer records.

## Prevention and Mitigation

* Use parameterized queries
* Validate input
* Escape user input where necessary
* Avoid dynamic SQL
* Apply least privilege
* Use ORM frameworks
* Perform security testing

---

# A06: Insecure Design

## Description

Insecure Design represents security weaknesses introduced during the application's design phase rather than implementation.

This includes:

* Missing security controls
* Poor threat modeling
* Insecure workflows
* Lack of business logic validation
* Missing rate limiting

## Common Causes

* No secure SDLC
* Missing threat modeling
* Weak architecture
* Business logic flaws
* Lack of security requirements

## Real-World Impact

Attackers may:

* Abuse business logic
* Bypass workflows
* Commit fraud
* Escalate privileges
* Cause financial loss

## Example

A banking application allows unlimited money transfer attempts without fraud detection.

## Case Study

Many financial fraud incidents occurred because applications lacked proper abuse prevention despite having technically secure code.

## Prevention and Mitigation

* Adopt Secure SDLC
* Perform threat modeling
* Apply secure design principles
* Validate business logic
* Implement abuse prevention
* Conduct security architecture reviews

---

# A07: Authentication Failures

## Description

Authentication Failures occur when authentication mechanisms are improperly implemented.

This includes:

* Weak passwords
* Session fixation
* Credential stuffing
* Weak MFA
* Session hijacking

## Common Causes

* Weak password policies
* Predictable session IDs
* Missing MFA
* Poor session management
* Unlimited login attempts

## Real-World Impact

Attackers may:

* Hijack accounts
* Access sensitive information
* Perform unauthorized actions
* Impersonate users

## Example

An application allows unlimited password attempts without account lockout.

## Case Study

Credential stuffing attacks have compromised millions of user accounts using previously leaked passwords.

## Prevention and Mitigation

* Require MFA
* Enforce strong passwords
* Rate-limit login attempts
* Secure session management
* Rotate session identifiers
* Detect credential stuffing

---

# A08: Software or Data Integrity Failures

## Description

Software or Data Integrity Failures occur when software or critical data cannot be trusted due to missing integrity verification.

This includes:

* Insecure deserialization
* Unsigned updates
* Tampered data
* Missing integrity validation
* CI/CD manipulation

## Common Causes

* Unsigned software
* Missing integrity checks
* Insecure deserialization
* Weak update mechanisms
* Insecure deployment

## Real-World Impact

Attackers may:

* Execute malicious code
* Modify application behavior
* Deploy malware
* Compromise production systems

## Example

A software updater installs packages without verifying digital signatures.

## Case Study

Several malware campaigns distributed malicious software updates due to missing signature verification.

## Prevention and Mitigation

* Verify digital signatures
* Validate update integrity
* Secure deployment pipelines
* Avoid insecure deserialization
* Monitor software integrity
* Secure CI/CD systems

---

# A09: Security Logging and Alerting Failures

## Description

Security Logging and Alerting Failures occur when security events are not properly logged, monitored, or acted upon.

This includes:

* Missing audit logs
* Poor monitoring
* Missing alerts
* Log tampering
* Insufficient incident detection

## Common Causes

* Logging disabled
* Short log retention
* Missing alert rules
* Poor monitoring
* Unprotected logs

## Real-World Impact

Attackers may:

* Remain undetected
* Delete evidence
* Persist in systems
* Increase breach duration

## Example

Repeated failed login attempts are never logged or alerted.

## Case Study

Several major breaches remained undetected for months because organizations lacked effective monitoring and alerting.

## Prevention and Mitigation

* Log all security events
* Protect log integrity
* Configure SIEM alerts
* Monitor suspicious activity
* Review logs regularly
* Maintain incident response procedures

---

# A10: Mishandling of Exceptional Conditions

## Description

Mishandling of Exceptional Conditions occurs when applications fail to safely handle unexpected situations, errors, resource exhaustion, or abnormal operating conditions.

This includes:

* Unhandled exceptions
* Fail-open behavior
* Resource exhaustion
* Race conditions
* Infinite loops
* Poor error recovery

## Common Causes

* Missing exception handling
* Lack of input validation
* No timeout mechanisms
* Poor resource management
* Unsafe default behavior

## Real-World Impact

Attackers may:

* Crash applications
* Cause denial of service
* Bypass security controls
* Corrupt data
* Exhaust system resources

## Example

A malformed request causes an application to crash because the exception is never handled.

## Case Study

Numerous denial-of-service vulnerabilities have resulted from applications exhausting memory or CPU resources due to improper exception handling.

## Prevention and Mitigation

* Handle exceptions securely
* Fail securely (Fail Closed)
* Implement resource limits
* Use timeouts
* Validate all inputs
* Monitor application health
* Test abnormal scenarios regularly

---

## References

* OWASP Top 10: 2025
* OWASP Web Security Testing Guide (WSTG)
* OWASP Cheat Sheet Series
* CWE Top 25
* NIST Secure Software Development Framework (SSDF)
