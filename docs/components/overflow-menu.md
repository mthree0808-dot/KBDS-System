# Design-to-Code Specification: Dropdown Menu / Context Popover Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Elevated wrapper with border radius and drop shadow)
  - MenuListWrapper (Vertical flex stack of context menu items)
    - MenuListItem (Interactive row container with 10px radius, min-width 120px)
      - LeadingIcon (`20x20px` icon asset slot)
      - MenuLabelText ("메뉴명", 15px bold KBFG Text)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-hasicon` | Boolean | `true`, `false` |
| `data-pressed` | State | `true`, `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Root Container Padding: Horizontal 4px, Vertical 8px, Radius: 16px
  - Menu Item Padding: 12px on all sides, Radius: 10px, Min-Width: 120px
  - Element Gap: 4px spacing between leading icon and menu label
- **컨트롤 및 타이포그래피 스펙**
  - Menu Label Text: Font Family `KBFG Text`, Size 15px, Weight 700 (Bold), Line-height 21px
  - Leading Icon Box: Size 20x20px bounding box (Icon graphic: 15.55x4.84px)
  - Date/Grid Matrix: N/A (Standard menu component layout)

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component State / Element | Background Token | Text / Icon Token | Elevation / Shadow Token |
| :--- | :--- | :--- | :--- |
| **Root Container Surface** | `var(--background-neutral-elevated, white)` | N/A | `0px 4px 16px rgba(12, 17, 29, 0.10)` |
| **Menu Item Text (Default)** | `transparent` | `var(--text-neutral-secondary, #374151)` | `transparent` |
| **Leading Icon Graphic** | `transparent` | `var(--icon-neutral-primary, #111827)` | `transparent` |

## 6. 구현 가이드라인
- **Elevation & Shadow Layering**
  - Dropdown menus and context popovers rely on elevated surface tokens (`white`) paired with prominent drop shadows (`0px 4px 16px rgba(12, 17, 29, 0.10)`) to maintain visual hierarchy and contrast over underlying UI layers.
- **Interactive Item States & Z-Index Rules**
  - Menu items utilize nested rounded containers (`10px` radius) with comfortable padding (`12px`) to ensure touch-friendly interaction targets. Popover menus must enforce an elevated stacking context (`z-index` management) to prevent clipping issues inside modal layers or scroll containers.
