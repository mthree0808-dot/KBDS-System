# Slider & Range Slider (슬라이더 & 레인지 슬라이더)

사용자가 설정된 트랙(Track) 위에서 핸들(Thumb)을 드래그하거나 스텝 버튼, 입력 필드를 통해 수치 또는 범위를 선택할 때 사용하는 폼 컴포넌트입니다.  
단일 값을 조절하는 **Single Slider(단일형)**와 시작/종료 범위를 지정하는 **Range Slider(범위형)**를 지원하며, 상단 툴팁(Tooltip), 스텝 제어 버튼(Stepper), 하단 인풋 필드(Input Field)와의 조합을 제공합니다.

---

## 1. Component Overview & Types

* **Single Slider (`type="single"`):**
  * **Stepper Type (스텝 버튼형):** 트랙 좌우에 감산(`-`) 및 가산(`+`) 버튼이 배치되어 정밀한 단위 조절이 가능하며, 핸들 상단에 실시간 수치 툴팁(예: `100%`)과 트랙 하단에 최소/최대 라벨을 표시합니다.
  * **Input Type (인풋 연동형):** 트랙 하단에 단일 텍스트/수치 입력 필드가 결합되어 직접 타이핑과 슬라이더 드래그를 상호 동기화합니다.
* **Range Slider (`type="range"`):**
  * 2개의 핸들(Start/End Thumb)을 통해 최소-최대 구간 범위를 지정합니다.
  * 하단에 2개의 인풋 필드와 구분자(`-`)가 배치되어 시작값과 종료값을 각각 입력 및 제어할 수 있습니다.

---

## 2. Component Properties

### 2.1 Header / Group Level

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `title` | Text | String | `"타이틀입니다"` | 그룹 타이틀 문구 |
| `required` | Boolean | `true`, `false` | `true` | `(필수)` 표기 노출 여부 |
| `hasTooltip` | Boolean | `true`, `false` | `true` | 타이틀 우측 정보 안내 툴팁 아이콘 노출 여부 |
| `hasSuffix` | Boolean | `true`, `false` | `false` | 타이틀 우측 추가 텍스트/액션 포함 여부 |

### 2.2 Slider Control Level

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `type` | Variant | `single`, `range` | `single` | 단일 값 조절 vs 범위 구간 조절 |
| `hasStepper` | Boolean | `true`, `false` | `false` | 좌우 증감(`-`, `+`) 버튼 포함 여부 |
| `hasThumbTooltip`| Boolean | `true`, `false` | `false` | 핸들 상단 수치 말풍선(Tooltip) 노출 여부 |
| `hasInputField` | Boolean | `true`, `false` | `false` | 하단 입력 폼 결합 여부 |
| `disabled` | Boolean | `true`, `false` | `false` | 슬라이더 전체 비활성화 여부 |
| `min` | Number | Number | `0` | 슬라이더 최소값 |
| `max` | Number | Number | `100` | 슬라이더 최대값 |
| `value` | Number / Array | Number / `[start, end]` | `0` | 현재 선택된 값 또는 범위 |

---

## 3. Sub-Component Specifications

### 3.1 Header Area (라벨 & 메타)

* **Layout:** Width `350px` (Inner Padding Left/Right `6px`), Gap `8px`
* **Title:** `KBFG Text`, Bold (`700`), `14px` / `20px`, Color `var(--text-neutral-primary, #111827)`
* **Required Tag (`(필수)`):** `KBFG Text`, Medium (`500`), `11px` / `15px`, Color `var(--text-accent-red, #E53838)`
* **Tooltip Button:** Size `16x16px`, Radius `4px`, Icon Bounding `12x12px`, Color `var(--icon-neutral-quaternary, #9CA3AF)`

---

### 3.2 Track & Thumb Area (슬라이더 본체)

* **Control Row:** Height `32px`, Padding Top/Bottom `12px`, `justify-content: space-between`, `align-items: center`
* **Rail (전체 배경 트랙):**
  * Height: `8px`, Border Radius: `9999px`
  * Width: `274px` (Stepper 포함 시) 또는 `338px` (기본형)
  * Background: `var(--surface-neutral-primary-muted, #ECEEF2)`
* **Bar (활성 진행 트랙):**
  * Height: `8px`, Border Radius: `9999px`, Position: `relative`
  * Background: `var(--surface-neutral-primary, #111827)`
* **Thumb (조절 핸들):**
  * Size: `24x24px`, Border Radius: `9999px`
  * Background: `var(--surface-neutral-quaternary-muted, white)`
  * Border: `6px solid var(--border-accent-brand-alt, #111827)`
  * Box Shadow: `0px 4px 16px rgba(12, 17, 29, 0.10)`
* **Thumb Tooltip (실시간 수치 말풍선):**
  * Height: `22px`, Max Width: `44px`, Padding: Top/Bottom `2px`, Left/Right `4px`
  * Background: `var(--surface-neutral-primary, #111827)`, Border Radius: `8px`
  * Placement: 핸들 상단 고정 (`top: -36px`)
  * Typography: `KBFG Text`, Bold (`700`) + Medium (`500`) (단위 `%`), `13px` / `18px`, Color `var(--text-neutral-primary-on, white)`

---

### 3.3 Stepper Buttons (좌우 증감 버튼)

* **Container:** 
  * Padding: `8px`, Border Radius: `6px`, Outline: `1px solid var(--border-neutral-primary-muted, #D1D5DB)` (Offset `-1px`)
  * Background: `var(--surface-neutral-quaternary-muted, white)`
  * Box Shadow: `0px 2px 4px -1px rgba(12, 17, 29, 0.10)`
* **Icon Spec:**
  * Container Size: `16x16px`
  * Color: `var(--icon-neutral-primary, #111827)`
  * Minus Icon (`-`): Width `10.33px`, Height `1px`
  * Plus Icon (`+`): Width `10.33px`, Height `10.33px`

---

### 3.4 Linked Input Field Area (하단 입력창 연동)

* **Single Type Input:**
  * Width: `350px`, Min Height: `56px`, Padding: `16px`, Border Radius: `12px`
  * Outline: `1px solid var(--border-neutral-primary-muted, #D1D5DB)` (Offset `-1px`)
  * Text / Placeholder: `KBFG Text`, Medium (`500`), `16px` / `22px`, Color `var(--text-neutral-placeholder, #9CA3AF)`
* **Range Type Input (듀얼 인풋 & 디바이더):**
  * Layout: `width: 350px`, `justify-content: center`, `align-items: center`, `gap: 4px`
  * Input Boxes: 좌우 각 `flex: 1 1 0` (스펙 동일)
  * Range Separator (`-`): `KBFG Text`, Bold (`700`), `17px` / `24px`, Color `var(--text-neutral-quaternary, #6B7280)`

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Component Usage |
| :--- | :--- | :--- | :--- |
| `--surface-neutral-primary` | `#111827` | `background` | 슬라이더 활성 게이지 바, Thumb 수치 말풍선 |
| `--surface-neutral-primary-muted` | `#ECEEF2` | `background` | 슬라이더 배경 트랙(Rail) |
| `--surface-neutral-quaternary-muted` | `#FFFFFF` | `background` | Thumb 중심부, 스텝 증감 버튼 배경 |
| `--border-accent-brand-alt` | `#111827` | `border-color` | Thumb 외곽 원형 보더 (두께 `6px`) |
| `--border-neutral-primary-muted` | `#D1D5DB` | `outline-color` | 스텝 증감 버튼 및 하단 인풋 필드 아웃라인 |
| `--text-neutral-primary` | `#111827` | `color` | 라벨 헤더 타이틀 문구 |
| `--text-neutral-primary-on` | `#FFFFFF` | `color` | Thumb 상단 툴팁 수치 텍스트 |
| `--text-neutral-quaternary` | `#6B7280` | `color` | 트랙 하단 최소/최대 라벨, 범위 구분자(`-`) |
| `--text-neutral-placeholder` | `#9CA3AF` | `color` | 인풋 필드 플레이스홀더 문구 |
| `--text-accent-red` | `#E53838` | `color` | 헤더 `(필수)` 표기 문구 |
| `--icon-neutral-primary` | `#111827` | `background` | 스텝 감산/가산(`-`, `+`) 아이콘 |
| `--icon-neutral-quaternary` | `#9CA3AF` | `background` | 헤더 툴팁 아이콘 |
| `--color-util-purple` | `#893DE7` | `border-color` | 가이드 영역 아웃라인 |

---

## 5. Interaction & Implementation Notes

* **양방향 동기화 (Two-way Binding):** 슬라이더 드래그 시 하단 인풋 필드의 수치가 실시간 반영되어야 하며, 반대로 인풋 필드에 숫자를 직접 입력/수정 시 슬라이더 핸들의 위치와 트랙 채움 비율이 즉시 갱신되어야 합니다.
* **Range 교차 방지 (Collision Prevention):** Range 타입의 경우 `startValue`가 `endValue`를 초과할 수 없도록 핸들 이동 범위를 상호 제한합니다.
* **접근성 (A11y):** 
  * Thumb 요소에 `role="slider"`, `aria-valuemin={min}`, `aria-valuemax={max}`, `aria-valuenow={value}`를 선언합니다.
  * Range 타입인 경우 각각 `aria-label="시작 값"`, `aria-label="종료 값"`으로 구분합니다.
