# Pagination Basic (페이지네이션 / 인디케이터)

리스트, 테이블, 카드 캐러셀 또는 배너 등 복수 항목의 콘텐츠를 탐색할 때 사용하는 페이지네이션 및 인디케이터 컴포넌트 세트입니다.  
사용 목적에 따라 **수치형(Number/Arrows)**, **도트/캐러셀형(Dots & Play/Pause)**, **캡슐/버튼형(Capsule Button)**의 3가지 유형을 제공합니다.

---

## 1. Component Overview & Types

* **Number Type (수치형 페이지네이션):** 현재 페이지와 전체 페이지 수를 수치(`1/10`)로 안내하며, 첫 페이지/이전 페이지/다음 페이지/끝 페이지 이동 화살표를 제공합니다.
* **Dots Type (캐러셀 도트 인디케이터):** 카드/배너 등의 슬라이드 상태를 점/바 형태로 표시하며, 자동 재생 제어 버튼(Play/Pause) 및 이전/다음 화살표를 포함합니다.
* **Capsule Type (캡슐/플로팅 버튼형):** 배너나 플로팅 바 내부에서 아이콘과 함께 페이지 탐색 액션을 제공하는 라운드형 버튼 형태입니다.

---

## 2. Component Properties

### 2.1 General Properties

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `type` | Variant | `number`, `dots`, `capsule` | `number` | 페이지네이션 유형 |
| `size` | Variant | `large`, `medium`, `small` | `large` | 컴포넌트 전체 규격/폰트 스케일 |

### 2.2 Number Type Props

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `currentPage` | Number | Integer | `1` | 현재 활성 페이지 번호 |
| `totalPage` | Number | Integer | `10` | 전체 페이지 수 |
| `showFirstLast` | Boolean | `true`, `false` | `true` | 첫/끝 페이지 이동(더블 화살표) 표시 여부 |

### 2.3 Dots Type Props

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `currentIndex` | Number | Integer | `0` | 현재 선택된 인덱스 (0-based) |
| `totalCount` | Number | Integer | `5` | 전체 슬라이드/도트 개수 |
| `isPlay` | Boolean | `true`, `false` | `true` | 자동 슬라이드 재생 상태 (Play/Pause 제어) |
| `showArrows` | Boolean | `true`, `false` | `true` | 좌우 이전/다음 탐색 화살표 표시 여부 |

### 2.4 Capsule Type Props

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `label` | Text | String | `"버튼명"` | 텍스트 레이블 |
| `hasPrefix` | Boolean | `true`, `false` | `true` | 좌측 프리픽스 아이콘 노출 여부 |
| `disabled` | Boolean | `true`, `false` | `false` | 비활성화 상태 여부 |

---

## 3. Sub-Component Specifications

### 3.1 Type: `number` (수치형 페이지네이션)

* **Container:**
  * Width: `350px`, Height: `31px`
  * Layout: 좌측 컨트롤, 중앙 페이지 텍스트, 우측 컨트롤 분할 배치
* **Navigation Arrows (Controls):**
  * Container Size: `24x24px`, Border Radius: `4px`
  * Inner Gap: `8px`
  * Icons:
    * First / Last (더블 꺾쇠): `13.39 x 13.60px` (우측은 180도 회전)
    * Prev / Next (싱글 꺾쇠): `7.29 x 13.50px` (우측은 180도 회전)
  * Fill: `var(--icon-neutral-tertiary, #6B7280)`
  * Props: `data-disabled="false"`, `data-pressed="false"`, `data-size="24"`, `data-variant="primary"`
* **Page Counter Display:**
  * Padding: Left/Right `2px`, Inner Gap: `2px`
  * Typography: `KBFG Text`, Bold (`700`), `22px` / `31px`
  * Current Page (`1`): `var(--text-neutral-secondary, #374151)`
  * Separator (`/`): `var(--text-neutral-placeholder, #9CA3AF)`
  * Total Page (`10`): `var(--text-neutral-placeholder, #9CA3AF)`

---

### 3.2 Type: `dots` (캐러셀 인디케이터)

* **Container:**
  * Height: `16px` (도트 영역 `8px`)
  * Layout: 가로 정렬, Inner Gap: `12px`
* **Arrow Buttons (Prev / Next):**
  * Size: `16x16px`, Border Radius: `4px`
  * Icon Bounding: `4.86 x 9.00px` (Next는 180도 회전)
  * Fill: `var(--icon-neutral-tertiary, #6B7280)`
* **Dots Track:**
  * Gap: `6px`, Radius: `9999px`
  * **Active Dot:** Width `18px`, Height `8px`, Background `var(--surface-neutral-primary, #111827)`
  * **Inactive Dot:** Width `8px`, Height `8px`, Background `var(--surface-neutral-primary-muted, #ECEEF2)`
* **Play / Pause Control:**
  * Size: `8x8px`
  * Fill: `var(--icon-neutral-primary, #111827)`
  * Props: `data-play="true"`, `data-size="small"`

---

### 3.3 Type: `capsule` (캡슐형 버튼)

* **Container:**
  * Height: `36px`
  * Padding: Top/Bottom `8px`, Left/Right `12px`
  * Background: `var(--surface-accent-brand-alt-muted, #F4F6F9)`
  * Border Radius: `9999px` (Full Round)
  * Inner Gap: `6px`
* **Internal Button:**
  * Border Radius: `8px`, Inner Gap: `2px`
  * Icon: Size `16x16px` (Bounding `10.33 x 10.33px`), Fill `var(--icon-accent-brand-alt, #111827)`
  * Typography: `KBFG Text`, Bold (`700`), `14px` / `20px`, Color `var(--text-accent-brand-alt, #111827)`
  * Props: `data-size="small"`, `data-variant="primary"`, `data-hasprefix="true"`

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Component Usage |
| :--- | :--- | :--- | :--- |
| `--text-neutral-secondary` | `#374151` | `color` | 수치형 현재 페이지 번호 |
| `--text-neutral-placeholder` | `#9CA3AF` | `color` | 수치형 구분선(`/`) 및 전체 페이지 수 |
| `--text-accent-brand-alt` | `#111827` | `color` | 캡슐형 버튼 텍스트 레이블 |
| `--icon-neutral-tertiary` | `#6B7280` | `background` / `fill` | 이전/다음/첫/끝 이동 화살표 아이콘 |
| `--icon-neutral-primary` | `#111827` | `background` / `fill` | 재생/정지(Play/Pause) 제어 아이콘 |
| `--icon-accent-brand-alt` | `#111827` | `background` / `fill` | 캡슐형 내부 프리픽스 아이콘 |
| `--surface-neutral-primary` | `#111827` | `background` | 활성 도트(Active Bar Indicator) |
| `--surface-neutral-primary-muted` | `#ECEEF2` | `background` | 비활성 도트(Inactive Dot) |
| `--surface-accent-brand-alt-muted` | `#F4F6F9` | `background` | 캡슐형 컨테이너 배경색 |
| `--color-util-purple` | `#893DE7` | `border-color` | 가이드 영역 아웃라인 |

---

## 5. Interaction & Usability Rules

* **경계 조건 비활성화:** 
  * `currentPage === 1`일 때 First 및 Prev 화살표는 `disabled="true"` 처리 및 터치 인터랙션을 차단합니다.
  * `currentPage === totalPage`일 때 Next 및 Last 화살표는 `disabled="true"` 처리합니다.
* **도트 확장 애니메이션:** 활성 도트는 너비가 `8px`에서 `18px`로 늘어나는 가로 확장 트랜지션(`transition: width 0.2s ease-in-out`)을 적용합니다.
* **접근성 (A11y):** 
  * 수치형 영역에 `aria-live="polite"`를 선언하여 페이지 전환 시 변경된 번호를 보조 기술에 전달합니다.
  * 이전/다음/재생 버튼에 명확한 명칭(`aria-label="이전 페이지"`, `aria-label="자동 재생 일시정지"`)을 부여합니다.
