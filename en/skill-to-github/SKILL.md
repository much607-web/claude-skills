---
name: skill-to-github
description: Use when publishing your skills to GitHub. Triggers on "upload my skill to GitHub", "I want to share my skill", "back up my skills". Scans for sensitive info, recommends public or private per skill, writes README and LICENSE, and uploads.
---

# Skill → GitHub

The user may not be a developer. Explain technical terms (repository, commit, push, etc.) in one plain line the first time they come up.

## 1. Choose the skills
Ask with a multiple-choice question tool (AskUserQuestion); if none exists, ask in text.
- Which skills to upload (multi-select from the user's skills)
- Don't ask about visibility yet — ask after steps 2–3, with a recommendation.

## 2. Sensitive-info scan (every file)
Read **every file** in each skill folder to the end — not just SKILL.md, but reference docs, scripts, examples, and templates. Open non-text files (images, spreadsheets) to check them; if a file can't be checked, list it as "check manually".

Look for:
- Real names, emails, phone numbers, addresses, account IDs
- Company names, clients, project names, amounts, internal figures
- Passwords, API keys, tokens (always recommend deleting)
- Personal file paths (e.g. `C:\Users\jane\...`)
- Personal work habits that mean nothing to others

Show the results as a table (file / location / content / recommendation: delete · generalize · keep) and get confirmation. Never edit the original skill — apply changes only to the upload copy.

## 3. Recommend visibility per skill
Based on the scan, recommend one of the following for each skill, with a one-line reason.

| Recommendation | When |
|---|---|
| **Public** | No sensitive info remains after generalizing, and others can use it as is |
| **Make a separate public version** | Broadly useful, but personal details (name, company rules, writing style) are woven through the core. Keep the original private; publish a generalized copy |
| **Keep private** | The user's personal style or work rules *are* the skill, or company/deal context could be inferred even after redaction |

When in doubt, recommend the safer option (private). After showing the table, ask for the final choice:
- "Go with the recommendation (Recommended)" / "Make everything private" / "Choose myself"
- If public and private skills are mixed, suggest two repositories (public and private).

## 4. Build the upload folder
```
<repo-name>/
├─ README.md
├─ LICENSE            (for public repos)
└─ <skill-name>/...   (one per skill)
```
- README.md: one-line intro, skills table (name / what it does / example phrase), install steps (claude.ai: zip the skill folder and upload it under Settings → Capabilities → Skills / Claude Code: copy the folder into `~/.claude/skills/`).
- LICENSE: MIT unless asked otherwise. Ask the user what name to use as copyright holder (a nickname or GitHub username is fine).
- Zip the whole folder and deliver it.

## 5. Final check (required for public repos)
Right before uploading, show the following again and ask "OK to publish as is?"
- The list of files to be uploaded
- Items kept in step 2 and items marked "check manually"
- Note: GitHub keeps history, so anything published can still be seen in old versions even after deletion

## 6. Upload
**A. GitHub connected and repository exists (automatic)**
1. Add the repository to the session with write access
2. Clone it, add the files, record the change with a one-line description (commit), and send it to GitHub (push)
3. Share the repository link when done

**B. Not connected or no repository yet (guide the user)**
1. Deliver the zip → unzip it
2. github.com → + (top right) → New repository → name, Public/Private, leave "Add README" off → Create
3. Click "uploading an existing file" → drag in everything *inside* the unzipped folder → Commit changes
4. Mention in one line that sharing the repo URL enables method A next time

## 7. Wrap-up
- Report only the repository link and the skills uploaded
- For public repos, one line: "Others can install these by following the README."

## When asked to update
Rerun steps 2–3 only for changed skills (flag any change in recommended visibility), update the README table, and upload to the same repository. Always ask before deleting existing files.
