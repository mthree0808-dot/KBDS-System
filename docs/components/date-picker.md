# Date Picker (휠 데이트 피커 바텀시트)

모바일 화면 하단에서 슬라이드 업되어 연도와 월을 스크롤/휠 인터랙션으로 선택할 수 있도록 제공하는 바텀시트형 날짜 선택 컴포넌트입니다.  
배경 딤 오버레이와 iOS 시스템 바(상태바 및 홈 인디케이터) 레이아웃 위에서 동작하며, 헤더 타이틀, 닫기 버튼, 2열 휠 피커, 하단 고정 CTA 버튼으로 구성됩니다.

---

## 1. Structure & Layout

* **Canvas Spec:** Width `390px`, Height `844px` (iOS iPhone 기준)
* **Overlay Layer:** Width `390px`, Height `844px`, Background `var(--background-overlay-dimmed, rgba(0, 0, 0, 0.20))`
* **Bottom Sheet Container:**
  * Width: `390px` (Fluid `100%`)
  * Placement: Absolute Bottom (`top: 424px`)
  * Radius: Top-Left/Top-Right `24px`
  * Background: `var(--background-neutral-elevated, #FFFFFF)`
  * Overflow: `hidden`
  * Layout: `flex-direction: column`, `align-items: flex-start`

---

## 2. Component Properties

### 2.1 Bottom Sheet Level

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `title` | Text | String | `"날짜 선택"` | 바텀시트 상단 타이틀 문구 |
| `hasCloseButton` | Boolean | `true`, `false` | `true` | 우측 상단 닫기(X) 버튼 노출 여부 |
| `hasHandle` | Boolean | `true`, `false` | `false` | 상단 드래그 핸들 바 노출 여부 |
| `expanded` | Boolean | `true`, `false` | `false` | 시트 전체 확장 여부 |

### 2.2 Wheel Picker Level

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `columnCount` | Number | `2`, `3` | `2` | 휠 컬럼 수 (기본: 연도 / 월) |
| `selectedYear` | String / Number | String | `"2024년"` | 현재 선택된 연도 |
| `selectedMonth` | String / Number | String | `"10월"` | 현재 선택된 월 |

### 2.3 Bottom CTA Button Level

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `ctaLabel` | Text | String | `"확인"` | 하단 액션 버튼 레이블 |
| `disabled` | Boolean | `true`, `false` | `false` | 버튼 비활성화 상태 여부 |
| `loading` | Boolean | `true`, `false` | `false` | 로딩 인디케이터 노출 여부 |

---

## 3. Sub-Component Specifications

### 3.1 Sheet Header Area (상단 헤더)

* **Container:**
  * Padding: Left/Right `20px`, Bottom `20px` (상단 여백 Padding Top `6px`, Bottom `8px`)
  * Layout: `align-self: stretch`, `flex-direction: column`
* **Title & Action Row:**
  * Layout: `justify-content: flex-start`, `align-items: flex-start`, `gap: 20px`
  * **Title:** 
    * Typography: `KBFG Text`, Bold (`700`), `18px` / `25px`
    * Color: `var(--text-neutral-primary, #111827)`
    * Padding Right: `32px` (닫기 버튼과의 여백 확보)
  * **Close Button (우측 닫기 아이콘):**
    * Size: `24x24px`, Radius `4px`
    * Icon Spec: Bounding `14.61 x 14.61px`, Color `var(--icon-neutral-primary, #111827)`
    * Props: `data-disabled="false"`, `data-pressed="false"`, `data-size="24"`, `data-variant="primary"`

---

### 3.2 Wheel Picker Area (중앙 휠 선택창)

* **Container:**
  * Height: 약 `257px` (아이템 5개 노출 기준)
  * Padding: Left/Right `20px`, Top/Bottom `12px`
  * Position: `relative`, Overflow: `hidden`
* **Wheel Columns (2열 구조: 연도, 월):**
  * Layout: `flex: 1 1 0` 분할 정렬
* **Row Item Spec (행 단위):**
  * **Normal Item (비선택 행):**
    * Padding: Top/Bottom `12px`
    * Typography: `KBFG Text`, Medium (`500`), `16px` / `22px`
    * Color: `var(--text-neutral-placeholder, #9CA3AF)`
  * **Selected Item (현재 선택 행 - 중앙 포커스):**
    * Padding: Top/Bottom `12px`
    * Background: `var(--surface-accent-brand-alt-muted, #F4F6F9)`, Border Radius: `12px`
    * Typography: `KBFG Text`, Bold (`700`), `18px` / `25px`
    * Color: `var(--text-accent-brand-alt, #111827)`
* **Gradient Overlay (상하단 페이드 마스크):**
  * **Top Mask:** Height `40px` (`10px` 솔리드 화이트 + `30px` `linear-gradient(180deg, white 0%, transparent 100%)`)
  * **Bottom Mask:** Height `40px` (`30px` `linear-gradient(180deg, transparent 0%, white 100%)` + `10px` 솔리드 화이트)

---

### 3.3 Bottom CTA Area (하단 고정 버튼)

* **Container:**
  * Padding: Left/Right `20px`, Bottom `8px`
  * Background: `var(--background-neutral-elevated, #FFFFFF)`
* **Confirm Button (확인 버튼):**
  * Min Height: `56px`
  * Padding: Left/Right `12px`, Top/Bottom `2px` (내부 텍스트 패딩: Left/Right `4px`)
  * Background: `var(--surface-accent-brand-alt, #111827)`
  * Border Radius: `16px`
  * Typography: `KBFG Text`, Bold (`700`), `18px` / `25px`
  * Text Color: `var(--text-neutral-primary-on, #FFFFFF)`
  * Props: `data-size="large"`, `data-variant="primary"`

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Component Usage |
| :--- | :--- | :--- | :--- |
| `--background-overlay-dimmed` | `rgba(0, 0, 0, 0.20)` | `background` | 배경 딤 오버레이 채움 |
| `--background-neutral-elevated` | `#FFFFFF` | `background` | 바텀시트 컨테이너 및 하단 CTA 영역 배경 |
| `--surface-accent-brand-alt-muted` | `#F4F6F9` | `background` | 휠 피커 선택된 행(Row) 하이라이트 배경 |
| `--surface-accent-brand-alt` | `#111827` | `background` | 하단 확인(CTA) 버튼 배경 |
| `--text-neutral-primary` | `#111827` | `color` | 바텀시트 헤더 타이틀 문구 |
| `--text-accent-brand-alt` | `#111827` | `color` | 휠 피커 선택된 행 텍스트 (Bold 18px) |
| `--text-neutral-placeholder` | `#9CA3AF` | `color` | 휠 피커 미선택 행 텍스트 (Medium 16px) |
| `--text-neutral-primary-on` | `#FFFFFF` | `color` | 하단 확인 버튼 텍스트 레이블 |
| `--icon-neutral-primary` | `#111827` | `background` / `fill` | 헤더 닫기(X) 아이콘 |

---

## 5. Interaction & Implementation Notes

* **휠 스냅(Wheel Snap) 동작:** 스크롤 종료 시 가장 가까운 연도 및 월 항목이 중앙 하이라이트 박스(`height: 49px`)에 정확히 안착하도록 CSS `scroll-snap-type: y mandatory` 및 자바스크립트 스냅 보정을 적용합니다.
* **배경 스크롤 방지:** 바텀시트가 열려 있는 동안에는 오버레이 뒤편의 메인 바디 스크롤을 차단(`overflow: hidden` 또는 `touch-action: none`)합니다.
* **접근성 (A11y):** 
  * 바텀시트 컨테이너에 `role="dialog"`, `aria-modal="true"`, `aria-labelledby="[타이틀ID]"`를 선언합니다.
  * 휠 피커 영역에 스크린 리더 포커스 진입 시 `role="listbox"` 또는 적절한 피커 롤을 부여하고, 값 변경 시 실시간으로 선택된 날짜 정보를 읽어주도록 구현합니다.
