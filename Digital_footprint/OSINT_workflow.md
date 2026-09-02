1. Sherlock — my first choice

Sherlock is an open-source username enumeration tool that checks 400+ social networks for a username.

2. WhatsMyName

This is another very good option and is particularly useful because its underlying dataset contains 700+ websites.

You can enter:

prakash1807

3. WhatsMyName.io

This is a newer browser-based interface around public username searching. It currently advertises roughly 525 source definitions, with results linking to public pages for manual

4. Sherlock Search — photo-based search

This is different from the open-source Sherlock project.

It claims to search public profiles based on a photo, including Instagram, TikTok, Facebook, X, LinkedIn and other sources, and says it doesn't access private accounts.


# OSINT Investigation Workflow — Practical Notes

> A reusable, public-information-only workflow for discovering and verifying online profiles that may belong to the same person.
>
> **Example target:** Prakash Singh — works at TCS.
>
> Any extra details below such as usernames, LinkedIn URLs, emails, universities, or projects are **dummy examples** unless explicitly stated as known.

---

## 1. What is OSINT?

**OSINT = Open-Source Intelligence.**

It means collecting, organizing, and correlating information that is already publicly available.

Typical sources:
- Public social-media profiles
- Public GitHub repositories
- Public developer profiles
- Public websites and portfolios
- Search-engine results
- Publicly accessible documents

### Basic boundary

Use public information only.

Do **not**:
- bypass authentication
- access private accounts
- use password-reset tricks to discover accounts
- use leaked/private databases
- steal credentials
- circumvent privacy controls

---

# 2. Complete Workflow

```text
Define the question
        ↓
Collect known public information
        ↓
Extract identifiers
        ↓
Search engines
        ↓
Username enumeration
        ↓
Search specific platforms
        ↓
Collect candidate accounts
        ↓
Correlate independent evidence
        ↓
Eliminate false positives
        ↓
Pivot from strong profiles
        ↓
Document evidence
        ↓
Assign confidence
        ↓
Final report
```

---

# 3. Example Target

Assume the target is:

```text
Name:
Prakash Singh

Employer:
TCS / Tata Consultancy Services

Known:
- Works at TCS
- IT/developer background
- May have LinkedIn
- May have Instagram
- May have GitHub
- May have LeetCode/GFG/CodeChef/Codeforces accounts
```

### Dummy extra information

These are only examples:

```text
Dummy LinkedIn:
linkedin.com/in/prakash-singh-example

Dummy Instagram:
@prakash1807

Dummy email:
prakash.singh.demo@example.com
```

---

# 4. Step 1 — Define the Investigation Goal

Before searching, write exactly what you want to find.

### Example

```text
Target:
Prakash Singh

Goal:
Find publicly available developer/social profiles that may belong
to the same Prakash Singh who works at TCS.

Platforms:
- GitHub
- LeetCode
- GeeksforGeeks
- CodeChef
- Codeforces
- HackerRank
- Instagram
- X
- Reddit
- Personal website
```

### Tool

No special tool is needed.

Use:
- Notepad
- Obsidian
- Notion
- Google Docs

### Why?

It prevents random searching and keeps the investigation focused.

---

# 5. Step 2 — Create an Investigation Sheet

Create a structured table before searching.

| Category | Known information |
|---|---|
| Name | Prakash Singh |
| Employer | TCS |
| LinkedIn | linkedin.com/in/prakash-singh-example |
| Instagram | prakash1807 |
| Email | prakash.singh.demo@example.com |
| Education | Unknown |
| Location | Unknown |
| Developer profiles | Unknown |

### Recommended tools

**Google Sheets / Excel**
- Best for candidate tracking and evidence.

**Notion**
- Good for notes + tables + links.

**Obsidian**
- Good for larger investigations and linking notes.

---

# 6. Step 3 — Extract Searchable Identifiers

A name is usually a weak identifier.

Convert known information into searchable terms.

### Example

```text
Name:
Prakash Singh

Employer:
TCS
Tata Consultancy Services

Possible usernames:
prakash1807
prakash_singh
prakash.singh
prakashsingh
prakashsingh07
```

Use variations based on information you actually know. Avoid generating huge numbers of random guesses.

### Tool

No special OSINT tool.

Use your notes or spreadsheet.

---

# 7. Step 4 — Search Engines

Search engines are your first discovery tool.

### Tools

- Google
- Bing
- DuckDuckGo

### Basic searches

```text
"Prakash Singh" TCS
```

```text
"Prakash Singh" "Tata Consultancy Services"
```

```text
"Prakash Singh" GitHub
```

```text
"Prakash Singh" LeetCode
```

```text
"Prakash Singh" GeeksforGeeks
```

```text
"prakash1807"
```

### `site:` searches

```text
site:github.com "Prakash Singh" TCS
```

```text
site:leetcode.com "Prakash Singh"
```

```text
site:geeksforgeeks.org "Prakash Singh"
```

```text
site:codechef.com "Prakash Singh"
```

### What search engines do

They are **discovery tools**. They can surface:
- Public profiles
- Public repositories
- Public posts
- Portfolio pages
- Public documents
- Links between public profiles

A search result is a lead, not proof of identity.

---

# 8. Step 5 — Username Enumeration with Sherlock

## What Sherlock does

**Sherlock** is an open-source username-enumeration tool.

Conceptually:

```text
username
   ↓
GitHub?
Instagram?
Reddit?
Pinterest?
Twitch?
...
   ↓
possible accounts
```

Official project:

https://github.com/sherlock-project/sherlock

### Basic command

```bash
sherlock prakash1807
```

Multiple usernames:

```bash
sherlock prakash1807 prakash_singh prakashsingh
```

Save results:

```bash
sherlock prakash1807 --folderoutput sherlock_results
```

Show found accounts:

```bash
sherlock prakash1807 --print-found
```

Help:

```bash
sherlock --help
```

### Important limitation

If Sherlock finds:

```text
GitHub → github.com/prakash1807
```

it means:

> A public GitHub account using that username exists.

It does **not** automatically prove that the account belongs to the target.

---

# 9. Step 6 — WhatsMyName

**WhatsMyName** is another username-enumeration resource.

Website:

https://whatsmyname.app/

Search:

```text
prakash1807
```

and:

```text
prakash_singh
```

### Why use it?

Different tools can have different coverage.

A useful combination is:

```text
Search engines
+
Sherlock
+
WhatsMyName
```

No single tool should be treated as complete.

---

# 10. Step 7 — Search Specific Platforms

After discovering candidate usernames, search the platforms directly.

## GitHub

```text
site:github.com "Prakash Singh" TCS
```

```text
site:github.com "prakash1807"
```

```text
site:github.com "Prakash Singh" "Tata Consultancy Services"
```

### Inspect

- Public name
- Bio
- Company
- Location
- Website
- Public repositories
- README files
- Social links
- Publicly published email, if intentionally exposed

---

## LeetCode

```text
site:leetcode.com "Prakash Singh"
```

```text
site:leetcode.com "prakash1807"
```

Inspect public profile information and any public links.

---

## GeeksforGeeks

```text
site:geeksforgeeks.org "Prakash Singh"
```

```text
site:geeksforgeeks.org "prakash1807"
```

---

## CodeChef

```text
site:codechef.com "Prakash Singh"
```

```text
site:codechef.com "prakash1807"
```

---

## Codeforces

```text
site:codeforces.com "Prakash Singh"
```

```text
site:codeforces.com "prakash1807"
```

---

## HackerRank

```text
site:hackerrank.com "Prakash Singh"
```

```text
site:hackerrank.com "prakash1807"
```

### Why direct platform searches matter

The platform itself may expose additional context that a username-enumeration tool does not.

---

# 11. Step 8 — Collect Candidate Accounts

Do not immediately declare that every result belongs to the target.

Create a candidate table.

| Candidate | Platform | Username | Initial evidence | Status |
|---|---|---|---|---|
| A | GitHub | `prakash1807` | Username match | 🟡 |
| B | LeetCode | `prakash_singh` | Name match | 🟡 |
| C | GitHub | `psingh1998` | Different employer | ❌ |
| D | CodeChef | `prakash1807` | Username match | 🟡 |

### Status

- 🟡 Candidate — needs verification
- 🟢 Strong candidate
- ✅ Strongly corroborated
- ❌ Rejected

---

# 12. Step 9 — Correlate Independent Evidence

This is the most important step.

Suppose:

```text
GitHub:
username = prakash1807
name = Prakash Singh
```

That is only one signal.

Look for more.

## Signal 1 — Employer

Does the public profile mention:

```text
TCS
Tata Consultancy Services
```

?

## Signal 2 — Education

Does it mention the same university or degree?

## Signal 3 — Location

Does the public location reasonably match?

## Signal 4 — Cross-links

Does GitHub link to:
- LinkedIn
- Personal website
- X

?

## Signal 5 — Username reuse

For example:

```text
Instagram → prakash1807
GitHub    → prakash1807
```

Useful, but not proof alone.

## Signal 6 — Public projects

Look at:
- Repository descriptions
- README files
- College projects
- Portfolio projects
- Publicly linked websites

The goal is to find **independent signals that agree**.

---

# 13. Weak vs Strong Evidence

### Weak

```text
Same name
```

### Slightly stronger

```text
Same name
+
same username
```

### Stronger

```text
Same name
+
same username
+
same university
+
same employer
```

### Very strong

```text
Same name
+
same username
+
same university
+
same employer
+
explicit public cross-link between profiles
```

### Principle

> Independent corroboration is more valuable than repeated copies of the same information.

---

# 14. Step 10 — Eliminate False Positives

False positives are normal.

Example candidate:

```text
Name:
Prakash Singh

Employer:
Infosys

University:
ABC University
```

Target:

```text
Employer:
TCS
University:
XYZ University
```

Then:

```text
Name       ✅
Employer   ❌
University ❌
```

Conclusion:

```text
❌ Probably a different person
```

Do not force a candidate to fit the target.

---

# 15. Step 11 — Profile-to-Profile Pivoting

Once you find a strongly corroborated public profile, inspect its public links.

Example:

```text
LinkedIn
   ↓
GitHub
   ↓
Personal Website
   ↓
X / other public developer profile
```

If a GitHub profile publicly links to a personal website, open the website and inspect its public links.

### Why pivoting helps

You are following explicit public relationships rather than randomly searching the Internet.

---

# 16. Step 12 — Search Public Email References

Suppose an email is intentionally published on a public developer page:

```text
prakash.singh.demo@example.com
```

Search exact public references:

```text
"prakash.singh.demo@example.com"
```

You can also search a non-sensitive username fragment:

```text
"prakash.singh.demo"
```

### Boundary

Keep this limited to public references.

Do not use:
- Password-reset probing
- Account-recovery probing
- Credential dumps
- Leaked databases
- Private-data lookup services
- Attempts to bypass privacy controls

---

# 17. Step 13 — Search Username Variations

People often reuse usernames with small changes.

For:

```text
prakash1807
```

logical variants might include:

```text
prakash_1807
prakash.1807
prakash-1807
prakash1807
prakashsingh1807
prakash_singh
prakashsingh
psingh1807
```

Then test selected variants:

```bash
sherlock prakash1807 prakash_1807 prakashsingh1807 prakash_singh
```

Keep variations tied to known information.

---

# 18. Step 14 — Reverse Image Search (Optional)

If you have a **publicly visible profile picture**, reverse-image-search tools can sometimes find other public pages using the same image.

### Tools

- Google Lens
- Bing Visual Search
- TinEye

### Workflow

```text
Public profile image
        ↓
Reverse image search
        ↓
Potential public pages
        ↓
Check context
        ↓
Correlate with other evidence
```

### Caution

Image similarity alone is not definitive identity proof.

Use surrounding public evidence.

---

# 19. Step 15 — Search Public Projects

For developer profiles this can be useful.

Suppose:

```text
GitHub:
prakash1807
```

Inspect:

```text
Repositories
README files
Project names
Portfolio links
Public profile links
```

Then search distinctive project names:

```text
"Project Name" "Prakash Singh"
```

Possible chain:

```text
GitHub
   ↓
Project
   ↓
Portfolio
   ↓
LinkedIn
```

---

# 20. Step 16 — Build an Evidence Graph

For larger investigations, think in relationships.

```text
                       ┌───────────────┐
                       │ Prakash Singh │
                       └───────┬───────┘
                               │
             ┌─────────────────┼─────────────────┐
             ↓                 ↓                 ↓
         LinkedIn          Instagram           Email
             │                 │                 │
             ↓                 ↓                 ↓
            TCS          prakash1807      public references
             │
             ↓
          GitHub
             │
             ↓
       Personal Website
             │
             ↓
        LeetCode / GFG
```

Each arrow should represent some public evidence.

---

# 21. Step 17 — Maintain an Evidence Table

For each candidate, save:

| Field | Example |
|---|---|
| Platform | GitHub |
| Username | `prakash1807` |
| URL | Public profile URL |
| Name | Prakash Singh |
| Employer | TCS |
| University | Example University |
| Matching username | Instagram |
| Links to LinkedIn | Yes |
| Other evidence | Public portfolio |
| Confidence | High |
| Date checked | 2026-09-02 |

Record:
- URL
- What was publicly visible
- Date checked
- Why it matters
- Confidence
- Contradictory evidence

---

# 22. Step 18 — Confidence System

## 🔴 Unconfirmed

Only weak evidence:

```text
Same name
```

or:

```text
Same username
```

## 🟡 Possible

Several weak signals:

```text
Same name
+
same username
+
similar public location
```

## 🟢 Strong Candidate

Several independent signals:

```text
Same name
+
same username
+
same university
+
same employer
```

## 🟢🟢 Highly Corroborated

Example:

```text
GitHub
   ↓
public personal website
   ↓
same LinkedIn profile
```

or:

```text
GitHub
+
same employer
+
same university
+
same username
+
explicit public cross-link
```

---

# 23. Example: Verifying a Candidate

Suppose Sherlock gives:

```text
GitHub:
github.com/prakash1807
```

### Initial observation

```text
Username matches Instagram:
prakash1807
```

Confidence:

```text
🟡 Possible
```

Public GitHub profile shows:

```text
Name:
Prakash Singh

Company:
TCS

Location:
Bengaluru

Website:
example.com/prakash
```

Confidence becomes:

```text
🟢 Strong candidate
```

The website publicly links to:

```text
LinkedIn:
linkedin.com/in/prakash-singh-example
```

Now:

```text
🟢🟢 Highly corroborated
```

---

# 24. Example: Rejecting a Candidate

Suppose:

```text
github.com/prakash1807
```

contains:

```text
Name:
Prakash Singh

Company:
Infosys

University:
University ABC
```

but the target is known to work at TCS and attend University XYZ.

Then:

```text
Name              ✅
Username          ✅
Employer          ❌
University        ❌
```

Conclusion:

```text
❌ Probably a different person
```

---

# 25. Useful Search Operators

### Exact phrase

```text
"Prakash Singh"
```

### Specific website

```text
site:github.com "Prakash Singh"
```

### Multiple conditions

```text
"Prakash Singh" TCS GitHub
```

### Username

```text
"prakash1807"
```

### Exclude a result

```text
"Prakash Singh" GitHub -Infosys
```

Search-engine operator support can vary, so inspect results manually.

---

# 26. Recommended OSINT Toolkit

| Purpose | Tool | What it does |
|---|---|---|
| General discovery | Google / Bing / DuckDuckGo | Finds indexed public pages |
| Username enumeration | Sherlock | Checks many sites for a username |
| Username enumeration | WhatsMyName | Broad username discovery |
| GitHub investigation | GitHub | Public profile/repositories |
| Coding profiles | LeetCode / GFG / CodeChef / Codeforces | Developer-profile discovery |
| Image search | Google Lens / Bing Visual Search / TinEye | Finds public pages using similar images |
| Notes | Obsidian / Notion | Investigation notes |
| Evidence table | Excel / Google Sheets | Candidate tracking |
| Browser | Chrome / Firefox | Manual inspection |

---

# 27. Important Principle

Remember:

```text
DISCOVERY ≠ IDENTIFICATION
```

Finding:

```text
github.com/prakash1807
```

is **discovery**.

Determining:

```text
github.com/prakash1807
=
the Prakash Singh who works at TCS
```

requires **corroboration**.

---

# 28. End-to-End Checklist

```text
STEP 1
Define target:
Prakash Singh
TCS

        ↓

STEP 2
Collect known public information.

        ↓

STEP 3
Extract identifiers:

Prakash Singh
TCS
Tata Consultancy Services
prakash1807
prakash_singh
etc.

        ↓

STEP 4
Search engines:

"Prakash Singh" TCS
"Prakash Singh" GitHub
"Prakash Singh" LeetCode
"prakash1807"

        ↓

STEP 5
Sherlock:

sherlock prakash1807 prakash_singh

        ↓

STEP 6
WhatsMyName:

prakash1807
prakash_singh

        ↓

STEP 7
Search developer platforms.

GitHub
LeetCode
GFG
CodeChef
Codeforces
HackerRank

        ↓

STEP 8
Create candidate list.

        ↓

STEP 9
For every candidate check:

Name?
Employer?
University?
Location?
Username?
Website?
Cross-links?
Projects?

        ↓

STEP 10
Reject false positives.

        ↓

STEP 11
Pivot from strong profiles.

LinkedIn → GitHub → Website → other public profiles

        ↓

STEP 12
Document evidence.

        ↓

STEP 13
Assign confidence.

UNCONFIRMED
POSSIBLE
STRONG
HIGHLY CORROBORATED

        ↓

STEP 14
Final report.
```

---

# 29. Final Report Template

```text
# OSINT Investigation Report

## Target

Name:
Employer:
Known usernames:
Known public profiles:

## Objective

What am I trying to discover?

## Known Information

- ...
- ...
- ...

## Candidate Accounts

### Candidate 1

Platform:
Username:
URL:

Evidence:
- ...
- ...
- ...

Contradictory evidence:
- ...

Confidence:
LOW / MEDIUM / HIGH

## Strongly Corroborated

- ...

## Probably Different People

- ...

## Not Found

- GitHub
- LeetCode
- GFG
- CodeChef
- Codeforces
- HackerRank

## Notes

- ...
```

---

# 30. Ethics and Safety Checklist

```text
[✓] Public web pages
[✓] Public social profiles
[✓] Public GitHub repositories
[✓] Public developer profiles
[✓] Public search-engine results
[✓] Publicly linked accounts

[✗] Private accounts
[✗] Password-reset probing
[✗] Credential theft
[✗] Leaked/private databases
[✗] Bypassing authentication
[✗] Circumventing privacy controls
```

The goal is to organize and correlate information that is already public.

---

# 31. Quick Reference Card

```text
KNOWN DATA
   ↓
NAME / USERNAME / COMPANY / UNIVERSITY
   ↓
SEARCH ENGINES
   ↓
SHERLOCK + WHATSMYNAME
   ↓
PLATFORM-SPECIFIC SEARCH
   ↓
CANDIDATE ACCOUNTS
   ↓
CORRELATE:
NAME
EMPLOYER
EDUCATION
LOCATION
USERNAME
WEBSITE
CROSS-LINKS
PROJECTS
   ↓
REMOVE FALSE POSITIVES
   ↓
PIVOT THROUGH PUBLIC LINKS
   ↓
DOCUMENT EVIDENCE
   ↓
ASSIGN CONFIDENCE
   ↓
FINAL REPORT
```



---

# 32. Additional Tools Similar to Sherlock

Sherlock is excellent for username enumeration, but it is useful to have several tools because their site coverage and detection methods differ.

## 32.1 Maigret — The Closest Alternative to Sherlock

**Maigret** is a username OSINT tool and a fork of Sherlock. Its project currently documents support for **2,500+ sites**, with the default search using 500 popular sites. It can also parse profile pages, extract links and information, perform recursive username searches, and generate HTML/PDF reports. citeturn542405search1turn542405search8

### Install

```bash
pip3 install maigret
```

### Basic search

```bash
maigret prakash1807
```

### Search all available sites

```bash
maigret prakash1807 -a
```

### Search several usernames

```bash
maigret prakash1807 prakash_singh prakashsingh -a
```

### Generate reports

```bash
maigret prakash1807 -HP
```

### Search coding-related sites

```bash
maigret prakash1807 --tags coding
```

### Why use it?

```text
Sherlock
   +
Maigret
   ↓
Compare results
   ↓
Investigate candidates
```

**Best use:** broad username discovery and deeper profile parsing.

### Important

Maigret itself warns that large-scale site searches can produce false positives, so every hit still needs verification. citeturn542405search8

---

# 32.2 WhatsMyName — Large Username Dataset

**WhatsMyName (WMN)** is a community-maintained dataset for checking whether a username exists across hundreds of websites. Its current project documentation lists **700+ websites** and explains that the data powers several checkers and OSINT tools. citeturn653862search0turn653862search2

### Website

```text
https://whatsmyname.app/
```

### Example

Search:

```text
prakash1807
```

Then:

```text
prakash_singh
```

### Useful feature

The web interface can filter results by category and export results to CSV. citeturn653862search0

**Best use:** quick browser-based username discovery and cross-checking Sherlock/Maigret.

---

# 32.3 Blackbird — Fast Username Search

**Blackbird** is listed by the WhatsMyName project as a fast username-search tool that integrates the WhatsMyName dataset. citeturn653862search0

The useful idea is:

```text
Blackbird
   ↓
WhatsMyName dataset
   ↓
many public sites
```

**Best use:** another independent username-enumeration check.

Because projects and installation methods change over time, use the current project documentation/repository for installation instructions rather than copying an old command from a random tutorial.

---

# 32.4 Social Analyzer — Username + Name Analysis

**Social Analyzer** goes beyond simple exact username matching. Its current project describes it as an API/CLI/web app for finding and analyzing profiles across **1,000+ social-media websites**, with multiple detection techniques and a rating system intended to reduce false positives. It can also analyze names and username permutations. citeturn653862search1

### Python installation

```bash
pip3 install social-analyzer
```

### Basic search

```bash
python3 -m social_analyzer --username "prakash1807"
```

Depending on the current package/version, check:

```bash
python3 -m social_analyzer --help
```

The project's current README also documents CLI, web-app, metadata, filtering, screenshots, and JSON output capabilities. citeturn653862search1

### Why it is useful

Instead of only asking:

```text
Does "prakash1807" exist?
```

it can also help analyze:

```text
Prakash Singh
     ↓
possible username permutations
     ↓
candidate profiles
     ↓
detection/rating
```

**Best use:** broader name/username discovery and candidate analysis.

---

# 32.5 Holehe — Email-Centered OSINT

**Holehe** is different from Sherlock.

Sherlock:

```text
username → possible accounts
```

Holehe:

```text
email → public account-existence signals
```

Its current project provides a CLI and Python interface for checking whether an email is associated with supported online services. citeturn542405search11

### Install

```bash
pip3 install holehe
```

### Example

For an address that you are authorized to investigate:

```bash
holehe example@example.com
```

### Why it belongs in the toolkit

Use it when your starting identifier is an **email**, whereas Sherlock/Maigret are primarily username-focused.

### Important privacy boundary

Treat account-existence results as leads, not proof of identity.

Do not use email-based tools to:
- bypass authentication
- recover accounts
- obtain private information
- probe private account-recovery mechanisms
- access leaked credentials

**Best use:** checking public/service-level account-existence signals for an email you legitimately have permission to investigate.

---

# 32.6 SpiderFoot — Broader OSINT Automation

**SpiderFoot** is broader than Sherlock. It is an OSINT automation platform with a web interface and CLI, and its project currently documents **200+ modules** plus CSV/JSON/GEXF export, a database, visualizations, and integrations with many data sources. citeturn542405search7

### Basic idea

```text
                SpiderFoot
                    │
        ┌───────────┼───────────┐
        ↓           ↓           ↓
      Domain      Username     Email
        ↓           ↓           ↓
      Public      Public      Public
      sources     sources     sources
```

### Example start

```bash
python3 ./sf.py -l 127.0.0.1:5001
```

Then use its local web interface.

The exact modules depend on the version and configuration. citeturn542405search7

**Best use:** larger investigations where you want to correlate multiple types of public information rather than only usernames.

---

# 33. Which Tool Should I Use?

Use this quick decision tree.

```text
What do I have?
        │
        ├── Username
        │      ↓
        │   Sherlock
        │      +
        │   Maigret
        │      +
        │   WhatsMyName
        │      +
        │   Blackbird
        │
        ├── Name + username possibilities
        │      ↓
        │   Social Analyzer
        │      +
        │   Search engines
        │
        ├── Public email
        │      ↓
        │   Holehe
        │      +
        │   Search engines
        │
        └── Multiple identifiers / broader investigation
               ↓
           SpiderFoot
               +
        Search engines
```

---

# 34. Recommended Tool Combination

For a normal person-to-public-profile investigation, a good sequence is:

```text
1. Search engines
        ↓
2. Sherlock
        ↓
3. Maigret
        ↓
4. WhatsMyName
        ↓
5. Social Analyzer
        ↓
6. Search specific platforms
        ↓
7. Holehe (when an authorized public email is a relevant identifier)
        ↓
8. SpiderFoot (when the investigation is broad)
        ↓
9. Manual correlation
```

The tools are **not alternatives where you blindly trust whichever tool returns the most results**.

Think:

```text
Tool A found candidate
        ↓
Tool B independently finds candidate
        ↓
Public profile contains matching context
        ↓
Possible cross-link to another profile
        ↓
Higher confidence
```

---

# 35. Example Using the Prakash Singh Scenario

Known:

```text
Name:
Prakash Singh

Employer:
TCS

Possible username:
prakash1807
```

## Stage A — Search engines

```text
"Prakash Singh" TCS
"Prakash Singh" GitHub
"Prakash Singh" LeetCode
"prakash1807"
```

## Stage B — Sherlock

```bash
sherlock prakash1807
```

## Stage C — Maigret

```bash
maigret prakash1807 -a
```

## Stage D — WhatsMyName

Search:

```text
prakash1807
```

## Stage E — Social Analyzer

```bash
python3 -m social_analyzer --username "prakash1807"
```

## Stage F — Compare

Suppose results show:

```text
GitHub       → prakash1807
Reddit       → prakash1807
CodeChef     → prakash1807
```

Do NOT immediately conclude all three belong to Prakash Singh.

Inspect each one.

---

# 36. Tool Results vs Evidence

A useful way to think about the tools:

```text
Sherlock
Maigret
WhatsMyName
Blackbird
Social Analyzer
        │
        ↓
     DISCOVERY
        │
        ↓
Candidate accounts
        │
        ↓
Search engines / platform pages
        │
        ↓
Public profile information
        │
        ↓
CORRELATION
        │
        ↓
Confidence
```

The tools mainly help with **discovery**.

The human analyst performs the **verification**.

---

# 37. False-Positive Example

Suppose:

```text
Sherlock:
GitHub → prakash1807

Maigret:
GitHub → prakash1807
```

This does NOT mean:

```text
Target = account owner
```

Both tools may simply have discovered the same public URL.

Now inspect the profile:

```text
Name: Prakash Singh
Company: TCS
University: XYZ
Website: example.com
```

Then the candidate becomes stronger.

If the site also publicly links back to the known LinkedIn profile:

```text
GitHub
   ↓
Personal website
   ↓
LinkedIn
```

the evidence becomes significantly stronger.

---

# 38. Recommended Installation Priority

You don't need to install everything at once.

Start with:

```text
1. Sherlock
2. Maigret
3. WhatsMyName
```

Then add:

```text
4. Social Analyzer
5. Holehe
6. SpiderFoot
```

### Why?

The first three cover the core username-discovery problem.

The later tools expand the investigation into:

```text
Username
Name
Email
Other public identifiers
```

---

# 39. Tool Comparison

| Tool | Main input | Main purpose | Typical use |
|---|---|---|---|
| Sherlock | Username | Username enumeration | Find public accounts |
| Maigret | Username | Large-scale username search + parsing | Deep username investigation |
| WhatsMyName | Username | Username dataset/checking | Browser cross-check |
| Blackbird | Username | Fast username search | Another enumeration pass |
| Social Analyzer | Name/username | Profile discovery + analysis | Broader social search |
| Holehe | Email | Account-existence signals | Email-centered investigation |
| SpiderFoot | Multiple identifiers | OSINT automation | Broad correlation |
| Google/Bing/DuckDuckGo | Any text | Web discovery | Manual investigation |
| GitHub/GFG/LeetCode/etc. | Username/name | Platform-specific verification | Confirm developer accounts |

---

# 40. Final Tool Stack to Remember

```text
                    OSINT
                      │
       ┌──────────────┼───────────────┐
       ↓              ↓               ↓
   USERNAME         EMAIL            NAME
       │              │               │
       ↓              ↓               ↓
 Sherlock          Holehe        Search Engines
 Maigret                            Social Analyzer
 WhatsMyName
 Blackbird
       │              │               │
       └──────────────┼───────────────┘
                      ↓
                Candidate Accounts
                      ↓
             Platform Verification
                      ↓
              Evidence Correlation
                      ↓
             False Positive Removal
                      ↓
                 Confidence
```

> **Remember:** More tools do not automatically mean more accuracy. Ten tools finding the same username can still represent one weak signal. What matters is independent public evidence connecting a candidate account to the target.


> **Golden rule:** Never conclude that two accounts belong to the same person based only on a matching name or username. Look for multiple independent, public signals.
