# kev-test-fixture
 
An intentionally vulnerable `package.json` for testing whether a dependency/SCA scanner (such as the Osprey CLI) detects npm packages tied to CVEs in the [CISA Known Exploited Vulnerabilities (KEV) catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog).
 
> **Warning:** This repo exists only for scanner testing. Never deploy it, never run it as a real application, and never copy these dependency versions into production code.
 
## What's inside
 
The fixture pins versions affected by **CVE-2025-55182 ("React2Shell")**, a pre-authentication remote code execution flaw in React Server Components (CVSS 10.0, listed in CISA KEV).
 
| Package | Pinned version | Fixed in |
|---|---|---|
| `next` | 15.5.6 | 15.5.7 |
| `react` | 19.2.0 | n/a (the flaw is in the server DOM packages) |
| `react-dom` | 19.2.0 | n/a |
| `react-server-dom-webpack` | 19.2.0 | 19.2.1 |
| `react-server-dom-turbopack` | 19.2.0 | 19.2.1 |
| `react-server-dom-parcel` | 19.2.0 | 19.2.1 |
 
There is no application code. The repo contains only a manifest (and optionally a lockfile) so the scanner has dependencies to analyze.
 
## Setup
 
```bash
git clone <this-repo-url>
cd kev-test-fixture
 
# Optional: generate a lockfile without installing anything
npm install --package-lock-only
```
 
Do **not** run `npm install` or start anything unless you specifically need `node_modules` for your scanner. Generating only the lockfile is enough for most SCA tools.
