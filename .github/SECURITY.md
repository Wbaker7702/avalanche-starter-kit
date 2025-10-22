# Security Policy

We take the security of this project seriously. Thank you for responsibly disclosing vulnerabilities.

## Supported Versions

We provide security fixes for:
- Main branch
- Latest tagged release

Older releases are best-effort only. For deployed contracts, we prioritize the most recent deployments on Avalanche C-Chain and our published Subnets.

## How to Report a Vulnerability

- Preferred: Open a private advisory via GitHub “Report a vulnerability” (Repository → Security → Advisories).
- Alternative: Email `security@YOURDOMAIN` with the subject “Vulnerability Report: REPO_NAME”.

Please include:
- Affected component(s): `contracts/**`, `web-apps/**`, deployment addresses, chain/network (e.g., C‑Chain, Subnet, Fuji)
- Impact and severity (what can an attacker do?)
- Steps to reproduce and a minimal PoC
- For contracts: target commit hash, `forge` test or script demonstrating the issue
- For web: affected routes, request/response samples, screenshots, console/network traces
- Your contact and public key (if encryption is required)

We will acknowledge within 3 business days.

## Coordinated Disclosure

- Do not file public issues or post publicly.
- We will work with you on a fix and coordinated release.
- You may request credit; we will attribute valid reports after remediation unless you prefer to remain anonymous.

## Scope

In scope:
- Smart contracts under `contracts/**` (including interchain messaging, token transfer, ERC721 bridge)
- Frontend under `web-apps/**` (Next.js), including client-side logic interacting with chains
- Build and deployment scripts that materially affect security of the above

Out of scope (unless leading to a concrete exploit):
- Social engineering, phishing, physical attacks
- Rate-limiting, DoS by volumetric traffic, and non-exploitable gas griefing
- Best-practice recommendations without a specific vulnerability
- Issues in 3rd‑party dependencies without a working exploit against this project
- Test or dev configurations not used in production

## Severity and Target Timelines

We follow CVSS v3.1 as guidance and align with contract risk profiles:

- Critical (fund loss, permanent lock, arbitrary mint/burn, cross‑chain message forgery, admin bypass): hotfix and advisory ASAP, target within 7 days
- High (theft with constraints, severe DoS of critical flows, reentrancy with bounded impact): fix within 30 days
- Medium (logic errors, privilege edge cases, price/MEV risks with mitigations): fix within 60 days
- Low (informational, minor UX, low‑impact misconfig): fix within 90 days or next planned release

We will keep you informed if timelines must shift (e.g., coordinated on‑chain upgrades).

## Safe Harbor

We will not pursue legal action against good‑faith research conducted under this policy:
- Avoid privacy violations, data exfiltration, and service degradation
- Only test on accounts and assets you own or have explicit permission to use
- Stop testing and report immediately upon discovering a vulnerability
- Do not access or modify data without authorization
- Follow applicable laws and do not violate third‑party rights

## Guidance for Reproducible Reports

Contracts (Foundry):
- Provide a `forge test` or reproduction script
- Specify compiler version, optimizer settings, and commit SHA
- Include deployment parameters, target network IDs, and relevant addresses
- Example: `forge test -vvv` output highlighting failing PoC

Web (Next.js):
- Include precise route(s), payload(s), and expected vs. actual behavior
- Note browser version, OS, and any extensions affecting the test
- For XSS/CSRF/redirects: provide payload and origin/headers details

## Examples of High‑Value Vulnerabilities

Smart contracts:
- Reentrancy, missing access control, unchecked external calls
- Signature malleability or replay across domains
- Cross‑chain message spoofing/forgery, incorrect message verification
- Integer over/underflows (where not safely handled), precision/accounting bugs
- Frontrunning/MEV enabling theft or invariant breakage
- DoS of critical lifecycle functions (e.g., upgrades, withdrawals)

Web:
- XSS, CSRF, SSRF, open redirect, authZ bypass, insecure origin checks
- Leaking private keys/secrets in client, build, or logs

## Security Practices We Follow

- Use of audited libraries (e.g., OpenZeppelin) and least‑privilege access controls
- Mandatory code review for changes under `contracts/**` and critical `web-apps/**` flows
- Static analysis and property‑based testing for contracts (Foundry); e2e tests for web
- Dependency update monitoring and pinned versions for critical components
- Principle of minimal trust across chains and explicit domain separation

## Bug Bounties

We may provide discretionary rewards for impactful, in‑scope vulnerabilities. If you operate a program (e.g., Immunefi), link it here. Otherwise: no guaranteed monetary bounty, but public credit is offered upon request after remediation.

## Security Advisories and Updates

- We publish advisories through GitHub Security Advisories and release notes
- Critical fixes may include mitigations or on‑chain upgrade guides
- Users should track releases and advisories and update promptly

## Contact

- Security: `security@YOURDOMAIN`
- Emergency/expedite: include “URGENT” in the subject
- Optional PGP: publish and link your key here

Thank you for helping keep the ecosystem safe.
