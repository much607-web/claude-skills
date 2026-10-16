# Claude Skills

Claude에서 바로 쓸 수 있는 스킬 모음입니다. 한국어판과 영어판이 있어요.
A collection of ready-to-use Claude skills, in Korean and English. ([English below](#english))

## 한국어

| 스킬 | 하는 일 | 이렇게 말하면 작동 | 다운로드 |
|---|---|---|---|
| [chat-to-project](chat-to-project/SKILL.md) | 채팅에서 하던 작업을 Claude 프로젝트로 옮기기. 영역 분리안을 먼저 묻고, 프로젝트별 지침·작업현황·첫 메시지 파일을 만들어 줌 | "이거 프로젝트로 전환해줘" | [⬇ zip](https://github.com/much607-web/claude-skills/raw/main/downloads/chat-to-project.zip) |
| [skill-to-github](skill-to-github/SKILL.md) | 만든 스킬을 깃허브에 올리기. 민감정보 점검, 스킬별 공개 여부 추천, README·라이선스 작성, 업로드 안내까지 | "이 스킬 깃허브에 올려줘" | [⬇ zip](https://github.com/much607-web/claude-skills/raw/main/downloads/skill-to-github.zip) |

### 설치 방법
**claude.ai / Claude 앱**
1. 위 표에서 원하는 스킬의 **⬇ zip** 클릭 (압축 풀 필요 없음)
2. 설정 → 기능(Capabilities) → 스킬에서 받은 zip 파일 업로드

**Claude Code**
- 스킬 폴더를 `~/.claude/skills/` 아래에 복사

한국어판과 영어판은 이름이 같으니 둘 중 하나만 설치하세요.

---

## English

English versions live in the [`en/`](en/) folder.

| Skill | What it does | Say this | Download |
|---|---|---|---|
| [chat-to-project](en/chat-to-project/SKILL.md) | Turns an ongoing chat into one or more Claude Projects — proposes how to split the work first, then generates instructions, a status file, and a first message for each project | "Turn this into a project" | [⬇ zip](https://github.com/much607-web/claude-skills/raw/main/downloads/chat-to-project-en.zip) |
| [skill-to-github](en/skill-to-github/SKILL.md) | Publishes your skills to GitHub — scans every file for sensitive info, recommends public or private per skill, writes README/LICENSE, and uploads or walks you through it | "Upload my skill to GitHub" | [⬇ zip](https://github.com/much607-web/claude-skills/raw/main/downloads/skill-to-github-en.zip) |

### Install
**claude.ai / Claude app**
1. Click **⬇ zip** for the skill you want (no need to unzip)
2. Upload the zip under Settings → Capabilities → Skills

**Claude Code**
- Copy the skill folder into `~/.claude/skills/`

The Korean and English versions share the same name — install only one of them.

## License
MIT
