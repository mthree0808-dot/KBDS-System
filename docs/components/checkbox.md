# Checkbox & Checkmark (체크박스 & 체크마크)

다중 선택 목록, 약관 동의, 설정 토글 등에 사용하는 선택 제어 컴포넌트입니다.  
사각 박스 형태의 **Checkbox(기본 박스형)**와 박스 없이 체크 심볼 단독으로 노출되는 **Checkmark(미니멀형)** 두 가지 시각적 타입을 제공하며, 크기(Large, Medium) 및 텍스트 굵기(Bold, Medium), 유효성 검증(Invalid/Error), 비활성화(Disabled) 상태를 지원합니다.

---

## 1. Component Overview & Types

* **Checkbox (`type="checkbox"`):** 
  * 외곽선 박스 및 채움 배경을 기반으로 명확한 터치 타깃과 선택 여부를 안내하는 표준 형태입니다.
  * 전체 선택 시 하위 항목 일부 선택을 나타내는 **Indeterminate(부분 선택/- 기호)** 상태를 지원합니다.
* **Checkmark (`type="checkmark"`):**
  * 배경 박스 없이 체크/대시 아이콘 자체의 컬러 변화로 상태를 나타내는 경량화 형태입니다.
  * 복잡한 리스트 아이템이나 간결한 레이아웃에 적용합니다.

---

## 2. Component Properties

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `type` | Variant | `checkbox`, `checkmark` | `checkbox` | 심볼 렌더링 스타일 (박스형 vs 아이콘 단독형) |
| `size` | Variant | `large` (16px), `medium` (14px) | `large` | 텍스트 레이블 및 디스크립션 스케일 |
| `checked` | Boolean | `true`, `false` | `false` | 선택 활성화 여부 |
| `indeterminate` | Boolean | `true`, `false` | `false` | 부분 선택 상태 여부 (`-` 기호 노출) |
| `invalid` | Boolean | `true`, `false` | `false` | 유효성 검증 오류 상태 (Red 강조) |
| `disabled` | Boolean | `true`, `false` | `false` | 사용자 인터랙션 비활성화 여부 |
| `labelWeight` | Variant | `bold` (700), `medium` (500) | `bold` | 레이블 타이틀 폰트 굵기 |
| `label` | Text | String | `"레이블"` | 주 타이틀 문구 |
| `description` | Text | String | `"디스크립션"` | 보조 설명 문구 |

---

## 3. Sub-Component Specifications

### 3.1 Control Icon (좌측 선택 심볼)

* **Outer Container:** Width `24px`, Height `24px`, Border Radius `8px`
* **Inner Box:** Width `20px`, Height `20px`, Absolute Left/Top `2px`, Border Radius `6px`
* **Icon Graphics:**
  * Check Icon: Bounding 약 `12.36~13.21 x 9.63~11.05px`
  * Indeterminate Line: Width `12.14px`, Height `2.14px`, Left `3.93px`, Top `8.93px`

#### A. Type: `checkbox` 상태별 스타일
| State | Checked / Indeterminate | Disabled | Invalid | Background | Border / Outline | Icon Fill |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Unchecked** | `false` | `false` | `false` | `transparent` | `1px solid var(--border-neutral-quaternary, #9CA3AF)` | `var(--icon-accent-brand-alt, #111827)` (10% Opacity) |
| **Checked** | `true` | `false` | `false` | `var(--surface-accent-brand-alt, #111827)` | None | `var(--icon-neutral-primary-on, #FFFFFF)` |
| **Indeterminate** | `true` (Line) | `false` | `false` | `var(--surface-accent-brand-alt, #111827)` | None | `var(--icon-neutral-primary-on, #FFFFFF)` |
| **Invalid (Unchecked)**| `false` | `false` | `true` | `transparent` | `1px solid var(--border-status-negative, #E53838)` | `var(--icon-status-negative, #E53838)` (10% Opacity) |
| **Invalid (Checked)** | `true` | `false` | `true` | `var(--surface-status-negative, #E53838)` | `1px solid var(--border-status-negative, #E53838)` | `var(--icon-neutral-primary-on, #FFFFFF)` |
| **Invalid (Indeter.)** | `true` (Line) | `false` | `true` | `var(--surface-status-negative, #E53838)` | `1px solid var(--border-status-negative, #E53838)` | `var(--icon-neutral-primary-on, #FFFFFF)` |
| **Disabled (Unchecked)**| `false`| `true` | `false` | `var(--surface-neutral-disabled, rgba(102,112,133,0.10))` | None | None |
| **Disabled (Checked)** | `true` | `true` | `false` | `var(--surface-neutral-disabled, rgba(102,112,133,0.10))` | None | `var(--icon-neutral-disabled, #D1D5DB)` |
| **Disabled (Indeter.)**| `true` (Line) | `true` | `false` | `var(--surface-neutral-disabled, rgba(102,112,133,0.10))` | None | `var(--icon-neutral-disabled, #D1D5DB)` |

#### B. Type: `checkmark` 상태별 스타일
| State | Checked / Indeterminate | Disabled | Invalid | Background | Icon Fill |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Unchecked** | `false` | `false` | `false` | `transparent` | `var(--icon-neutral-quaternary, #9CA3AF)` |
| **Checked** | `true` | `false` | `false` | `transparent` | `var(--border-accent-brand-alt, #111827)` |
| **Indeterminate** | `true` (Line) | `false` | `false` | `transparent` | `var(--icon-accent-brand-alt, #111827)` |
| **Invalid (Checked)** | `true` | `false` | `true` | `transparent` | `var(--icon-status-negative, #E53838)` |
| **Invalid (Indeter.)** | `true` (Line) | `false` | `true` | `transparent` | `var(--icon-status-negative, #E53838)` |
| **Disabled (Unchecked)**| `false`| `true` | `false` | `transparent` | `var(--icon-neutral-disabled, #D1D5DB)` |
| **Disabled (Checked)** | `true` | `true` | `false` | `transparent` | `var(--icon-neutral-quaternary, #9CA3AF)` |
| **Disabled (Indeter.)**| `true` (Line) | `true` | `false` | `transparent` | `var(--icon-neutral-quaternary, #9CA3AF)` |

---

### 3.2 Label & Description Area (우측 텍스트 영역)

* **Layout:** `flex-direction: column`, `align-items: flex-start`
* **Typography:** `KBFG Text`, `wordWrap: break-word`

#### A. Large Size (`size="large"`)
* **Vertical Gap:** `4px`
* **Label (타이틀):** 
  * Font Size / Line Height: `16px` / `22px`
  * Weight: `700` (Bold) 또는 `500` (Medium)
* **Description (설명):** 
  * Font Size / Line Height: `14px` / `20px`
  * Weight: `300` (Light)

#### B. Medium Size (`size="medium"`)
* **Vertical Gap:** `0px` (인라인 결합)
* **Label (타이틀):** 
  * Font Size / Line Height: `14px` / `20px`
  * Weight: `700` (Bold) 또는 `500` (Medium)
* **Description (설명):** 
  * Font Size / Line Height: `13px` / `18px`
  * Weight: `300` (Light)

#### C. Text Colors by Status
* **Normal (Default / Checked):**
  * Label: `var(--text-neutral-secondary, #374151)`
  * Description: `var(--text-neutral-quaternary, #6B7280)`
* **Invalid (Error):**
  * Label: `var(--text-status-negative, #E53838)`
  * Description: `var(--text-neutral-quaternary, #6B7280)`
* **Disabled:**
  * Label: `var(--text-neutral-disabled, #9CA3AF)`
  * Description: `var(--text-neutral-disabled, #9CA3AF)`

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Component Usage |
| :--- | :--- | :--- | :--- |
| `--surface-accent-brand-alt` | `#111827` | `background` | Checkbox 활성 체크 및 부분 선택 채움 배경 |
| `--surface-status-negative` | `#E53838` | `background` | Checkbox 오류 활성 체크 채움 배경 |
| `--surface-neutral-disabled` | `rgba(102, 112, 133, 0.10)` | `background` | Checkbox 비활성화 박스 배경 |
| `--border-neutral-quaternary` | `#9CA3AF` | `outline-color` | Checkbox 미선택 기본 보더 |
| `--border-status-negative` | `#E53838` | `outline-color` | Checkbox 오류 상태 보더 |
| `--border-accent-brand-alt` | `#111827` | `background` | Checkmark 활성 체크 심볼 |
| `--icon-neutral-primary-on` | `#FFFFFF` | `background` | Checkbox 활성 체크 및 인디터미네이트 라인 |
| `--icon-neutral-quaternary` | `#9CA3AF` | `background` | Checkmark 미선택 심볼 및 비활성 체크 심볼 |
| `--icon-neutral-disabled` | `#D1D5DB` | `background` | 비활성화 상태 내부 체크/대시 심볼 |
| `--icon-status-negative` | `#E53838` | `background` | 오류 상태 심볼 |
| `--text-neutral-secondary` | `#374151` | `color` | 정상 상태 메인 레이블 |
| `--text-neutral-quaternary` | `#6B7280` | `color` | 정상 상태 디스크립션 문구 |
| `--text-status-negative` | `#E53838` | `color` | 오류 상태 메인 레이블 |
| `--text-neutral-disabled` | `#9CA3AF` | `color` | 비활성화 상태 레이블 및 디스크립션 문구 |

---

## 5. Interaction & Implementation Notes

* **터치 영역 확장:** 시각적 심볼은 `20x20px`이지만 터치 타깃은 최소 `24x24px` 이상을 유지하며, 우측 텍스트 영역 전체를 클릭/탭해도 선택 토글이 발생하도록 구현합니다.
* **접근성 (A11y):** 
  * 네이티브 `<input type="checkbox" />`를 기반으로 마크업을 구성하고 시각 요소를 오버레이합니다.
  * `aria-checked` 속성에 `true`, `false`, `"mixed"` (Indeterminate) 상태를 바인딩합니다.
  * `invalid="true"`인 경우 `aria-invalid="true"`를 부여합니다.
