# Chips (필터 칩 / 칩 그룹)

콘텐츠 목록의 필터링, 정렬 기준 선택, 태그 지정 등에 사용하는 캡슐형 칩(Chip) 컴포넌트 세트입니다.  
선택된 시각적 스타일에 따라 **Solid Fill(단색 채움형)**과 **Outline(외곽선 강조형)** 방식을 제공하며, 레이아웃에 따라 **가로 스크롤형(Horizontal Scroll with Fade Mask)**과 **전체 펼침형(Multi-line Wrap)**을 지원합니다.

---

## 1. Component Overview & Modes

* **Visual Variant:**
  * **Solid Fill Type:** 
    * 선택 시 다크 배경(`var(--surface-accent-brand-alt, #111827)`)과 반전 텍스트로 강한 시각적 대비를 제공합니다.
    * 미선택 시 연회색 배경(`var(--background-neutral-light-gray, #F9FAFB)`)과 `1px` 보더가 적용됩니다.
  * **Outline Type:** 
    * 투명 배경을 유지하며, 선택 시 두께 `1.60px`의 브랜드 아웃라인(`var(--border-accent-brand-alt, #111827)`)으로 선택 여부를 표시합니다.
    * 미선택 시 투명 배경에 `1px` 뉴트럴 보더(`var(--border-neutral-secondary-muted, #E5E7EB)`)가 적용됩니다.
* **Layout Mode:**
  * **Scrollable (단일 행 가로 스크롤):**
    * 높이 `68px`의 고정 컨테이너 내에서 칩들이 한 줄로 나열됩니다.
    * 우측 끝에 페이드 그라데이션 마스크와 더보기/펼침 토글 화살표(하단 회전 아이콘)를 제공합니다.
  * **Expanded / Wrap (다중 행 전체 펼침):**
    * `flex-wrap: wrap`을 통해 전체 칩 항목을 그리드로 펼쳐 보여주며, 우측에 접기 토글 화살표(상단 회전 아이콘)가 배치됩니다.

---

## 2. Component Properties

### 2.1 Chip Group Container Level

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `styleVariant` | Variant | `solid`, `outline` | `solid` | 칩의 선택 시각화 방식 (채움형 vs 외곽선형) |
| `expanded` | Boolean | `true`, `false` | `false` | 가로 스크롤 상태 vs 다중 행 전체 펼침 상태 |
| `showToggleButton` | Boolean | `true`, `false` | `true` | 우측 펼침/접기 화살표 버튼 노출 여부 |

### 2.2 Chip Item Level

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `selected` | Boolean | `true`, `false` | `false` | 칩 활성화/선택 여부 |
| `label` | Text | String | `"텍스트"` | 칩 내부 텍스트 문구 |
| `hasIcon` | Boolean | `true`, `false` | `false` | 프리픽스 아이콘 포함 여부 |
| `hasNumber` | Boolean | `true`, `false` | `false` | 카운트/수치 표시 여부 |
| `hasDotBadge` | Boolean | `true`, `false` | `false` | 상태 알림 도트 뱃지 포함 여부 |

---

## 3. Sub-Component Specifications

### 3.1 Chip Item (개별 칩 스펙)

* **Common Box Model:**
  * Min Height: `36px`
  * Padding: Left/Right `12px` (내부 텍스트 패딩 Left/Right `4px`, Inner Gap `4px`)
  * Border Radius: `9999px` (Full Round)
  * Overflow: `hidden`

#### A. Solid Fill Type (`styleVariant="solid"`)
* **Selected (`selected="true"`):**
  * Background: `var(--surface-accent-brand-alt, #111827)`
  * Outline / Border: None
  * Typography: `KBFG Text`, Bold (`700`), `14px` / `20px`
  * Text Color: `var(--text-neutral-primary-on, #FFFFFF)`
* **Unselected (`selected="false"`):**
  * Background: `var(--background-neutral-light-gray, #F9FAFB)`
  * Outline: `1px solid var(--border-neutral-secondary-muted, #E5E7EB)` (Offset: `-1px`)
  * Typography: `KBFG Text`, Medium (`500`), `14px` / `20px`
  * Text Color: `var(--text-neutral-secondary, #374151)`

#### B. Outline Type (`styleVariant="outline"`)
* **Selected (`selected="true"`):**
  * Background: `transparent`
  * Outline: `1.60px solid var(--border-accent-brand-alt, #111827)` (Offset: `-1.60px`)
  * Typography: `KBFG Text`, Bold (`700`), `14px` / `20px`
  * Text Color: `var(--text-neutral-primary, #111827)`
* **Unselected (`selected="false"`):**
  * Background: `transparent`
  * Outline: `1px solid var(--border-neutral-secondary-muted, #E5E7EB)` (Offset: `-1px`)
  * Typography: `KBFG Text`, Medium (`500`), `14px` / `20px`
  * Text Color: `var(--text-neutral-secondary, #374151)`

---

### 3.2 Container & Toggle Button

* **Container Area:**
  * Width: `390px` (Fluid `100%`)
  * Padding: Top/Bottom `16px`, Left/Right `20px`, Gap `8px`
* **Scroll Mask Gradient (`expanded="false"`):**
  * Size: Width `390px`, Height `68px`
  * Background: `linear-gradient(90deg, white 83%, rgba(255, 255, 255, 0) 91%)`
* **Toggle Button (우측 펼침/접기 액션):**
  * Container Size: `32x32px` (Padding Left `12px`, Right `16px`)
  * Icon Bounding: `9.72 x 18.00px`, Color `var(--icon-neutral-primary, #111827)`
  * **Scrollable 상태:** `transform: rotate(-90deg)` (아래 방향 화살표 토글)
  * **Expanded 상태:** `transform: rotate(90deg)` (위 방향 화살표 토글)

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Component Usage |
| :--- | :--- | :--- | :--- |
| `--surface-accent-brand-alt` | `#111827` | `background` | Solid 타입 선택 칩 배경 채움 |
| `--background-neutral-light-gray` | `#F9FAFB` | `background` | Solid 타입 미선택 칩 배경 채움 |
| `--border-accent-brand-alt` | `#111827` | `outline-color` | Outline 타입 선택 칩 테두리 (`1.60px`) |
| `--border-neutral-secondary-muted`| `#E5E7EB` | `outline-color` | 미선택 칩 기본 외곽선 테두리 (`1px`) |
| `--text-neutral-primary-on` | `#FFFFFF` | `color` | Solid 타입 선택 칩 텍스트 레이블 |
| `--text-neutral-primary` | `#111827` | `color` | Outline 타입 선택 칩 텍스트 레이블 |
| `--text-neutral-secondary` | `#374151` | `color` | 미선택 칩 텍스트 레이블 |
| `--icon-neutral-primary` | `#111827` | `background` | 우측 펼침/접기 토글 화살표 아이콘 |
| `--color-util-purple` | `#893DE7` | `border-color` | 가이드 영역 아웃라인 |

---

## 5. Interaction & Usability Rules

* **스크롤 및 페이드 마스크 연동:** 가로 스크롤 상태(`expanded="false"`)에서 칩 목록이 화면 폭을 초과할 경우 우측 텍스트 잘림을 부드럽게 감추기 위해 페이드 마스크 오버레이를 유지하며, 우측 토글 화살표 터치 시 다중 행 펼침 뷰(`expanded="true"`)로 트랜지션 전환합니다.
* **다중 선택 / 단일 선택 대응:** 요구사항에 따라 1개만 선택 가능한 Single Select(라디오 형태) 또는 복수 선택이 가능한 Multi Select 모드로 동작을 바인딩합니다.
* **접근성 (A11y):** 
  * 단일 선택 모드인 경우 `role="radiogroup"` 및 칩에 `role="radio"`, `aria-checked={selected}`를 부여합니다.
  * 다중 필터 모드인 경우 개별 칩에 `role="checkbox"`, `aria-checked={selected}` 또는 `<button aria-pressed={selected}>`를 적용합니다.
