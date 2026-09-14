# Tabs (탭)

동일한 맥락 내에서 콘텐츠 그룹을 전환할 때 사용하는 네비게이션 컴포넌트입니다. 위계(Depth)에 따라 1depth(언더라인), 2depth(캡슐/필), 3depth(구분선 텍스트) 형태를 제공하며, 좌우 스크롤(Scrollable) 또는 균등 분할(Fixed) 배치를 지원합니다.

---

## 1. Component Overview & Types

* **1depth (Line Tab):** 페이지의 최상위 카테고리 전환에 사용하며, 하단 언더라인 인디케이터로 활성 탭을 표시합니다.
  * **Fixed Type:** 가로 폭(`390px`) 내에서 탭 아이템이 균등한 너비(`flex: 1`)로 분할 배치됩니다.
  * **Scrollable Type:** 탭 아이템이 자체 너비를 가지며 좌우 스크롤을 지원합니다. (좌우 페이드 그라데이션 포함)
* **2depth (Pill Tab):** 1depth 하위의 서브 카테고리 분류에 사용하며, 캡슐형 배경(`border-radius: 9999px`)으로 활성 상태를 강조합니다.
* **3depth (Inline Separator Tab):** 세부 필터링 및 최하위 분류에 사용하며, 탭 아이템 사이에 버티컬 디바이더(Divider)를 배치합니다.

---

## 2. Properties Specification

### 2.1 Tab Container Level

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `variant` | Variant | `1depth`, `2depth`, `3depth` | `1depth` | 탭 계층 구조 및 비주얼 스타일 |
| `layout` | Variant | `fixed`, `scrollable` | `scrollable` | 균등 너비 분할형 vs 스크롤형 (1depth 지원) |
| `hasGradient` | Boolean | `true`, `false` | `true` | 스크롤 영역 좌우 페이드 그라데이션 표시 여부 |

### 2.2 Tab Item Level

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `selected` | Boolean | `true`, `false` | `false` | 현재 탭 선택 활성화 여부 |
| `label` | Text | String | `"텍스트"` | 탭 텍스트 레이블 |
| `hasIcon` | Boolean | `true`, `false` | `false` | 탭 내 아이콘 표시 여부 |
| `hasIconBadge` | Boolean | `true`, `false` | `false` | 뱃지/카운터 표시 여부 |

---

## 3. Detailed Specifications by Variant

### 3.1 1depth (Line Tab)

* **Container:**
  * Height: 약 `46~47px` (Padding Top/Bottom `12px` + Text `22px` + Indicator `2px`)
  * Outer Padding: Left/Right `24px` (Fixed) 또는 `20px` (Scrollable)
  * Container Border: 하단 `1px solid var(--border-neutral-tertiary-muted, #F4F6F9)`
  * Item Gap: `4px`
* **Item Layout & Internal Spacing:**
  * Padding: Top/Bottom `12px`, Inner Text Padding Left/Right `8px` + `4px`
* **Indicator (Selected):**
  * 하단 `2px solid var(--border-neutral-primary, #111827)`
* **Typography & Color:**
  * Selected: `KBFG Text`, Bold (`700`), `16px` / `22px`, Color `var(--text-neutral-primary, #111827)`
  * Unselected: `KBFG Text`, Bold (`700`), `16px` / `22px`, Color `var(--text-neutral-quaternary, #6B7280)`

---

### 3.2 2depth (Pill Tab)

* **Container:**
  * Height: `36px`
  * Outer Padding: Left/Right `20px`
  * Item Gap: `4px`
* **Item Spec:**
  * Min Width: `56px`
  * Height: `36px`
  * Padding: Top/Bottom `8px`, Left/Right `12px` (Inner text padding: `2px`)
  * Radius: `9999px` (Full Pill)
* **States:**
  * **Selected:**
    * Background: `var(--surface-neutral-primary, #111827)`
    * Typography: `KBFG Text`, Bold (`700`), `14px` / `20px`
    * Text Color: `var(--text-neutral-primary-on, #FFFFFF)`
  * **Unselected:**
    * Background: `transparent`
    * Typography: `KBFG Text`, Medium (`500`), `14px` / `20px`
    * Text Color: `var(--text-neutral-quaternary, #6B7280)`

---

### 3.3 3depth (Inline Separator Tab)

* **Container:**
  * Height: `28px`
  * Outer Padding: Left/Right `20px`
  * Item Gap: `4px`
* **Item Spec:**
  * Min Width: `64px`
  * Height: `28px`
  * Padding: Top/Bottom `4px`, Left/Right `8px` (Inner text padding: `2px`)
  * Radius: `9999px`
* **States:**
  * **Selected:**
    * Typography: `KBFG Text`, Bold (`700`), `14px` / `20px`
    * Text Color: `var(--text-accent-brand-alt, #111827)`
  * **Unselected:**
    * Typography: `KBFG Text`, Medium (`500`), `14px` / `20px`
    * Text Color: `var(--text-neutral-quaternary, #6B7280)`
* **Divider (인라인 구분선):**
  * Total Height: `28px` (Padding Top/Bottom `8px`)
  * Line Spec: Width `1px`, Height `12px` (`flex: 1 1 0`)
  * Line Color: `var(--border-neutral-tertiary-muted, #F4F6F9)`
  * Properties: `data-length="insent"`, `data-tone="tertiaryMuted"`

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Usage |
| :--- | :--- | :--- | :--- |
| `--text-neutral-primary` | `#111827` | `color` | 1depth 선택 탭 레이블 |
| `--text-neutral-primary-on` | `#FFFFFF` | `color` | 2depth 선택 탭 레이블 |
| `--text-accent-brand-alt` | `#111827` | `color` | 3depth 선택 탭 레이블 |
| `--text-neutral-quaternary` | `#6B7280` | `color` | 1depth / 2depth / 3depth 미선택 탭 레이블 |
| `--surface-neutral-primary` | `#111827` | `background` | 2depth 선택 탭 배경 캡슐 |
| `--border-neutral-primary` | `#111827` | `border-bottom-color` | 1depth 선택 탭 하단 인디케이터 (2px) |
| `--border-neutral-tertiary-muted` | `#F4F6F9` | `border-color` / `background` | 1depth 하단 구분선 (1px), 3depth 세로 디바이더 |
| `--color-util-purple` | `#893DE7` | `border-color` | 가이드/아웃라인 영역 |

---

## 5. Layout & Interaction Rules

* **스크롤 페이드 마스크:** 탭 개수가 많아 화면 너비를 초과할 경우, 좌우 끝에 `linear-gradient(90deg, rgba(255, 255, 255, 0) 0%, white 5%, white 95%, rgba(255, 255, 255, 0) 100%)` 오버레이를 적용해 스크롤 가능함을 시각적으로 안내합니다.
* **디바이더 렌더링 규칙 (3depth):** 마지막 탭 아이템 우측에는 디바이더를 배치하지 않습니다.
* **텍스트 처리:** 탭 내 텍스트는 `wordWrap: break-word` 속성이 정의되어 있으나, UI 일관성을 위해 1줄(`white-space: nowrap`) 유지를 기본으로 권장합니다.
