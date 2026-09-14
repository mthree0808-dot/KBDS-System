# Chips (칩 / 태그)

사용자가 선택, 필터링, 검색어 삭제, 상태 라벨링 등을 수행할 때 사용하는 다목적 캡슐형 컴포넌트입니다.  
콘텐츠 목록의 조건 선택 및 펼침 제어를 지원하는 **Basic (필터형)**과 선택된 키워드 태깅 및 삭제(Delete/Clear) 인터랙션을 지원하는 **Keyword (키워드/입력형)** 두 가지 타입을 제공합니다.

---

## 1. Component Overview & Types

* **Basic Type (`type="basic"`):**
  * 콘텐츠 필터링 및 카테고리 전환에 사용하는 인터랙티브 칩 그룹입니다.
  * **Solid Fill:** 선택 시 다크 채움 배경(`var(--surface-accent-brand-alt)`)과 화이트 텍스트가 적용됩니다.
  * **Outline:** 선택 시 두께 `1.60px`의 브랜드 아웃라인(`var(--border-accent-brand-alt)`)이 적용됩니다.
  * **Layout Modes:** 단일 행 가로 스크롤(우측 페이드 마스크 및 펼침 버튼) 또는 다중 행 전체 펼침(Multi-line Wrap) 모드를 지원합니다.
* **Keyword Type (`type="keyword"`):**
  * 최근 검색어, 선택된 태그, 입력 폼의 토큰 등을 나타내며 우측 삭제(`X`) 버튼을 기본 포함합니다.
  * **Tone:** Neutral(기본), Red(경고/중요), Blue(정보/강조) 컬러 팔레트를 지원합니다.
  * **Variant:** Muted Tint Background(연한 배경 채움형)와 Outline(외곽선형) 스타일을 제공합니다.
  * **Size:** Medium(`36px`), Small(`32px`) 규격을 지원합니다.

---

## 2. Component Properties

### 2.1 Basic Type Properties (Chip Group)

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `type` | Variant | `"basic"` | `"basic"` | 컴포넌트 유형 |
| `styleVariant` | Variant | `solid`, `outline` | `solid` | 선택 활성화 비주얼 스타일 |
| `expanded` | Boolean | `true`, `false` | `false` | 단일 행 가로 스크롤 vs 다중 행 전체 펼침 |
| `showToggleButton` | Boolean | `true`, `false` | `true` | 우측 펼침/접기 화살표 버튼 표시 여부 |
| `selected` | Boolean | `true`, `false` | `false` | 개별 칩 선택 여부 |
| `label` | Text | String | `"텍스트"` | 칩 내부 텍스트 문구 |

### 2.2 Keyword Type Properties (Individual Chip)

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `type` | Variant | `"keyword"` | `"keyword"` | 컴포넌트 유형 |
| `size` | Variant | `medium` (36px), `small` (32px) | `medium` | 높이 및 패딩, 폰트 규격 |
| `variant` | Variant | `tint` (Background Fill), `outline` | `tint` | 배경 채움 vs 외곽선 스타일 |
| `tone` | Variant | `neutral`, `red`, `blue` | `neutral` | 의미론적 컬러 테마 |
| `label` | Text | String | `"키워드"` | 태그 텍스트 문구 |
| `removable` | Boolean | `true`, `false` | `true` | 우측 닫기/삭제(X) 아이콘 노출 여부 |

---

## 3. Sub-Component Specifications

### 3.1 Type: `basic` (필터 칩 그룹)

* **Chip Item Box Model:**
  * Min Height: `36px`
  * Padding: Left/Right `12px` (내부 텍스트 좌우 패딩: `4px`, Gap: `4px`)
  * Radius: `9999px`
* **Solid Style (`styleVariant="solid"`):**
  * **Selected:** Background `var(--surface-accent-brand-alt, #111827)`, Text `var(--text-neutral-primary-on, white)`, `14px` / `20px` Bold (`700`)
  * **Unselected:** Background `var(--background-neutral-light-gray, #F9FAFB)`, Outline `1px solid var(--border-neutral-secondary-muted, #E5E7EB)` (Offset `-1px`), Text `var(--text-neutral-secondary, #374151)`, `14px` / `20px` Medium (`500`)
* **Outline Style (`styleVariant="outline"`):**
  * **Selected:** Background `transparent`, Outline `1.60px solid var(--border-accent-brand-alt, #111827)` (Offset `-1.60px`), Text `var(--text-neutral-primary, #111827)`, `14px` / `20px` Bold (`700`)
  * **Unselected:** Background `transparent`, Outline `1px solid var(--border-neutral-secondary-muted, #E5E7EB)` (Offset `-1px`), Text `var(--text-neutral-secondary, #374151)`, `14px` / `20px` Medium (`500`)
* **Group Controls:**
  * Scroll Fade Mask: Width `390px`, Height `68px`, `linear-gradient(90deg, white 83%, rgba(255, 255, 255, 0) 91%)`
  * Toggle Button: Container `32x32px`, Icon `9.72 x 18.00px`, Color `var(--icon-neutral-primary, #111827)`
    * Scrollable 모드: `rotate(-90deg)` (하향 화살표)
    * Expanded 모드: `rotate(90deg)` (상향 화살표)

---

### 3.2 Type: `keyword` (키워드/삭제형 칩)

* **Common Box Model:**
  * Layout: `display: inline-flex`, `align-items: center`, `gap: 4px`, `borderRadius: 9999px`, `overflow: hidden`
  * Delete Icon (Suffix): Container `16x16px`, Icon Bounding `9.74 x 9.74px`, Color `var(--icon-neutral-quaternary, #9CA3AF)`
* **Size Matrix:**
  * **Medium (`size="medium"`):** Height/Min Height `36px`, Padding: Left `16px`, Right `12px`, Typography: `KBFG Text`, `14px` / `20px`, Medium (`500`)
  * **Small (`size="small"`):** Min Height `32px`, Padding: Left `12px`, Right `8px`, Typography: `KBFG Text`, `13px` / `18px`, Medium (`500`)

#### Tone & Variant Color Matrix

| Tone | Variant | Background Token | Border / Outline Token | Text Token |
| :--- | :--- | :--- | :--- | :--- |
| **Neutral** | `tint` | `--surface-neutral-secondary-muted` (`#F4F6F9`) | None | `--text-neutral-primary` (`#111827`) |
| **Neutral** | `outline` | `transparent` | `--border-neutral-secondary-muted` (`#E5E7EB`) | `--text-neutral-primary` (`#111827`) |
| **Red** | `tint` | `--surface-accent-red-muted` (`#FFF6F5`) | None | `--text-accent-red` (`#E53838`) |
| **Red** | `outline` | `transparent` | `--border-accent-red-muted` (`#FFD1D1`) | `--text-accent-red` (`#E53838`) |
| **Blue** | `tint` | `--surface-accent-blue-muted` (`#EBF6FF`) | None | `--text-accent-blue` (`#1F6AFF`) |
| **Blue** | `outline` | `transparent` | `--border-accent-blue-muted` (`#C5DDFF`) | `--text-accent-blue` (`#1F6AFF`) |

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Component Usage |
| :--- | :--- | :--- | :--- |
| `--surface-accent-brand-alt` | `#111827` | `background` | Basic Solid 선택 칩 배경 |
| `--background-neutral-light-gray` | `#F9FAFB` | `background` | Basic Solid 미선택 칩 배경 |
| `--border-accent-brand-alt` | `#111827` | `outline-color` | Basic Outline 선택 칩 테두리 (`1.60px`) |
| `--border-neutral-secondary-muted` | `#E5E7EB` | `outline-color` | Basic 미선택 및 Keyword Neutral Outline 테두리 (`1px`) |
| `--surface-neutral-secondary-muted` | `#F4F6F9` | `background` | Keyword Neutral Tint 배경 |
| `--surface-accent-red-muted` | `#FFF6F5` | `background` | Keyword Red Tint 배경 |
| `--border-accent-red-muted` | `#FFD1D1` | `outline-color` | Keyword Red Outline 테두리 (`1px`) |
| `--surface-accent-blue-muted` | `#EBF6FF` | `background` | Keyword Blue Tint 배경 |
| `--border-accent-blue-muted` | `#C5DDFF` | `outline-color` | Keyword Blue Outline 테두리 (`1px`) |
| `--text-neutral-primary` | `#111827` | `color` | Basic Outline 선택 텍스트 및 Keyword Neutral 텍스트 |
| `--text-neutral-primary-on` | `#FFFFFF` | `color` | Basic Solid 선택 텍스트 |
| `--text-neutral-secondary` | `#374151` | `color` | Basic 미선택 텍스트 |
| `--text-accent-red` | `#E53838` | `color` | Keyword Red 텍스트 |
| `--text-accent-blue` | `#1F6AFF` | `color` | Keyword Blue 텍스트 |
| `--icon-neutral-primary` | `#111827` | `background` | Basic 펼침/접기 토글 화살표 |
| `--icon-neutral-quaternary` | `#9CA3AF` | `background` | Keyword 삭제(X) 아이콘 |
| `--color-util-purple` | `#893DE7` | `border-color` | 가이드 영역 아웃라인 |

---

## 5. Interaction & Implementation Notes

* **Basic 타입 펼침 트랜지션:** Scrollable 상태에서 접힌 항목들은 우측 토글 클릭 시 `flex-wrap: wrap` 모드로 부드럽게 확장되며, 컨테이너 높이가 동적으로 늘어나도록 레이아웃 애니메이션을 적용합니다.
* **Keyword 타입 삭제 액션:** 우측 `16x16px` 삭제 버튼 클릭 시 `onDelete(id)` 핸들러를 트리거하며, 칩 본체 클릭 이벤트와 버블링되지 않도록 이벤트 전파를 중단(`e.stopPropagation()`)합니다.
* **접근성 (A11y):** 
  * Basic 칩은 선택 방식에 따라 `role="radio"`(단일 선택) 또는 `role="checkbox"`(다중 필터)를 적용합니다.
  * Keyword 칩의 삭제 버튼에는 `aria-label="[키워드명] 삭제"`를 지정하여 보조 기술 사용자가 명확히 인지할 수 있도록 구현합니다.
