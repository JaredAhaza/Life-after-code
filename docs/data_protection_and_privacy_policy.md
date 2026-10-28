# Data Protection and Privacy Policy: CodeRescue
## Post-Code DevSecOps Platform

**Effective Date:** Hackathon Release v1.0  
**Scope:** CodeRescue Web Application, MCP Server, and GitLab Integration Services  

---

## 1. Core Data Privacy Commitments

CodeRescue is engineered under the principle of **Zero-Storage for Proprietary Source Code**:
1. **Transient Analysis**: Source code snippets retrieved for defect remediation are processed in volatile memory and are **never** persisted to databases or long-term disk storage.
2. **Metadata-Only Persistence**: Only deterministic findings metadata, policy rules, verification test metrics (pass/fail counts), and audit logs are retained.
3. **No Secondary Model Training**: Data processed by CodeRescue and delegated to GitLab Duo is never used to train third-party foundation models.

---

## 2. Information Collected & Processing Grounds

| Category | Specific Elements | Purpose | Retention Period |
| :--- | :--- | :--- | :--- |
| **User Identity** | GitLab username, email, user ID | Authentication & session integrity | Retained until session logout / account deletion |
| **Repository Metadata** | Project name, commit SHA, branch name, language | Scope determination & context mapping | Retained in project workspace cache |
| **CI/CD Evidence** | Pipeline status, test execution results, SAST/DAST findings summary | Verification audit trail & release gating | Stored for duration of repository tracking |
| **Audit Events** | Action name, actor, timestamp, outcome | Compliance, accountability, and governance | 90-day rolling log |

---

## 3. Data Flow & Boundary Security

```
[Developer Browser] 
       │ (HTTPS / TLS 1.3)
       ▼
[CodeRescue Control Center (GCP)] 
       │ 
       ├── (Zero-disk ephemeral buffer)
       │
       ▼ (Encrypted JSON-RPC / REST)
[GitLab Duo Agent Platform / GitLab API]
       │
       ▼ (Direct execution on GitLab Runner)
[Repository Artifacts & CI/CD Pipelines]
```

---

## 4. User Rights & Data Deletion

- **Instant Disconnect**: Users can revoke GitLab access with a single click. Revocation immediately invalidates active tokens.
- **Cache Purge**: Users can trigger an instant purge of all cached findings, test reports, and policy profiles associated with their repository.
