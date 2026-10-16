---
name: chat-to-project
description: Use when moving work from a regular chat into a Claude Project. Triggers on "turn this into a project", "move this to a project", "split this into projects". Proposes how to split the work first, then creates instructions, a status file, and a first message for each project.
---

# Chat → Project

Claude cannot create projects or move chats itself. Instead, it builds a "handoff pack" the user only has to paste into a new project. The main value of a project is keeping areas of work separate, so always settle the split before building the pack.

## 1. Review the conversation
Extract only what actually appeared in the conversation (no guessing).
- The topics and chunks of work covered
- For each chunk: goal, confirmed decisions, key facts and numbers, open tasks, files and links used
- Formats, tone, and restrictions the user asked for

## 2. Propose a split → ask the user (required)
Group the chunks into a proposed set of projects and let the user choose with a multiple-choice question tool (AskUserQuestion). If no such tool exists, ask in text.

Split criteria (in priority order):
1. Different deliverables → separate (e.g. report vs spreadsheet model)
2. Different audiences or confidentiality levels → separate (work vs personal)
3. Conflicting instructions (format, tone) → separate
4. Topics that keep drawing on the same material → keep together

Questions:
- Q1. How to split: put the recommended option first, marked "(Recommended)". Usually "Keep as one / Recommended split (N projects) / Split further"
  - Each option's description names the projects and the topics each will hold, in one line
- Q2. (If splitting and needed) Which project an ambiguous topic should go to
- If the user mentioned an existing project of the same kind, include an "Add to existing project" option

If the user is away, proceed with the recommended split and note at the top: "Proceeded with the recommended split (N projects)."

## 3. Sensitive-info check
- For anything that looks sensitive (company names, clients, amounts, personal details), ask once before including it: "Keep as is, or replace with a placeholder?" (best asked together with the step 2 questions).
- Never mix work and personal content in the same file.

## 4. Build the pack per project (3 files each)
Prefix each file name with the project name (e.g. `Report_instructions.md`).

**① [name]_instructions.md** — to paste into the project's Instructions field. Under 300 words.
- The project's purpose in 1–2 lines; what's in scope and out of scope
- Claude's role, answer format and tone, standing rules
- "Read status.md first"

**② [name]_status.md** — to upload to the project's Knowledge.
- Date / background / decisions (table) / key facts and numbers / open tasks (checkboxes) / open questions / reference files
- Leave out topics that went to another project; if related, add one line: "Related: ○○ project"

**③ [name]_first_message.txt** — 1–3 lines to send as the first message in a new chat.
- e.g. "Let's continue from status.md, starting with open task #1."

Create the files and deliver them to the user. If the user named a save folder, save there too.

## 5. Guide the user (briefly)
For each project, list only these steps:
1. Sidebar → Projects → New project (suggest a name)
2. Paste ① into Instructions
3. Upload ② to Knowledge, plus any original files for that area
4. Send ③ in a new chat

## When asked to update the status
On "update the status file", build a new version from the existing status.md that adds only this conversation's new decisions and progress (don't overwrite the original; save a new dated file). If this conversation mixes content from different areas, ask which project each part goes to first.
