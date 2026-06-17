---
name: easy-prompt-symbols
description: "Turn rough requests into easy symbol-based prompts using #, *, {}, [], angle brackets, -, and quotation marks. Use when the user asks to make a prompt, improve a prompt, create a reusable prompt template, explain prompt symbols, or convert plain Korean instructions into a clear prompt that everyday users can copy and use."
---

# Easy Prompt Symbols

## Purpose

Turn a rough request into a copy-ready prompt using seven familiar symbols. The skill should feel simple enough for non-engineers: each symbol has one job, and the final prompt should be clear without needing a lesson in prompt engineering.

## Symbol Grammar

Use only these symbols for structural meaning:

| 기호 | 뜻 | 쓰는 곳 |
| --- | --- | --- |
| `#` | 큰 제목 | 긴 프롬프트를 `# 목적`, `# 입력`, `# 조건`, `# 출력`처럼 나눈다. |
| `*` | 중요 표시 | 꼭 지켜야 할 조건이나 핵심 항목만 강조한다. |
| `{}` | 바꿔 넣는 값 | `{주제}`, `{대상}`, `{분량}`, `{말투}`처럼 매번 달라지는 값을 둔다. |
| `[]` | 선택지와 범위 | `[친근하게 | 전문적으로]`, `[300-500자]`처럼 고를 수 있는 값을 둔다. |
| `<>` | 실제 내용 자리 | `<여기에 초안 붙여넣기>`처럼 사용자가 넣을 원문 자리를 만든다. |
| `-` | 순서 없는 목록 | 순서가 중요하지 않은 조건을 나열한다. |
| `""` | 뜻 고정 | `"쉬운 말"`처럼 AI가 다르게 해석하면 안 되는 말을 고정한다. |

## Workflow

1. Find the user's real goal, audience, input material, and output shape.
2. If one missing detail would completely change the result, ask one short question. Otherwise, use a `{바꿔넣을값}` placeholder.
3. Choose 3-6 `#` sections. Prefer simple Korean headings: `# 목적`, `# 입력`, `# 조건`, `# 출력 형식`, `# 확인 기준`.
4. Use `{}` for values the user can replace, and `<>` for raw material the user should paste.
5. Use `[]` only for real choices, ranges, formats, or limits.
6. Use `""` only for words whose meaning must stay fixed.
7. Return the finished prompt in one fenced code block. Add a short variable list only when placeholders need explanation.

## Composition Rules

- Preserve the user's language unless they request another language.
- Prefer concrete instructions over meta-instructions about prompt engineering.
- Keep the prompt usable as-is. Do not explain every symbol inside the generated prompt unless the user asks for teaching material.
- Do not add unrelated roles, chain-of-thought requests, hidden reasoning instructions, or broad fallback behavior.
- Do not use `{}` for content that should be supplied verbatim. Use `<>` for actual content.
- Do not use `[]` for normal prose. Use it only for options, ranges, or constrained formats.
- Use `*` sparingly for must-follow requirements; too many emphasized items erase priority.
- If the source request is simple, make a compact prompt instead of forcing every possible section.
- Prefer everyday wording over technical labels. For example, use `# 해야 할 일` instead of `# Objective` for Korean users.

## Output Pattern

When responding, use this shape:

````text
아래 프롬프트를 사용하세요.

```prompt
# 목적
...
```

변수:
- `{변수}`: ...
````

Omit `변수:` when the generated prompt has no placeholders or all placeholders are self-explanatory.

## Mini Example

Rough request:

```text
블로그 글 써줘. AI 생산성에 대해, 너무 어렵지 않게.
```

Generated prompt:

```prompt
# 목적
{대상}이 쉽게 이해할 수 있는 블로그 글을 작성한다.

# 주제
"AI 생산성"

# 조건
- *어려운 용어는 피하고, 꼭 필요하면 짧게 풀어서 설명한다.*
- 실제 업무에서 쓸 수 있는 예시를 3-5개 넣는다.
- 말투는 [친근하게 | 전문적으로] 중 하나로 유지한다.
- 분량은 [800-1200자]로 작성한다.

# 출력 형식
- 제목
- 짧은 도입
- 소제목이 있는 본문
- 마지막 한 줄 요약
```
