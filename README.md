# 내 친애하는 적대자

사용자를 참칭하는 제3의 적대자 `'나'`의 주장과 판단을 논리와 검증된 사실로 해체하는 레드팀 검증 프롬프트다.

비판의 강도를 조롱이나 역할극에서 얻지 않는다. 직접 인용, 수치, 계산, 내부 모순, 검증된 외부 사실과 논리적 귀결을 사용해 핵심 주장·숨은 전제·파생 결론·예상 반론을 끝까지 검증한다. 결과는 건조한 `레드팀 검증 보고서` 형식으로 작성한다.

## 핵심 원칙

- 사용자, LLM, 참칭자 `'나'`를 서로 분리한다.
- LLM은 사용자가 아니라 `'나'`의 논지를 공격한다.
- 사실과 판단, 제한된 추론, 확인 불가 사항을 구분한다.
- 제출 자료가 허용하는 가장 강한 해석을 공격해 허수아비 논증을 피한다.
- MECE를 쟁점 선정, 문단 구성, 근거 배치와 보고서 전체에 적용한다.
- 하나의 치명적 결함에서 멈추지 않고 파급 효과와 주요 반론까지 추적한다.
- 조롱, 비꼼, 야유, 과장, 법정극과 인신 공격을 사용하지 않는다.
- 명시적으로 호출된 경우에만 작동한다.

## 구성

```text
.
├── claude/
│   └── my-dear-adversary/
│       └── SKILL.md
├── codex/
│   └── my-dear-adversary/
│       ├── SKILL.md
│       └── agents/
│           └── openai.yaml
└── prompts/
    └── my-dear-adversary.ko.md
```

## Claude Code

`claude/my-dear-adversary` 폴더를 개인 스킬 경로로 복사한다.

```bash
mkdir -p ~/.claude/skills
cp -R claude/my-dear-adversary ~/.claude/skills/
```

호출:

```text
/my-dear-adversary
```

Claude 버전은 `disable-model-invocation: true`를 사용해 모델의 자동 호출을 차단한다.

## Codex

`codex/my-dear-adversary` 폴더를 개인 스킬 경로로 복사한다.

```bash
mkdir -p ~/.agents/skills
cp -R codex/my-dear-adversary ~/.agents/skills/
```

호출:

```text
$my-dear-adversary
```

Codex 버전은 `agents/openai.yaml`에서 다음 정책을 사용한다.

```yaml
policy:
  allow_implicit_invocation: false
```

## 일반 웹 LLM

[`prompts/my-dear-adversary.ko.md`](prompts/my-dear-adversary.ko.md)의 전체 내용을 ChatGPT, Claude, Gemini 등 원하는 웹 LLM의 새 대화에 붙여넣고 마지막 입력란에 검토 자료를 추가한다.

검색 기능이 있는 모델은 필요한 외부 사실을 직접 검증하고 출처를 제시하도록 했으며, 검색 기능이 없으면 확인하지 못한 외부 지식을 사실처럼 사용하지 않도록 제한했다.

## 출력

기본 출력은 다음 구조를 따른다.

```text
레드팀 검증 보고서
├── 검토 대상
├── 최종 판정
├── 주요 결함
│   └── 판정 → 근거 → 영향
├── 예상 반론 검증
├── 확인 불가 사항
└── 종합 판단
```

중요도는 `치명적`, `중대`, `보통`으로 구분하며 표현의 공격성이 아니라 입증된 영향에 따라 판정한다.

## 주의

이 프롬프트는 작업물, 주장, 판단, 결정과 자료에 드러난 오류를 공격한다. 제출 자료로 확인할 수 없는 성격, 지능, 의도나 자격을 추정하지 않는다. 외부 사실을 검증할 수 없는 환경에서는 해당 사실을 판정 근거로 사용하지 않는다.
