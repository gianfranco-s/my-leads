# lead-thread

This is a project to generate sales leads for three very different domains.
We're at the planning stage yet. No code to be implemented. I'm not even sure we'll ever write code.


## Project Outline

1. Define tools within the Claude ecosystem
2. A way to search for leads. Maybe a prompt for each domain. Domains are: software engineering (devops, automation, agents), job search (for a specific human), donations for building a school (donations coming from Argentina, US, EU)
3. A way to save those leads. Maybe a CSV or a google sheets. This may require research into MCP
4. A way to contact those leads. This entails doing some legwork on their painpoints, and an adequate entrypoint.
5. A way to perform followups and verify conversion rates

Things to consider:
* this is not a full automation. I still want to be directed to specific insights
* I'm looking to get into sales, and want to be AI-assisted
* first tangible objective is to generate 2 valid leads for each field

## Current state
- LinkedIn MCP server is configured and active (Docker, stdio transport)
- Project is structured by domain under `domains/`
- A prompt template exists at `domains/_template.md` for authoring new prompts

## Domain structure
```
domains/
  my-awesome-domain-name/
    prompt.md         ← search directive for this domain
    leads.csv         ← summary of all leads found
    rejected.csv      ← candidates checked and discarded (do not re-evaluate)
    leads-research/   ← one detail file per lead
    background/       ← source documents for this domain (business plan, resume, brief, etc.)
```

IMPORTANT: `background/` directory should only be used to improve the prompt. Only read if user asks explicitly, or `prompt.md` is empty.

---

## Search Execution Guidelines

These rules apply whenever executing any search prompt in this project.

**Tools available**
- **WebSearch (Google)** — for companies that publicly discuss their problems (news, job boards, industry directories)
- **LinkedIn MCP** — for direct discovery of founders, CTOs, or ops leads, especially companies with little or no web presence (common with Argentine PyMEs)

Use both tools. There is no fixed sequence — choose based on where the signal is likely to be found.

**Rate limiting**
- Wait a **random interval between 8 and 25 seconds** between LinkedIn MCP calls — fixed intervals are a bot fingerprint and increase detection risk
- If a rate limit error is returned, wait a random interval between 25 and 45 seconds before retrying once. If it fails again, skip and move on
- Do not make more than 10 LinkedIn MCP calls per run

**Search discipline**
- Before profiling any candidate, check `rejected.csv` — skip any company already listed there
- Evaluate and shortlist after each tool phase — do not pull full profiles for every result
- Pull `get_company_profile` only for companies that match at least 2 entry signals
- Pull `get_person_profile` only for companies already shortlisted

**Stop conditions**
- Stop when 5 qualified candidates are found, or all search queries are exhausted
- A candidate is "qualified" if it has: a company name, a fit signal, an estimated size, and at least one named contact

**Output discipline**
- Do not write to leads.csv until all searches are complete
- Write all candidates in a single pass — do not append incrementally
- Flag candidates with missing fields rather than omitting them
- At the end of every search run, append all discarded candidates to `rejected.csv` with columns: `company,url,reason,date_checked`
  - Valid reasons: `competitor`, `too large`, `wrong sector`, `already funded/has tech team`, `no decision-maker`, `insufficient signals`
