# Component: Form / CenterInput

본 문서는 금액 송금 및 보안 PIN/인증번호 입력 화면에서 중앙 집중형으로 사용되는 `CenterInput` 명세입니다.
대형 수치 중심의 `amount` 타입과 도트/박스 PIN 형태의 `password` 타입을 단일 명세로 통합 지원하며, 상태별 토큰 바인딩 매트릭스를 정의합니다.

---

## 1. 컴포넌트 구조 (Hierarchy)

CenterInput은 수직 방향(Auto Layout Vertical)의 중앙 집중형 2단 레이아웃 구조를 갖습니다.

```text
[CenterInput Container] (Width: 390px / Fill container)
  ├── 1. Primary Display Area (수치 타이포그래피 또는 PIN 도트/박스 인디케이터)
  └── 2. Helper & Feedback Area (출금가능금액/한도제한 뱃지, 한글 환산 표기, 에러/안내 메시지)
```

---

## 2. 속성 (Properties & Variants)

| Property | Type | Options | Default | 설명 |
|---|---|---|---|---|
| `type` | String | `amount`, `password` | `amount` | 금액 입력형 vs 패스워드/PIN 입력형 |
| `state` | String | `placeholder`, `focused`, `entered`, `error` | `placeholder` | 인터랙션 상태 |
| `pinLength` | Number | `4`, `6`, `7` | `6` | password 타입의 입력 자릿수 |
| `pinStyle` | String | `dot`, `box`, `mixed` | `dot` | password 인디케이터 스타일 (원형 도트 / 사각 박스 / 혼합형) |
| `hasBadge` | Boolean | `true`, `false` | `false` | 피드백 영역 내 뱃지 노출 여부 (한도제한 등) |

---

## 3. 상세 레이아웃 스펙

### 1. Amount Type (금액 입력형)
* **Container:** Width `390px` (`Fill container`), Padding Top/Bottom `16px` (`$spacing.spacingXl`), Left/Right `20px` (`$spacing.spacing2xl`)
* **Vertical Gap:** `12px` (`$spacing.spacingLg`)
* **Align:** Horizontal/Vertical Center 정렬
* **Primary Display Area (입력 금액):**
  * Placeholder: `"얼마를 보낼까요?"`, Typography `KBFG Text`, Size `32px` (`$type.fontSizeDisplay5xl`), Weight `700` (`$type.fontWeightBold`), Line Height `45px`
  * Value Text (Focused / Entered): Typography `Pretendard`, Size `38px` (`$type.fontSizeDisplay6xl`), Weight `600` (`$type.fontWeightSemibold`), Line Height `53px`
  * Caret (Focused 시): Width `1.6px`, Height `45px`, Color `var(--icon-accent-brand-alt)` (`#111827`)
  * Unit (`"원"`): Typography `KBFG Text`, Size `26px` (`$type.fontSizeDisplay4xl`), Weight `500` (`$type.fontWeightMedium`), Line Height `36px`
* **Helper & Feedback Area:**
  * 출금가능금액 정보 (Placeholder):
    * 라벨: `"출금가능금액"`, `KBFG Text`, Size `13px`, Weight `300`, Color `var(--text-neutral-quaternary)` (`#6b7280`)
    * 수치: `"3,000,000원"`, `KBFG Text`, Size `13px`, Weight `500`, Color `var(--text-neutral-quaternary)`
    * 한도제한 뱃지: Height `20px`, Padding Horizontal `6px` (`$spacing.spacingSm`), Radius `4px` (`$radius.radius3xs`), Background `var(--surface-accent-red-muted)` (`#fff6f5`), Text `"한도제한"` (`11px`, Bold, `var(--text-accent-red)`)
  * 한글 환산 금액 표기 (Focused / Entered):
    * Text: `"240원"`, `"240만원"`, Typography `KBFG Text`, Size `13px`, Weight `500`, Color `var(--text-neutral-quaternary)` (`#6b7280`)
  * 에러 메시지 (Error):
    * Icon: `12px x 12px` (Vector: `9px x 9px`), Color `var(--icon-status-negative)` (`#e53838`)
    * Typography: `KBFG Text`, Size `13px`, Weight `500`, Color `var(--text-status-negative)` (`#e53838`)

---

### 2. Password Type (PIN / 패스워드 입력형)
* **Container:** Width `390px` (`Fill container`), Padding Top/Bottom `28px` (`$spacing.spacing4xl`), Left/Right `20px` (`$spacing.spacing2xl`)
* **Vertical Gap:** `20px` (`$spacing.spacing2xl`)
* **Align:** Horizontal/Vertical Center 정렬, Flex-Wrap 대응
* **Primary Display Area (PIN 인디케이터):**
  * Indicator Item Gap: `8px` (`$spacing.spacingMd`)
  * Dot Style (원형 도트):
    * Size: `16px x 16px`, Radius `9999px` (`$radius.radiusFull`), Padding `2px`
    * Disabled / Empty: Background `var(--surface-neutral-disabled)` (10%), Border `1px solid var(--border-neutral-disabled)` (`#d1d5db`)
    * Entered: Background `var(--icon-neutral-primary)` (`#111827`), Border None
    * Error: Background `var(--icon-status-negative)` (`#e53838`), Border None
  * Box Style (사각 넘버 박스):
    * Dimensions: Width `48px`, Height `56px`, Radius `12px` (`$radius.radiusMd`)
    * Empty: Background `var(--surface-neutral-secondary-muted)` (`#f4f6f9`), Border `1px solid var(--border-neutral-primary-muted)` (`#d1d5db`)
    * Active Focused (현재 입력칸): Background `var(--surface-neutral-quaternary-muted)` (`#ffffff`), Border `3px solid var(--border-accent-brand-alt)` (`#111827`), Box Shadow `0px 4px 6px rgba(12, 17, 29, 0.10)`
    * Entered: Typography `Pretendard`, Size `22px` (`$type.fontSizeTitle3xl`), Weight `600`, Color `var(--text-neutral-primary)` (`#111827`)
    * Error: Background `var(--surface-status-negative-muted)` (`#fff6f5`), Border `1px solid var(--border-status-negative-muted)` (`#ffbdbd`), Text Color `var(--text-status-negative)` (`#e53838`)
* **Helper & Feedback Area:**
  * 안내 메시지 (Normal):
    * Typography: `KBFG Text`, Size `13px`, Weight `300`, Color `var(--text-neutral-quaternary)` (`#6b7280`)
  * 에러 메시지 (Error):
    * Icon: `12px x 12px`, Color `var(--icon-status-negative)` (`#e53838`)
    * Typography: `KBFG Text`, Size `13px`, Weight `500`, Color `var(--text-status-negative)` (`#e53838`)

---

## 4. 토큰 바인딩 종합 (Token Mapping Matrix)

| 구분 (Type) | UI 요소 (Element) | Placeholder / Empty | Focused | Entered | Error |
|---|---|---|---|---|---|
| **Amount** | 입력 금액 텍스트 | `var(--text-neutral-secondary-on)` | `var(--text-neutral-primary)` | `var(--text-neutral-primary)` | `var(--text-status-negative)` |
| | 단위 접미사 ('원') | - | - | `var(--text-neutral-primary)` | `var(--text-status-negative)` |
| | 입력 커서 (Caret) | - | `var(--icon-accent-brand-alt)` | - | - |
| | 서브 환산 / 안내 텍스트 | `var(--text-neutral-quaternary)` | `var(--text-neutral-quaternary)` | `var(--text-neutral-quaternary)` | `var(--text-status-negative)` |
| | 에러 아이콘 | - | - | - | `var(--icon-status-negative)` |
| | 한도제한 뱃지 배경/텍스트 | `var(--surface-accent-red-muted)` / `var(--text-accent-red)` | - | - | - |
| **Password** | 원형 도트 (Dot) | `var(--surface-neutral-disabled)` (Border: `var(--border-neutral-disabled)`) | - | `var(--icon-neutral-primary)` | `var(--icon-status-negative)` |
| | 사각 박스 (Box) 배경 | `var(--surface-neutral-secondary-muted)` | `var(--surface-neutral-quaternary-muted)` | `var(--surface-neutral-secondary-muted)` | `var(--surface-status-negative-muted)` |
| | 사각 박스 (Box) 테두리 | `1px var(--border-neutral-primary-muted)` | `3px var(--border-accent-brand-alt)` | `1px var(--border-neutral-primary-muted)` | `1px var(--border-status-negative-muted)` |
| | 사각 박스 (Box) 숫자 | - | - | `var(--text-neutral-primary)` | `var(--text-status-negative)` |
| | 하단 안내 / 에러 텍스트 | `var(--text-neutral-quaternary)` | `var(--text-neutral-quaternary)` | `var(--text-neutral-quaternary)` | `var(--text-status-negative)` |

---

## 5. AI UI 생성 규칙 (Generation Rules)

1. **송금 입력 화면 구성 시:**  
   `type: 'amount'`를 배치하고, 키패드 연동 입력 시 실시간으로 입력값 하단에 한글 환산 표기(`240만원` 등)를 자동 갱신하도록 처리하세요.
2. **비밀번호/생체인증 PIN 화면 구성 시:**  
   `type: 'password'`를 배치하고, 금융 간편비밀번호(6자리)는 기본 `pinStyle: 'dot'`, 주민번호/보안카드형은 `pinStyle: 'mixed'` 또는 `'box'`를 적용하세요.
3. **숫자 타이포그래피 원칙:**  
   금액 수치 및 박스 내부 입력 숫자는 반드시 `fontFamilyNumeric`(`Pretendard`)을 우선 바인딩하세요.
