# Introduction

## Mitigating Web Application Security Risks: Addressing Broken Access Controls and Authentication Failures

When building a website or application for customers, adopting a security-first mindset is essential. However, this can be challenging during development due to short development cycles, frequent updates, and the rapid evolution of technology. Security must remain a priority throughout the agile development process, as bad actors constantly seek to exploit vulnerabilities. These threats can result in data theft, misuse of systems, or disruptions to organizational operations.

As websites and applications grow increasingly interactive and complex, security can sometimes take a back seat, leading to a variety of risks. As cybersecurity analysts, we must address not only the obvious threats but also ensure that access controls are well-defined, user rights are properly assigned, and regular audits are conducted. Additionally, user identification and non-repudiation processes must be clearly defined and implemented.

In this analysis, I will explore key risks such as broken access controls and identification and authentication failures. I will define each risk, provide real-world examples, and suggest proactive controls based on guidance from the Open Web Application Security Project (OWASP). OWASP is a respected organization that researches and publishes known security threats to web applications, offering actionable guidance to developers and cybersecurity professionals to promote secure development practices.

---

## Risk One: Broken Access Control

- **Max Occurrence Rate:** 55.97%  
- **Average Incident Rate:** 3.81%  
- **Total Resulting Occurrences:** 318,487  
- **Common Vulnerabilities Identified:** 19,013  

### **Description of the Risk**

Broken access control occurs when attackers manipulate a web application or system to exceed their authorized permissions. This can lead to privilege escalation, where a malicious actor elevates their access from a standard user to an administrator or root user. Such control allows attackers to modify or steal sensitive information, resulting in data breaches, financial losses, and legal ramifications.

### **Example**

An attacker exploiting broken access controls might gain access to a web server and upgrade their user account permissions from "read-only" to "root" access. This elevated access could allow them to inject malicious code into the site, potentially stealing sensitive customer and employee information. Additionally, they might use this access to create a spoofed website to deceive users into providing credentials, credit card details, or other personally identifiable information (PII).

### **Proactive Controls**

#### **Deny by Default**

- Configure systems to deny access by default unless explicitly permitted. This approach ensures that access decisions are deliberate and reduces the likelihood of errors.  
- Begin with a straightforward access control policy and enhance it over time.  
- Regularly review change logs and policies to keep up with evolving frameworks.  
- Customize default configurations and implement robust logging mechanisms to monitor access activities. *(OWASP Top 10: 2021, 2021)*  

#### **Prefer Attribute-Based and Relationship-Based Access Control Over RBAC**

- **Role-Based Access Control (RBAC)** assigns permissions based on roles, but it can become unwieldy when users hold multiple roles. 

- **Attribute-Based Access Control (ABAC)** simplifies management by assigning permissions based on predefined attributes (e.g., job function or department). 

- ABAC enables automated enforcement of policies and makes it easier to manage group memberships and revoke permissions as needed. *(OWASP Top 10: 2021, 2021)*  

---

## Risk Two: Identification and Authentication Failures

- **Max Occurrence Rate:** 14.84%  
- **Average Incident Rate:** 2.55%  
- **Total Resulting Occurrences:** 132,195  
- **Common Vulnerabilities Identified:** 3,897  

### **Description of the Risk**

This risk arises when an application fails to implement robust identity, authentication, and session management protocols. Without proper authentication policies, attackers can execute automated attacks to guess username/password combinations, commonly known as brute-force attacks.

### **Example**

An application lacking a lockout policy or multi-factor authentication (MFA) becomes vulnerable to brute-force attacks using tools like **Hashcat** or **John the Ripper**. Once attackers gain access, they can impersonate legitimate users and potentially steal sensitive data.

### **Proactive Controls**

#### **Multi-Factor Authentication (MFA)**

- Enforce MFA to add an additional layer of security.  
- Validate password strength by comparing inputs against a list of commonly used passwords.  

#### **Account Lockout

Policies** *(Price, 2024)*

- **Account Lockout Duration:** Specify how long an account remains locked after failed attempts.  
- **Lockout Threshold:** Set a limit on failed login attempts before locking the account.  
- **Reset Counter:** Define the time interval to reset failed login attempts.  

#### **Session Management**

- Use frameworks like **PHP, .NET, or J2EE**, which offer robust, pre-built session management systems that are regularly updated to address vulnerabilities.  
- Encrypt session ID exchanges using **TLS** to prevent interception.  
- Implement **secure cookies and session expiration** to protect sensitive user data.  

---

## Conclusion

The risks of broken access controls and identification and authentication failures highlight the importance of implementing robust security measures in web development. By following proactive controls such as **denying access by default**, **preferring ABAC over RBAC**, **enforcing MFA**, and **securing session management**, organizations can significantly reduce the likelihood of exploitation. OWASP's guidelines provide a reliable foundation for identifying vulnerabilities and fostering a security-first mindset in development processes.

---

## Bibliography

- OWASP Top 10: 2021. (2021). Retrieved from **[A01:2021 – Broken Access Control](https://owasp.org/Top10/A01_2021-Broken_Access_Control/)**  
- Price, M. H. (2024). *Web Application Security*. In *Internet and Web Application Security* (p. 171). Burlington: Jones and Bartlett Learning.  
