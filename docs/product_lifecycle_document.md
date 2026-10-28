# Product Lifecycle Document: CodeRescue
## Comprehensive 9-Stage DevSecOps Lifecycle & Autonomy Matrix

**Document Version:** 1.0  
**Focus:** GitLab Transcend Hackathon — Prize for Most Stages Covered  
**Autonomy Modes:** Assisted | Supervised | Hands-Off  

---

## 1. DevSecOps 9-Stage Architecture Mapping

CodeRescue provides active automation across **every single stage** of the GitLab DevSecOps lifecycle:

```mermaid
journey
    title CodeRescue Post-Code Lifecycle Progression
    section 1. Plan
      Discover Repo & Metadata: 5: Developer, CodeRescue
      Triage Issues & Root Causes: 4: CodeRescue, Duo Agent
      Establish Policy Baseline: 5: Duo Agent, Developer
    section 2. Create
      Formulate Stabilization MR: 5: Duo Agent
      Inject Policy Standards: 4: CodeRescue MCP
    section 3. Verify
      Run Deterministic Unit Tests: 5: GitLab CI/CD Runner
      Validate Cross-Domain Fix: 4: CodeRescue Engine
    section 4. Package
      Build Container Image: 5: GitLab Container Registry
      Generate SBOM & Attestation: 5: GitLab CI
    section 5. Secure
      Run SAST & Secret Detection: 5: GitLab Security Suite
      Scan Dependencies & CVEs: 4: GitLab Security Suite
    section 6. Release
      Semantic Tagging & Changelog: 5: CodeRescue Automation
      Canary / Staged Deployment: 4: Google Cloud Run
    section 7. Configure
      Validate IaC & Environment: 4: GitLab CI / Terraform
      Inject Runtime Secrets: 5: Google Secret Manager
    section 8. Monitor
      Health Checks & Probes: 5: CodeRescue Health Monitor
      Automate Fast Rollback: 4: GitLab Auto DevOps
    section 9. Govern
      Audit Evidence & Traceability: 5: CodeRescue Audit Core
      Enforce Production Gates: 5: Policy Sign-Off Engine
```

### Detailed Breakdown of the 9 Stages

| # | Stage | GitLab Duo & CodeRescue Role | Verifiable Artifact Output |
| :---: | :--- | :--- | :--- |
| **1** | **Plan** | Ingests repository state; Duo proposes policy baseline & sequences stabilization tasks. | `policy-baseline.json`, prioritized remediation backlog. |
| **2** | **Create** | Duo generates remediation branch (`coderescue/*`) & patches conforming to policies. | Git Merge Request with explanatory rationale & diff. |
| **3** | **Verify** | Triggers CI automated unit, functional, and regression test suites. | JUnit XML test reports, coverage percentage report. |
| **4** | **Package** | Packages the verified application into an OCI container image. | OCI Container in GitLab Container Registry, CycloneDX SBOM. |
| **5** | **Secure** | Runs GitLab SAST, Secret Detection, Dependency Scanning, and Container Scanning. | `gl-sast-report.json`, `gl-secret-detection-report.json`. |
| **6** | **Release** | Tags release version, writes release notes, orchestrates deployment to staging/prod. | GitLab Release, deployed Cloud Run URL. |
| **7** | **Configure** | Validates cloud environment configurations, environment variables, and network ports. | Verified runtime environment configuration. |
| **8** | **Monitor** | Continuously pings `/healthz`, monitors error rates and latency regressions. | Live health status dashboard, alert thresholds. |
| **9** | **Govern** | Gathers cryptographic commit SHA, pipeline IDs, policy compliance sign-off. | Immutable Compliance & Release Readiness Certificate. |

---

## 2. Autonomy Operating Matrix

Users can toggle their preferred autonomy level at any time in CodeRescue:

### 2.1 Mode 1: Assisted (Human-in-the-Loop)
- **Workflow**: Duo identifies defect ➔ proposes fix ➔ displays visual diff to user ➔ awaits manual click "Approve & Run CI" ➔ awaits approval before merge ➔ awaits approval before release.
- **Ideal For**: Sensitive enterprise codebases, novice developers wanting line-by-line review.

### 2.2 Mode 2: Supervised (Milestone Gating)
- **Workflow**: Developer triggers "Stabilize Repository" ➔ Duo creates MR, runs tests, fixes linter and CVE failures autonomously ➔ pauses at Staging gate ➔ Developer reviews summary report and clicks "Promote to Production".
- **Ideal For**: Fast-paced teams wanting automated post-code hygiene with final release veto power.

### 2.3 Mode 3: Hands-off (Autonomous Closed-Loop)
- **Workflow**: New issue or failing commit pushed ➔ Duo triages, repairs defect, verifies pipeline passes, security scan is clean, auto-merges, and deploys to Google Cloud Run ➔ Posts executive summary to GitLab Issue. Zero human clicks needed.
- **Ideal For**: Nightly maintenance, dependabot remediation, post-code automated hardening.

---

## 3. Two Personas Experience Flow

### Persona A: Advanced Developer
- Fast-track direct access: Jumps immediately into the **Release Gate Matrix**.
- Direct policy editing (YAML/JSON).
- Can override individual checks or run multi-repo batch verifications.

### Persona B: Guided Beginner
- Warm educational onboarding with simplified health gauge (0-100%).
- Plain-English breakdown: *"We detected that your API returns unencrypted passwords. Here is why that's dangerous, and how Duo fixed it."*
- Interactive "Fix It with GitLab Duo" guided wizard.
