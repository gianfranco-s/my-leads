# Search Prompt — Job Search Leads

## Candidate Profile
**Name:** Gianfranco Salomone
**Title:** Python Developer / Backend AI Engineer
**Seniority:** Senior
**Location:** Río Negro, Argentina — open to remote
**Languages:** Spanish (native), English (C2)

**Core strengths:**
- Python backend (FastAPI, Flask, Django)
- DevOps & cloud (AWS, Docker, Terraform, Ansible, CI/CD)
- AI/ML integration (LLMs, RAG, OpenAI, Ollama)
- Team lead experience (code review, mentoring, advocating best practices)
- Worked for US-based companies

---

## Prompt

Search for hiring managers, engineering leads, or recruiters at companies that are **actively hiring** for roles matching this profile:

- **Role titles:** Backend Engineer, Python Developer, Backend AI Engineer, MLOps Engineer, DevOps Engineer, Cloud Engineer, AI/ML Engineer
- **Seniority:** Senior or above
- **Work model:** Remote open to international contractors (LATAM / Argentina) — **discard any role that says "Remote - US only" or requires US work authorization**
- **Company type:** Tech startups, scale-ups, or established tech companies — especially those with Python or AI/ML in their stack

**Where to search:**
- LinkedIn: search the role titles above, filter by "remote", sort by recent postings
- LinkedIn: look for recruiters who specialize in backend/Python/DevOps roles and are active (recent posts)
- Twitter/X: search "hiring senior python" OR "hiring backend engineer remote"
- Wellfound (AngelList): filter by role + remote + Python/AI stack
- We Work Remotely / Remote OK: check active Python/backend/DevOps listings

**Also search EPIC iO competitors directly.**
EPIC iO (epicio.com) is an AIoT operational intelligence platform: edge computing, video management (DeepVision), connectivity (WirelessWindow), and industrial AI analytics (DeepInsights). They serve construction, energy, utilities, government, and manufacturing. Their LinkedIn page was not resolvable — search by website or name.

Confirmed competitors to target first:
- **Samsara** — strongest match; IoT operations platform, multiple confirmed remote Python roles (Growth, Connectivity, External Platform). Connectivity role is the sharpest fit given EPIC iO's device/connectivity work. Recruiter on record: Michelle Smiley (linkedin.com/in/michelle-smiley-36513b48).
- **Augury** — machine health AI for manufacturing; Python/Kafka/K8s/Airflow/MLOps stack. Open Backend Developer role as of March 2026. Remote status and contacts not yet confirmed.
- **Cognite** — industrial AI (Atlas AI platform); Python, LLMs, RAG, Kubernetes. Open Senior Backend role as of March 2026. Listed as Phoenix, AZ — verify if remote option exists before pursuing.

Additional companies worth checking (not yet verified for open roles): Sight Machine, C3.ai, Uptake, Rhombus Systems, Vantiq, Litmus Automation.

Gianfranco has hands-on domain experience in this vertical — lead with that when assessing fit. Prioritize companies that are hiring remotely and have a Python or AI backend.

**Prioritize companies that mention:**
- Python, FastAPI, or Flask in their stack
- AWS or cloud-native infrastructure
- AI, LLMs, or automation work
- Small-to-mid engineering teams (signal: the hire matters more)

**For each prospect, capture:**
- Company name + job post URL
- Hiring manager or recruiter name + LinkedIn
- Role title and key requirements
- Why it's a strong fit for Gianfranco
- Remote policy — explicitly note whether the role is open to international contractors or restricted to US residents

---

## Output files

**Summary CSV:** append each candidate as a row to `domains/job/leads.csv`

Columns: `id,company,sector,size,contact_name,contact_role,contact_linkedin,job_post_url,role_title,remote_policy,confidence,date_found,status,status_description,detail_file`

- `id`: sequential, prefix `JOB-` (e.g. `JOB-001`)
- `remote_policy`: one of `international ok`, `US only`, `unknown — verify`
- `confidence`: `High`, `Medium`, or `Low`
- `status`: `new`, `incomplete`, or `rejected`
- `status_description`: leave blank if status is `new`; explain the gap or rejection reason otherwise

**Detail files:** one markdown file per candidate in `domains/job/leads-research/`, named `JOB-NNN-company-slug.md`

Each detail file should follow this structure:
```
# JOB-NNN — Company Name

| Field | Value |
|---|---|
| **Company** | |
| **Website** | |
| **Sector** | |
| **Size** | |
| **Role** | |
| **Job post URL** | |
| **Remote policy** | |
| **Fit signal** | |

## Contact

| Field | Value |
|---|---|
| **Name** | |
| **Role** | |
| **LinkedIn** | |

## Outreach History

_No outreach yet._

## Research Notes
```
