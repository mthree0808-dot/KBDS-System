# Design-to-Code Specification: Bottom Navigation Bar Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - BottomNavWrapper (Elevated surface container with rounded top corners)
    - NavItemContainer (Repeated flex items for menu tabs, e.g., 5-column layout)
      - IconContainer (`32x32px` interactive bounding box with opacity states)
        - InnerIconGraphic (`24x24px` icon asset)
      - LabelText ("메뉴", 11px KBFG Text)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-select` | State | `true` (Active tab), `false` (Inactive tab) |
| `data-variant` | Variant | `elevated`, `bottom-nav` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Navigation Bar Width: 390px
  - Top Padding: 4px, Left/Right Padding: 20px
  - Top Corner Radius: 24px (Border top-left and top-right)
  - Item Layout Gap: 2px (Between icon container and text label)
- **컨트롤 및 아이콘 스펙**
  - Tab Item Width: Flex uniform distribution (`flex: 1 1 0`)
  - Icon Wrapper Size: 32x32px (Inner graphic size: 24x24px)
- **타이포그래피 스펙**
  - Menu Label Text: Font Family `KBFG Text`, Size 11px, Weight 700 (Bold), Line-height 15px, Alignment Center

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Element | Background Token | Text / Icon Token | Border / Divider Token |
| :--- | :--- | :--- | :--- |
| **Bottom Nav Surface** | `var(--background-neutral-elevated, white)` | N/A | `var(--border-neutral-tertiary-muted, #F4F6F9)` (1px solid top border) |
| **Active Tab (`data-select="true"`)** | `transparent` | `var(--icon-neutral-primary, #111827)` (Opacity 1.0) | `transparent` |
| **Inactive Tab (`data-select="false"`)** | `transparent` | `var(--icon-neutral-primary, #111827)` (Opacity 0.30) | `transparent` |

## 6. 구현 가이드라인
- **Opacity & State Transition Rules**
  - Active and inactive navigation states rely on opacity adjustments (`opacity: 0.30` for unselected icons vs fully opaque selected states) to maintain visual hierarchy across tab items.
- **Uniform Column Distribution**
  - Nav items utilize flex distribution (`flex: '1 1 0'`) with centered text and icon alignment to divide the standard mobile width (`390px`) evenly across all menu actions.
