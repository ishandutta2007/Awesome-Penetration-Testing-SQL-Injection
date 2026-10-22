# Awesome-Penetration-Testing-SQL-Injection

## Top Penetration Testing & SQL Injection Tools Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on SQL Injection Detection, DAST Coverage & Authorized Exploitation*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Penetration Testing & SQL Injection**. These tools help security professionals discover injection flaws, enumerate database structures, and validate exploitability — from automated DAST scanners that crawl modern web apps to specialized SQL injection engines that dump tables once a flaw is confirmed.

**Examples** include sqlmap, OWASP ZAP, Burp Suite, Acunetix, Invicti, and Arachni (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, SQL injection automation, and transparent scanning logic — ideal for penetration testers who need reproducible exploits, security engineers auditing their own applications, and teams running DAST in CI without per-target licensing.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Acunetix](https://www.acunetix.com/)**  
  **The highest-accuracy SQL injection scanner in independent academic testing** — achieved **86.96% accuracy, 94.74% precision, and 90% recall** on the Test PHP benchmark application, outperforming Burp Suite (52.17% accuracy) and Invicti (47.83%) . **On the Bricks application, Acunetix maintained 90.48% accuracy** with 100% precision . Commercial licensing; pricing by target count and scan frequency.

- **[Invicti](https://www.invicti.com/)**  
  **Commercial DAST platform with strong proof-based scanning** — achieved **100% precision across both Bricks and Test PHP applications** in independent testing, though recall was lower (85.71% and 40% respectively) . **Best for teams wanting confirmed vulnerabilities with minimal false positives** rather than exhaustive detection.

- **[Burp Suite Professional](https://portswigger.net/burp)**  
  **The industry-standard manual testing toolkit with integrated scanner** — achieved **52.17% accuracy and 45% recall** on Test PHP in the SQLi-ScanEval framework, with **100% precision** (no false positives) . **In API security benchmarking, Burp Suite achieved the highest detection rate (90%) but with high false positives (F1 = 0.53)** . **Best for manual testers** who value deep request manipulation over automated coverage.

## Open-Source GitHub Projects

- **[sqlmap](https://github.com/sqlmapproject/sqlmap)**  
  **The reference open-source SQL injection engine** — GPL-2.0 licensed. **Automates detection and exploitation of SQL injection flaws** with a powerful detection engine, database fingerprinting, data fetching, file system access, and OS command execution via out-of-band connections . **Supported DBMS**: MySQL, PostgreSQL, Microsoft SQL Server, Oracle, Microsoft Access, IBM DB2, SQLite, Firebird, and more . **Core workflow**: `sqlmap -u "URL" --dbs` to enumerate databases, `-D dbname --tables` for tables, `-D dbname -T users --columns` for columns, and `-D dbname -T users --dump` to extract data . **Works from Burp Suite captured requests**: save the request to a file and use `sqlmap -r request.txt` . **Best for any authorized SQL injection assessment** — the standard tool that every other SQLi tool is compared against.

- **[OWASP ZAP](https://github.com/zaproxy/zaproxy)**  
  **The most widely used open-source DAST scanner** — Apache 2.0 licensed. **Runs as an intercepting proxy for manual testing and as an automated scanner for CI** . **Baseline scan designed for fast pipeline execution** against a target URL, with API and Docker image for straightforward automation . **In independent academic testing, ZAP achieved a 75% true positive rate (TPR) with a Youden's Index of 0.625** on OWASP Top 10 vulnerabilities . **Completed fuzzing in an average of 4.72 seconds** versus Burp Suite Community's 22.56 seconds — significantly faster due to no free-tier throttling . **In API security benchmarking, ZAP achieved the highest severity-weighted Coverage Score (0.70)** against OWASP API Security Top 10 (2023) . **Best for teams wanting free, serious DAST coverage** with CI integration.

- **[sqleech](https://github.com/0x6d61/sqleech)**  
  **A next-generation SQL injection testing tool written in Go** — MIT licensed, **claiming 10-100x faster scanning than traditional tools** via goroutine-based concurrent worker pools . **Zero dependencies** — single binary deployment with no runtime required . **Multiple techniques**: error-based, Boolean-blind, time-blind, UNION-based, and stacked queries . **DBMS support**: MySQL, PostgreSQL, MSSQL, Oracle, SQLite . **Modern target support**: GraphQL, JSON body, and REST API parameter injection . **WAF bypass** with 20+ evasion modules, **CI/CD ready** with JSON and SARIF output, **session resume** for interrupted scans, and **library mode** for use in custom Go tools . **Best for teams wanting faster SQLi scanning** with modern target support and DevSecOps integration.

- **[ending (cfreal)](https://github.com/cyrus-and/ending)**  
  **A flexible SQL injection framework for complex targets** — Python-based, v0.4.0 . **Designed for cases where sqlmap runs out of options** — when you hit a WAF, a non-standard protocol, or a complex request flow that requires custom scripting . **Targets defined as Python design files** rather than CLI arguments, enabling authentication handling, custom headers, non-HTTP protocols, and WAF bypass logic in code . **AST-based SQL generation** — injection techniques implemented generically, with each DBMS translating the AST to its dialect . **Advanced bypass capabilities**: rewrite AST nodes to eliminate bad characters (e.g., `a<b` as `a BETWEEN 0 AND b`) or obfuscate function calls (`SUBSTR# comment\n(a,b)`) in a few lines of code . **Supported databases**: MySQL, PostgreSQL, SQLite, Oracle, MSSQL . **Best for complex SQLi cases** where sqlmap's built-in options are insufficient and you need programmatic control.

- **[Nuclei](https://github.com/projectdiscovery/nuclei)**  
  **Fast, template-driven vulnerability scanner** — MIT licensed. **Community-maintained template library** for specific known vulnerabilities and misconfigurations . **Excellent for scanning many hosts for known issues** quickly . **Less of a deep crawler than ZAP** — best used alongside it rather than as a replacement . **Best for broad reconnaissance** across large target sets.

- **[Nikto](https://github.com/sullo/nikto)**  
  **Older but still useful web server scanner** — GPL licensed. **Checks for dangerous files, outdated server software, and common misconfigurations** . **Noisy and not a full application scanner**, but quick for a first pass on a server . **Best for fast server-level reconnaissance.**

- **[Wapiti](https://github.com/wapiti-scanner/wapiti)**  
  **Lightweight open-source DAST crawler** — GPL-2.0 licensed. **In independent SQLi testing, Wapiti showed consistent precision rates across applications** . **Less actively developed than ZAP**, but useful for smaller targets . **Best for lightweight automated scanning** where ZAP is overkill.

- **[Arachni](https://github.com/Arachni/arachni)**  
  **Open-source DAST scanner with consistent SQLi detection** — in independent testing, **Arachni showed reliable and consistent recall rates across both Bricks and Test PHP applications**, making it a trustworthy option for SQLi vulnerability identification . **Best for teams wanting a capable open-source alternative** to commercial scanners.

### Additional Strong Open-Source Options

- **Bug Hunter CLI** — Autonomous agentic SAST/DAST scanner built on LangGraph. Orchestrates AI agents for static and dynamic testing with near-zero false-positive validation over the network. Stack-agnostic (Python, Node.js, Java, Go, Ruby, PHP) .
- **UltraDAST** — Comprehensive Python DAST tool with automated scanner, Burp-style proxy, and GUI. Focuses on business logic flaws, race conditions, and modern API testing (GraphQL, gRPC, WebSockets) .
- **WebVigil** — Python DAST scanner that proves vulnerabilities with bounded markers rather than dumping databases. Includes SARIF output for CI and a FastAPI web service .
- **Nuclei Templates** — The template repository powering Nuclei's vulnerability checks.

**Frameworks for building custom systems**: Combine **sqlmap** for comprehensive SQL injection detection and exploitation with full database enumeration, **OWASP ZAP** for fast automated DAST in CI with proxy-based manual testing, **sqleech** for faster modern-target SQLi scanning with SARIF output, **ending** for complex SQLi cases requiring programmatic control, and **Nuclei** for template-driven reconnaissance across large target sets — to build a penetration testing stack tailored to your testing depth, target complexity, and CI integration needs.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- **Penetration testing and SQL injection tools must only be used against systems you own or have explicit written authorization to test.** Unauthorized access to computer systems is illegal and unethical. **sqlmap's documentation and community consistently emphasize authorization as the first step** before any testing . **Acunetix achieved the highest SQLi accuracy (86.96%) in independent academic testing**, while **Burp Suite had the highest precision (100%) but lower recall** — no single tool detects everything . **OWASP ZAP is the most capable free DAST option** for both manual proxy testing and automated CI scanning . **sqleech claims 10-100x speedup** over traditional tools via Go concurrency, but real-world performance depends on target responsiveness and scan configuration . **ending is designed for complex cases** where sqlmap runs out of options, requiring Python scripting rather than CLI flags .
- Self-hosted open-source solutions require proper authorization verification, scope documentation, and test artifact cleanup after engagement.

---

**Made for penetration testers, security engineers, and teams conducting authorized vulnerability assessments.**
Let's make penetration testing and SQL injection detection more open, accurate, and authorized.
