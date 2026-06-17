# Easy Prompt Symbols

![Codex Skill](https://img.shields.io/badge/Codex-Skill-111827?style=for-the-badge)
![Prompting](https://img.shields.io/badge/Prompting-7%20Symbols-2563EB?style=for-the-badge)
![Korean First](https://img.shields.io/badge/Korean-First-16A34A?style=for-the-badge)

기호 7개만으로 막연한 요청을 복붙 가능한 AI 프롬프트로 바꿔주는 Codex skill입니다.

복잡한 프롬프트 이론을 외우기보다, `#`, `*`, `{}`, `[]`, `<>`, `-`, `""`를 각자 한 가지 용도로만 써서 AI가 덜 헷갈리게 만듭니다.

## 핵심 아이디어

| 기호 | 뜻 | 예시 |
| --- | --- | --- |
| `#` | 큰 제목 | `# 목적`, `# 입력`, `# 출력 형식` |
| `*` | 중요 표시 | `*반드시 쉬운 말로 설명한다.*` |
| `{}` | 바꿔 넣는 값 | `{주제}`, `{대상}`, `{분량}` |
| `[]` | 선택지와 범위 | `[친근하게 | 전문적으로]`, `[300-500자]` |
| `<>` | 실제 내용 자리 | `<여기에 초안 붙여넣기>` |
| `-` | 순서 없는 목록 | `- 예시 3개 포함` |
| `""` | 뜻 고정 | `"쉬운 말"`, `"실행 계획"` |

## 설치

Codex에서 쓰려면 아래처럼 설치합니다.

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/jiyeongjun/easy-prompt-symbols.git ~/.codex/skills/easy-prompt-symbols
```

Claude Code에서 `/easy-prompt-symbols`로 쓰려면 아래처럼 설치합니다.

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/jiyeongjun/easy-prompt-symbols.git ~/.claude/skills/easy-prompt-symbols
```

설치 후 Codex에서 이렇게 요청할 수 있습니다.

```text
Use $easy-prompt-symbols to turn my rough request into an easy symbol-based prompt.
```

한국어로는 이렇게 써도 됩니다.

```text
$easy-prompt-symbols 써서 이 요청을 기호 기반 프롬프트로 바꿔줘:
인스타 릴스 대본 써줘. 초보 창업자 대상이고 너무 광고 같지 않게.
```

설치 후 Claude Code에서는 `/easy-prompt-symbols`로 호출합니다.

```text
/easy-prompt-symbols
회의록을 정리해줘. 중요한 결정이랑 할 일만 뽑아줘.
```

CLI에서 한 번에 실행할 때도 같은 slash 호출을 쓸 수 있습니다.

```bash
claude -p '/easy-prompt-symbols
회의록을 정리해줘. 중요한 결정이랑 할 일만 뽑아줘.'
```

## 결과 예시

```prompt
# 목적
{대상}이 공감할 수 있는 인스타 릴스 대본을 작성한다.

# 입력
- 주제: "초보 창업자가 처음 겪는 시행착오"
- 대상: {대상}
- 말투: [친근하게 | 담백하게 | 전문가처럼]

# 조건
- *광고처럼 보이지 않게 자연스럽게 말한다.*
- 첫 3초 안에 관심을 끄는 문장으로 시작한다.
- 어려운 용어는 쓰지 않는다.
- 전체 길이는 [30-45초] 분량으로 맞춘다.

# 출력 형식
- 훅
- 장면별 대본
- 화면 자막
- 마지막 행동 유도 문장
```

## 효과가 나는 이유

- `#`로 블록을 나누면 AI가 요청의 구조를 빨리 파악합니다.
- `{}`와 `<>`를 나누면 바꿔 넣을 값과 실제 원문을 혼동하지 않습니다.
- `[]`는 선택지를 제한해 결과가 엉뚱한 방향으로 튀는 일을 줄입니다.
- `""`는 중요한 단어의 뜻을 고정해 해석 차이를 줄입니다.
- 짧은 요청도 반복 가능한 템플릿으로 바꿀 수 있습니다.

## 한계

이 방식은 좋은 프롬프트를 만드는 데 도움을 주지만, 모든 답변 품질을 자동으로 보장하지는 않습니다. 특히 전문 지식, 최신 정보, 법률, 의료, 금융 판단이 필요한 작업은 출처 확인과 사람의 검토가 필요합니다.

가장 효과적인 경우는 다음과 같습니다.

- 블로그, 이메일, 제안서, SNS 대본처럼 출력 형식이 중요한 작업
- 매번 일부 값만 바꿔 반복해서 쓰는 프롬프트
- AI가 조건을 자주 빠뜨리는 작업
- 초보자가 프롬프트 구조를 빠르게 익혀야 하는 상황

## 구성

```text
easy-prompt-symbols/
├── SKILL.md
├── README.md
└── agents/
    └── openai.yaml
```

## 검증

- `skill-creator`의 `quick_validate.py` 통과
- Claude Code로 `skill-creator` 기준 독립 검토 PASS

## 라이선스

아직 별도 라이선스를 지정하지 않았습니다.
