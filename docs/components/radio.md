# Radio (라디오 버튼)

단일 선택 그룹에서 사용자가 여러 옵션 중 오직 하나의 항목만 선택할 수 있도록 제공하는 컴포넌트입니다.  
원형(Border Radius `9999px`) 인디케이터 심볼과 우측 텍스트 영역(레이블 및 디스크립션)으로 구성되며, 선택 여부(`checked`), 유효성 검증(`invalid`), 비활성화(`disabled`) 상태를 지원합니다.

---

## 1. Structure & Layout

* **Container:** `display: inline-flex`, `align-items: center`, `gap: 8px`
* **Layout Structure:**
  * **Radio Symbol (Leading):** 원형 선택 인디케이터 컨테이너
  * **Label / Description Area:** `flex-direction: column`, `align-items: flex-start`

---

## 2. Component Properties

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `checked` | Boolean | `true`, `false` | `false` | 선택 활성화 여부 |
| `disabled` | Boolean | `true`, `false` | `false` | 사용자 인터랙션 비활성화 여부 |
| `invalid` | Boolean | `true`, `false` | `false` | 유효성 검증 오류 상태 |
| `label` | Text | String | `"레이블"` | 주 타이틀 문구 |
| `description` | Text | String | `"디스크립션"` | 보조 설명 문구 |

---

## 3. Sub-Component Specifications

### 3.1 Radio Symbol (원형 인디케이터)

* **Outer Container:**
  * Size: Width `24px`, Height `24px`
  * Radius: `9999px` (Full Round)
  * Position: `relative`
* **Inner Circle:**
  * Size: Width `20px`, Height `20px`
  * Position: `absolute`, Left `2px`, Top `2px`
  * Radius: `9999px`
* **States (제공된 코드 기준 - Disabled Unchecked):**
  * Props: `data-checked="false"`, `data-disabled="true"`, `data-invalid="false"`
  * Background: `var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10))`

---

### 3.2 Text Area (레이블 & 디스크립션)

* **Layout:** `display: inline-flex`, `flex-direction: column`, `align-items: flex-start`
* **Label (타이틀):**
  * Typography: `KBFG Text`, Medium (`500`), `14px` / `20px`
  * Color: `var(--text-neutral-disabled, #9CA3AF)`
  * Style: `wordWrap: break-word`
* **Description (보조 설명):**
  * Typography: `KBFG Text`, Light (`300`), `13px` / `18px`
  * Color: `var(--text-neutral-disabled, #9CA3AF)`
  * Style: `wordWrap: break-word`

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Component Usage |
| :--- | :--- | :--- | :--- |
| `--surface-neutral-disabled` | `rgba(102, 112, 133, 0.10)` | `background` | 비활성화(Disabled) 상태의 라디오 심볼 배경 |
| `--text-neutral-disabled` | `#9CA3AF` | `color` | 비활성화(Disabled) 상태의 레이블 및 디스크립션 텍스트 |

---

## 5. Usage & Accessibility Rules

* **그룹핑 규칙:** 항상 2개 이상의 항목을 하나의 라디오 그룹으로 묶어 사용해야 하며, 그룹 내 항목들은 동일한 `name` 어트리뷰트를 공유합니다.
* **터치 영역 확장:** 원형 심볼 영역뿐 아니라 우측 텍스트 영역 전체를 탭해도 라디오 버튼이 선택되도록 구현합니다.
* **접근성 (A11y):** 
  * 표준 `<input type="radio" />` 마크업을 기반으로 감싸거나, 상위 컨테이너에 `role="radiogroup"`, 개별 항목에 `role="radio"`, `aria-checked={checked}`, `aria-disabled={disabled}` 속성을 부여합니다.
