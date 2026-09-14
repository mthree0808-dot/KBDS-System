# Component: Form / InputField

본 문서는 서비스 전반에서 사용되는 단일 라인 텍스트 입력 필드(InputField) 명세입니다.
피그마의 Instance Swap 구조를 지원하기 위해 상위 컨테이너 구조(Label / Input Body / Help Message)와 내부 슬롯 합성 패턴(Prefix / Core / Suffix), 그리고 상태별 토큰 매핑 매트릭스를 정의합니다.

---

## 1. 컴포넌트 구조 (Hierarchy)

InputField는 세로 방향(Auto Layout Vertical)의 3단 복합 구조로 조립됩니다.

```text
[InputField Container] (Gap: 8px)
  ├── 1. Title Area (Label + Required + Tooltip)
  ├── 2. Input Box (Min-Height: 56px, Radius: 12px)
  │     ├── [Prefix Slot]   : 은행/카드 로고, 통화 기호, 국가번호 등
  │     ├── [Core Slot]     : 텍스트 입력값 / Placeholder, 커서 인디케이터
  │     └── [Suffix Slot]   : 삭제(X), 타이머, 단위('원'), 비밀번호 마스킹, 인라인 버튼 등
  └── 3. Message Area (Error Message + Sub Label / Counter)
```

---

## 2. 속성 (Properties & Variants)

| Property | Type | Options | Default | 설명 |
|---|---|---|---|---|
| `state` | String | `default`, `focused`, `entered`, `error`, `disabled` | `default` | 인터랙션 상태 |
| `required` | Boolean | `true`, `false` | `false` | 필수 입력 여부 (`(필수)` 텍스트 표시) |
| `tooltip` | Boolean | `true`, `false` | `false` | 타이틀 우측 도움말 툴팁 아이콘 표시 여부 |
| `hasPrefix` | Boolean | `true`, `false` | `false` | 좌측 Prefix 요소 표시 여부 |
| `hasSuffix` | Boolean | `true`, `false` | `false` | 우측 Suffix 요소 표시 여부 |
| `hasTextDel` | Boolean | `true`, `false` | `true` | 활성 입력 시 전체 삭제(X) 아이콘 제공 여부 |

---

## 3. 상세 레이아웃 스펙

### 전체 컨테이너
* **Width:** `Fill container` (기본 기준폭: `350px`)
* **Layout:** Auto Layout Vertical, Align Start, Justify Start
* **Gap:** `8px` (`$spacing.spacingMd`)

### 1. 상단 타이틀 영역 (Title Area)
* **Dimensions:** Width `Fill container`, Height `Hug contents`
* **Layout:** Auto Layout Horizontal, Align Center, Gap `2px` (`$spacing.spacing2xs`)
* **Title Text:**
  * Typography: `KBFG Text`, Size `14px` (`$type.fontSizeBodyXsFixed`), Weight `700` (`$type.fontWeightBold`), Line Height `20px`
  * Color: `var(--text-neutral-primary)` (`#111827`)
* **Required Indicator:**
  * Text: `(필수)`
  * Typography: `KBFG Text`, Size `11px` (`$type.fontSizeBody4xsFixed`), Weight `500` (`$type.fontWeightMedium`), Line Height `15px`
  * Color: `var(--text-accent-red)` (`#e53838`)
* **Tooltip Icon Button:**
  * Box: `16px x 16px`, Radius `4px` (`$radius.radius3xs`)
  * Icon Vector: `12px x 12px`, Color `var(--icon-neutral-quaternary)` (`#9ca3af`)

### 2. 인풋 박스 본체 (Input Box)
* **Dimensions:** Width `Fill container`, Min Height `56px`
* **Padding:** All `16px` (`$spacing.spacingXl`)
* **Corner Radius:** `12px` (`$radius.radiusMd`)
* **Layout:** Auto Layout Horizontal, Align Center, Gap `8px` (`$spacing.spacingMd`)
* **Core Text Area (입력 영역):**
  * Typography: `KBFG Text`, Size `16px` (`$type.fontSizeBodyMdFixed`), Line Height `22px`
  * Value Weight: 미입력(Placeholder) 시 `500` (`$type.fontWeightMedium`), 값 입력(Entered) 시 `700` (`$type.fontWeightBold`)
  * Caret (커서): Width `1.6px`, Height `22px`, Color `var(--icon-accent-brand-alt)` (`#111827`)

### 3. 하단 메시지 영역 (Message Area)
* **Dimensions:** Width `Fill container`, Height `Hug contents`
* **Layout:** Auto Layout Vertical, Gap `2px` (에러 발생 시) 또는 `10px`
* **Padding:** Left / Right `6px` (`$spacing.spacingSm`)
* **Error Message:**
  * Icon: `12px x 12px` (Vector: `9px x 9px`), Color `var(--icon-status-negative)` (`#e53838`)
  * Typography: `KBFG Text`, Size `13px` (`$type.fontSizeBody2xsFixed`), Weight `500`, Line Height `18px`
  * Color: `var(--text-status-negative)` (`#e53838`)
* **Sub Label / Helper Text:**
  * Typography: `KBFG Text`, Size `13px` (`$type.fontSizeBody2xsFixed`), Weight `500`, Line Height `18px`
  * Color: `var(--text-neutral-quaternary)` (`#6b7280`)

---

## 4. 토큰 바인딩 종합 (Token Mapping Matrix)

| 구분 (Area) | UI 요소 (Element) | Default / Normal | Focused | Entered | Error | Disabled |
|---|---|---|---|---|---|---|
| **Title Area** | 타이틀 텍스트 | `var(--text-neutral-primary)` | `var(--text-neutral-primary)` | `var(--text-neutral-primary)` | `var(--text-neutral-primary)` | `var(--text-neutral-disabled)` |
| | 필수 표시 `(필수)` | `var(--text-accent-red)` | `var(--text-accent-red)` | `var(--text-accent-red)` | `var(--text-accent-red)` | `var(--text-neutral-disabled)` |
| | 툴팁 아이콘 | `var(--icon-neutral-quaternary)` | `var(--icon-neutral-quaternary)` | `var(--icon-neutral-quaternary)` | `var(--icon-neutral-quaternary)` | `var(--icon-neutral-disabled)` |
| **Input Box** | 배경 (Background) | Transparent | Transparent | Transparent | Transparent | `var(--surface-neutral-disabled)` |
| | 테두리 (Border/Outline) | `1px solid var(--border-neutral-primary-muted)` | `1px solid var(--border-neutral-primary-muted)` | `1px solid var(--border-neutral-primary-muted)` | `2px solid var(--border-status-negative)` | None (Outline 제거) |
| | 텍스트 / 플레이스홀더 | `var(--text-neutral-placeholder)` | `var(--text-neutral-primary)` | `var(--text-neutral-primary)` | `var(--text-neutral-primary)` | `var(--text-neutral-placeholder)` |
| | 커서 (Caret) | - | `var(--icon-accent-brand-alt)` | - | `var(--icon-accent-brand-alt)` | - |
| **Slots** | 삭제(X) 아이콘 | - | `var(--icon-neutral-quaternary)` | - | - | - |
| | 단위 텍스트 ('원') | `var(--text-neutral-primary)` | `var(--text-neutral-primary)` | `var(--text-neutral-primary)` | `var(--text-status-negative)` | `var(--text-neutral-disabled)` |
| | 인라인 액션 버튼 배경 | `var(--surface-accent-brand)` | `var(--surface-accent-brand)` | `var(--surface-accent-brand)` | `var(--surface-accent-brand)` | `var(--surface-neutral-disabled)` |
| **Message Area**| 에러 아이콘 / 텍스트 | - | - | - | `var(--text-status-negative)` / `var(--icon-status-negative)` | - |
| | 서브 레이블 / 헬퍼 | `var(--text-neutral-quaternary)` | `var(--text-neutral-quaternary)` | `var(--text-neutral-quaternary)` | `var(--text-neutral-quaternary)` | `var(--text-neutral-disabled)` |

---

## 5. ITEM 슬롯 스왑 패턴 (Slot Swap Cases)

피그마 그리드에 나열된 모든 세부 케이스는 인풋 박스 내부의 3가지 슬롯 조합으로 매핑됩니다.

```text
[Prefix Slot] ─── (Gap 8px) ─── [Core Slot] ─── (Gap 8px) ─── [Suffix Slot]
```

### Prefix Slot 유형
* **None:** 기본 단일 텍스트 입력창
* **Icon / Logo:** 은행 심볼마크, 카드사 로고, 검색(Magnifier) 아이콘
* **Fixed Text:** 국가번호(`+82`), 프로토콜(`https://`)

### Core Slot 유형
* **Single Text:** 단일 텍스트/숫자 (기본값)
* **Split Field (분할형):**
  * 주민등록번호 앞자리(6자리) + `-` + 뒷자리(1자리 or 마스킹 6자리)
  * 사업자등록번호(3자리 - 2자리 - 5자리)
  * 카드번호(4자리씩 4분할)

### Suffix Slot 유형 (복수 조합 가능)
* **Delete Button:** 입력값 일괄 삭제 X 버튼 (`24px x 24px`, 아이콘 `18px`, `var(--icon-neutral-quaternary)`)
* **Unit Text:** 단위 표기 (`"원"`, `"%"`, `"개월"`, `"건"`) - Font Weight `700`, `var(--text-neutral-primary)`
* **Timer:** 남은 인증 시간 (`"03:00"`) - `var(--text-status-negative)`
* **Dropdown Arrow:** 선택형 인풋의 펼침 화살표 Chevron 아이콘
* **Security Masking Toggle:** 비밀번호 표시/숨김 눈(Eye) 아이콘
* **Inline Action Button (인라인 버튼):**
  * 유형: `"인증요청"`, `"재전송"`, `"전액"`, `"조회"`
  * 버튼 규격: Height `32px` ~ `36px`, Radius `6px` (`$radius.radius2xs`), Padding Horizontal `12px`
  * 배경: `var(--surface-accent-brand)` 또는 `var(--surface-neutral-primary-muted)`

---

## 6. AI UI 생성 규칙 (Generation Rules)

1. **상태 전환 시 레이아웃 보존:** 에러 메시지가 노출될 때 인풋 필드의 높이나 너비가 흔들리지 않도록 하단 메시지 영역의 간격을 유지하세요.
2. **복합 금융 입력 필드 구현 원칙:**
   - 금액 입력 케이스: 우측 Suffix 슬롯에 `"원"` 텍스트를 배치하고 필요 시 `"전액"` 인라인 버튼을 함께 결합합니다.
   - 계좌번호 입력 케이스: Prefix 슬롯에 은행 로고를 배치하고 Core 슬롯에 숫자 폰트(`Pretendard`)를 바인딩합니다.
3. **토큰 바인딩 강제:** 하드코딩된 `#D1D5DB`, `#E53838`, `rgba(102, 112, 133, 0.10)` 대신 정의된 시맨틱 토큰 변수(`var(--border-neutral-primary-muted)`, `var(--border-status-negative)`, `var(--surface-neutral-disabled)`)를 반드시 사용하세요.
