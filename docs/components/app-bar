# Navigation Bar (Top App Bar)

모바일 화면 상단에 고정되어 현재 뷰의 타이틀을 안내하고 뒤로가기 및 글로벌 유틸리티 액션을 제공하는 헤더 컴포넌트입니다.

---

## 1. Structure & Layout

* **Container Size:** Width `390px` (Fluid `100%`), Height `56px`
* **Padding:** Left/Right `20px`, Top/Bottom `16px`
* **Section Gap:** Left Section과 Right Section 간 간격 `20px`
* **Inner Layout:**
  * **Left (Title/Leading Area):** `flex: 1 1 0` (가변 너비)
  * **Right (Action Area):** `justify-content: flex-end`, `gap: 16px` (고정 간격)

---

## 2. Variants & Properties

### Component Level Properties

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `type` | Variant | `Navigation`, `Main` | `Navigation` | 상단 바 레이아웃 형태 |
| `title` | Text | String | `"타이틀"` | 화면 헤더 타이틀 문구 |
| `showLeftAction` | Boolean | `true`, `false` | `true` | 좌측 탐색 아이콘(Back 또는 Dropdown) 표시 여부 |
| `hasTextButton` | Boolean | `true`, `false` | `false` | 우측 텍스트 버튼 포함 여부 |

---

## 3. Sub-Component Specifications

### 3.1 Left Area (Title & Leading)

#### Navigation Type (서브페이지)
* **Layout:** `align-items: center`, `gap: 8px`
* **Back Button:**
  * Container Size: `28x28px`, Border Radius: `4px`
  * Icon Bounding: `8.51 x 15.75px`
  * Default Props: `data-disabled="false"`, `data-pressed="false"`, `data-size="28"`, `data-variant="primary"`
  * Fill: `var(--icon-neutral-primary, #111827)`
* **Title:**
  * Font Family: `KBFG Text`
  * Font Size / Line Height: `15px` / `21px`
  * Font Weight: `500` (Medium)
  * Text Color: `var(--text-neutral-primary, #111827)`

#### Main Type (메인/홈 화면)
* **Layout:** `align-items: center`, `gap: 2px`
* **Title:**
  * Font Family: `KBFG Text`
  * Font Size / Line Height: `18px` / `25px`
  * Font Weight: `700` (Bold)
  * Text Color: `var(--text-neutral-primary, #111827)`
* **Dropdown Icon:**
  * Container Size: `24x24px`, Border Radius: `4px`
  * Icon Bounding: `7.29 x 13.50px` (Rotate: `180deg`)
  * Default Props: `data-disabled="false"`, `data-pressed="false"`, `data-size="24"`, `data-variant="primary"`
  * Fill: `var(--icon-neutral-primary, #111827)`

---

### 3.2 Right Area (Actions)

* **Layout:** `justify-content: flex-end`, `align-items: center`, `gap: 16px`

#### Icon Buttons (Common Spec)
* **Container:** Size `24x24px`, Border Radius: `4px`
* **State Props:** `data-disabled="false"`, `data-pressed="false"`, `data-size="24"`, `data-variant="primary"`
* **Icon Color:** `var(--icon-neutral-primary, #111827)`
* **Items:**
  * `home`: `18.50 x 19.00px`
  * `alarm`: `18.00 x 19.92px`
  * `menu`: `15.50 x 13.50px`

#### Text Button
* **Container:** Height `24px`, Border Radius: `8px`, Inner Gap: `2px`
* **Props:** `data-size="small"`, `data-variant="primary"`, `data-disabled="false"`, `data-pressed="false"`, `data-loading="false"`, `data-hasprefix="false"`, `data-hassuffix="false"`, `data-underline="false"`
* **Typography:**
  * Font Family: `KBFG Text`
  * Font Size / Line Height: `14px` / `20px`
  * Font Weight: `700` (Bold)
  * Text Color: `var(--text-accent-brand-alt, #111827)`

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Component Usage |
| :--- | :--- | :--- | :--- |
| `--text-neutral-primary` | `#111827` | `color` | Main/Navigation Title |
| `--text-accent-brand-alt` | `#111827` | `color` | Right Text Button Label |
| `--icon-neutral-primary` | `#111827` | `background` / `fill` | Back, Dropdown, Home, Alarm, Menu Icons |
| `--color-util-purple` | `#893DE7` | `border-color` | System Guide Boundary Outline |
