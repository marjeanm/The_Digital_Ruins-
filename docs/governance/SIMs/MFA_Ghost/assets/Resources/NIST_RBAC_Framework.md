
# NIST Role-Based Access Control (RBAC) Framework

This framework outlines RBAC structures aligned with NIST SP 800-53 and SP 800-171 standards, tailored to support secure identity and access management.

## 🎯 Objectives
- Enforce least privilege access
- Align roles to job functions
- Simplify policy application and auditing

---

## 🧱 RBAC Layers

### 1. **Role Assignment**
Users must be assigned to roles based on organizational function, not individual preference.

### 2. **Permission Assignment**
Roles must map to explicit permissions across cloud apps, file systems, and platforms.

### 3. **Session Activation**
Access only during defined sessions, enforced via Conditional Access.

---

## 🔐 Example Roles

| Role Name         | Description                        | Permissions Summary |
|------------------|------------------------------------|---------------------|
| `User.Basic`     | Default user access                | Email, SharePoint   |
| `User.HR`        | Access to HRIS + sensitive data    | HR tools, eDocs     |
| `IT.Helpdesk`    | Tier 1 IT support permissions       | Password reset, VDI |
| `Security.Admin` | Admin rights for identity & audit  | CA, audit logs      |
| `Executive`      | Protected role, high-risk control  | Conditional access, Teams |

---

## 🔎 Auditing & Monitoring
- Log role assignments in audit logs
- Review assignments quarterly
- Tie to privileged identity management (PIM)
