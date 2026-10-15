# CPS Problem Solver

**Context · Problem · Solution**

Resume interrupted work in a fresh session without losing the user's intent, constraints, design criteria, or the reasons behind earlier decisions.

[한국어 안내](#한국어-안내) · [Skill instructions](skills/cps-problem-solver/SKILL.md)

## What it keeps

CPS updates one `CPS_STATE.md` in the task folder. It records the context, unresolved problems, chosen solutions, decision history, and the next action.

The usual size target is about **2,000 tokens**. At **3,000 tokens**, or before an update would exceed that threshold, the agent asks how to proceed. It must not automatically compress the record. Removing completed records or intermediate artifacts requires approval for the specific items.

The skill contains instructions, not a background service. It does not save while the agent is inactive, guarantee exact reconstruction of missing files, or synchronize state between computers. Keep the state file with the project when moving work to another machine or agent.

## Install by sharing the repository URL

Repository: https://github.com/Zeti-GD/CPS-Solver

Paste this into an agent that can fetch URLs and write local files:

```text
Install the cps-problem-solver skill from https://github.com/Zeti-GD/CPS-Solver.
Read the README and skills/cps-problem-solver/SKILL.md first.
Use the skill location supported by this agent, scoped to the current project.
Install only the skill folder; do not modify unrelated configuration.
If this skill already exists, show the differences and ask before replacing it.
Verify that the agent can discover the installed skill.
```

A URL by itself does not install a skill. The agent needs network and filesystem access. If the agent cannot install it, use the command or manual method below.

## Install from a terminal

Requires Node.js/npm and Git. Run in the project where you want to use CPS:

```sh
npx skills add https://github.com/Zeti-GD/CPS-Solver --skill cps-problem-solver
```

Choose the target agent when prompted. To choose explicitly:

```sh
npx skills add https://github.com/Zeti-GD/CPS-Solver --skill cps-problem-solver --agent codex
npx skills add https://github.com/Zeti-GD/CPS-Solver --skill cps-problem-solver --agent antigravity
npx skills add https://github.com/Zeti-GD/CPS-Solver --skill cps-problem-solver --agent antigravity-cli
npx skills add https://github.com/Zeti-GD/CPS-Solver --skill cps-problem-solver --agent gemini-cli
npx skills add https://github.com/Zeti-GD/CPS-Solver --skill cps-problem-solver --agent claude-code
```

Run only the command for your agent. Add `--global` if you deliberately want a user-wide installation. For `agy`, choose `antigravity-cli`; the Antigravity IDE uses `antigravity`. Gemini here means **Gemini CLI**, not the Gemini chat website.

The shared installer and its agent identifiers are documented in [vercel-labs/skills](https://github.com/vercel-labs/skills).

## Manual installation

Download the repository and copy the entire `skills/cps-problem-solver` folder to a supported project skill directory. The resulting path must end in `cps-problem-solver/SKILL.md`.

| Agent | Project installation path |
| --- | --- |
| Codex | `.agents/skills/cps-problem-solver/SKILL.md` |
| Antigravity IDE / CLI (agy) | `.agents/skills/cps-problem-solver/SKILL.md` |
| Gemini CLI | `.gemini/skills/cps-problem-solver/SKILL.md` |
| Claude Code | `.claude/skills/cps-problem-solver/SKILL.md` |

Restart or reload the agent if the skill does not appear. Preserve an existing installation until you have reviewed any differences.

## Start and resume

Start:

```text
Use cps-problem-solver for this task in [task folder].
Save the intent, constraints, design decisions and their reasons in CPS_STATE.md.
```

Resume in a fresh session:

```text
Use cps-problem-solver to resume the task in [task folder].
Read its CPS_STATE.md, explain the restored intent and last confirmed state,
then continue with the next unfinished action.
```

The instruction file is written in Korean with English discovery metadata. It uses no platform-specific tools and does not require other local skills.

## Publish this folder

1. Create a GitHub repository.
2. Upload this folder's **contents** so that `README.md` and `skills/` are at the repository root.
3. Share the repository URL with the installation prompt above.

Recommended layout:

```text
README.md
.gitignore
skills/
  cps-problem-solver/
    SKILL.md
```

No repository owner or branch name is hard-coded. `.gitignore` excludes task state from ordinary Git staging; browser uploads do not apply those exclusions. Publish the distribution files, not private task records.

## Validation status

The skill's behavior has been checked with simulated resume, token-threshold, missing-deliverable, and selective-deletion scenarios. The distribution structure and UTF-8 text have been checked. Installation and real session recovery have not been executed in every listed agent.

## 한국어 안내

CPS는 **Context, Problem, Solution**의 약자입니다. 새 세션에서도 사용자 의도와 설계 기준을 이어갈 수 있도록 작업의 문맥, 문제, 해결책을 기록합니다. 마지막에 무엇을 했는지와 함께 왜 그 방향을 선택했는지도 남깁니다.

작업 폴더의 `CPS_STATE.md` 하나를 계속 갱신합니다. 평소에는 약 **2,000토큰**을 목표로 관리하고, **3,000토큰**에 도달하거나 다음 갱신으로 넘을 것 같으면 처리 방법을 묻습니다. 자동으로 압축하지 않으며 완료 기록이나 중간 파일도 승인받은 항목만 삭제합니다.

### 주소를 붙여 넣어 설치하기

위 설치 명령에는 실제 GitHub 저장소 주소가 들어 있습니다. 그대로 실행하거나, 에이전트에게 다음 문구를 복사해 보내세요.

```text
https://github.com/Zeti-GD/CPS-Solver에서 cps-problem-solver 스킬을 설치해줘.
먼저 README와 skills/cps-problem-solver/SKILL.md를 읽고,
현재 사용하는 에이전트의 프로젝트용 스킬 폴더에 설치해줘.
다른 설정은 건드리지 말고, 같은 스킬이 있으면 차이를 보여준 뒤 교체 여부를 물어봐.
설치 후 스킬을 인식하는지도 확인해줘.
```

주소만 보내면 자동 설치되는 방식은 아닙니다. 에이전트가 웹에 접근하고 파일을 쓸 수 있어야 합니다. 설치를 실행할 수 없는 환경에서는 위 터미널 명령이나 수동 복사 방법을 사용하세요. `agy`는 Antigravity CLI를, Gemini는 Gemini CLI를 기준으로 안내했습니다.

### 작업을 시작하거나 이어가기

처음에는 “이 작업에 cps-problem-solver를 사용하고, [작업 폴더]에 상태를 기록해줘”라고 요청하세요.

새 세션에서는 “[작업 폴더]의 CPS_STATE.md를 읽고, 이전 의도와 마지막 상태를 확인한 뒤 이어서 작업해줘. cps-problem-solver를 사용해줘”라고 요청하면 됩니다.

다른 컴퓨터나 에이전트에서 이어갈 때도 상태 파일이 필요합니다. 결과물이 없다면 기록된 명세로 복원 가능한 부분을 확인하지만, 기록에 없는 세부 내용까지 그대로 재현한다고 보장하지는 않습니다.

### GitHub에 올리기

이 폴더 안의 파일과 `skills` 폴더를 저장소 최상위에 올리세요. 업로드한 뒤 저장소 주소를 복사해 위 설치 요청문에 넣으면 됩니다. 개인 작업의 `CPS_STATE.md`는 배포 파일에 포함하지 않습니다.

README는 영어 안내와 한국어 안내를 함께 담았고, 스킬 본문은 한국어로 작성했습니다. 현재 검증 범위는 모의 재개 상황과 배포 파일 형식입니다. 모든 앱에서 실제 설치와 세션 초기화 후 재개를 시험한 상태는 아닙니다.

## References

- [Agent Skills specification](https://agentskills.io/specification)
- [Skills installer](https://github.com/vercel-labs/skills)
- [Codex skills](https://developers.openai.com/codex/skills)
- [Antigravity skills](https://antigravity.google/docs/skills)
- [Gemini CLI skills](https://geminicli.com/docs/cli/using-agent-skills/)
- [Claude Code skills](https://code.claude.com/docs/en/skills)
