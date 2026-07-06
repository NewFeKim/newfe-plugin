# newfe-plugin

개인용 Claude Code 플러그인 마켓플레이스. 시각 자료·PPT 제작을 돕는 스킬 모음입니다.

## 설치

```bash
# 1. 마켓플레이스 등록
claude plugin marketplace add NewFeKim/newfe-plugin

# 2. 원하는 플러그인 설치
claude plugin install visual-toolkit@newfe-plugin
claude plugin install ppt-toolkit@newfe-plugin
```

> `ppt-toolkit`은 `visual-toolkit`의 스킬(레이아웃·컬러 추천)과 연계해 동작하도록
> 설계되어 있으므로 **둘 다 설치하는 것을 권장**합니다.

## 플러그인 목록

### visual-toolkit — 시각 디자인 의사결정 도구

| 스킬 | 하는 일 | 트리거 예시 |
|------|---------|------------|
| `visual-technique-picker` | 13가지 시각 전달 기법(인포그래픽·다이어그램·차트 등) 중 상황에 맞는 기법 추천 | "이걸 어떻게 보여주지?" |
| `color-palette-picker` | 분위기·목적 기반 색상 팔레트 추천 (헥스코드 + WCAG 대비 체크) | "어울리는 색 조합 추천해줘" |
| `slide-layout-picker` | 콘텐츠 성격에 맞는 슬라이드 레이아웃 패턴 10종 추천 | "슬라이드 레이아웃 어떻게 잡지?" |

### ppt-toolkit — PPT 제작 end-to-end 워크플로

| 스킬 | 하는 일 | 트리거 예시 |
|------|---------|------------|
| `presentation-planner` | 목적·청중·핵심 메시지 등 10가지 기준으로 슬라이드별 기획서 + 디자인 시스템 출력, 확인 후 .pptx 생성 연계 | "PPT 만들어줘", "피치덱 뼈대 잡아줘" |

지원 스토리라인: 문제→해결 · 개념→실습 · Before→After · 데이터 스토리텔링 · 타임라인/로드맵
지원 디자인 스타일: B2B SaaS · 교육자료 · 보고서 · IR · 컨설팅/전략 보고서 · 스타트업 브리핑

### code-dev-toolkit — (준비 중)

코드 개발 보조 스킬 모음. 스킬이 추가되면 마켓플레이스에 등록될 예정입니다.

## 저장소 구조

```
newfe-plugin/
├── .claude-plugin/marketplace.json    # 마켓플레이스 카탈로그
└── plugins/
    ├── visual-toolkit/
    │   ├── .claude-plugin/plugin.json
    │   └── skills/<skill-name>/SKILL.md
    ├── ppt-toolkit/
    └── code-dev-toolkit/              # 준비 중
```

## 스킬 개발 규칙

- 스킬은 `plugins/<plugin>/skills/<skill-name>/SKILL.md` 형태로 추가
- `plugin.json`에 `"skills": ["./skills/"]` 필드 필수 (누락 시 설치 실패)
- 새 플러그인은 `marketplace.json`의 `plugins` 배열에 `"source": "./plugins/<name>"` 형식으로 등록
- 스킬 추가/수정 시 [skill-creator](https://github.com/anthropics/skills)로 eval 검증 후 커밋
- 버전 규칙: 스킬 추가 = minor (1.0.0 → 1.1.0), 스킬 내용 수정 = patch

## 라이선스

[MIT](LICENSE)
