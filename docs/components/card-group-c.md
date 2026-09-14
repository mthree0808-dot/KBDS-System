# Design-to-Code Specification: Key-Value List Row, Bullet Content & Radio Button Item Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - ContentWrapperGroup (Absolute positioned vertical layout sections)
    - KeyValueSplitRow (Flex row layout with label, tooltip icon, data value, and bottom divider)
      - LabelGroupContainer (Left side label with optional info tooltip icon)
      - DataValueContainer (Right side primary data text)
      - BottomDividerLine (`1px` thickness, tertiary muted border token)
    - BulletMarkerContentRow (Bullet list item supporting text wrapping and information markers)
      - BulletMarkerSymbol ("∙", 14px light KBFG Text)
      - BulletContentBodyText (Descriptive body text, 14px light KBFG Text)
    - RadioSelectionRowItem (Circular radio button control paired with bold label and subtitle description)
      - CircularRadioButton (`24x24px` bounding box with neutral quaternary border outline)
      - TextDescriptionGroup (Bold primary label and light sublabel description)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-layout` | Variant | `split` (Key-value row layout) |
| `data-hasdivider` | Boolean | `true` |
| `data-hastooltip` | Boolean | `true` |
| `data-variant` | Variant | `bullet`, `secondary` |
| `data-checked` | State | `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Container Width: 310px fixed max width across all list rows
  - Positioning: Absolute positioning offsets (`left: 20px`, `top: 80px`, `153px`, `233px`)
  - Key-Value Split Gap: 12px horizontal gap between label and data, 12px vertical spacing before divider line
  - Bullet Item Gap: 4px spacing between bullet marker and body text
  - Radio Item Gap: 8px spacing between circular radio control and text group
- **타이포그래피 및 아이콘 스펙**
  - Key-Value Label Text: Font Family `KBFG Text`, Size 14px, Weight 300 (Light), Line-height 20px
  - Key-Value Data Text: Font Family `KBFG Text`, Size 14px, Weight 500 (Medium), Line-height 20px, Text Align Right
  - Bullet Body Text: Font Family `KBFG Text`, Size 14px, Weight 300 (Light), Line-height 20px
  - Radio Label Text: Font Family `KBFG Text`, Size 14px, Weight 700 (Bold), Line-height 20px
  - Radio Sublabel Text: Font Family `KBFG Text`, Size 13px, Weight 300 (Light), Line-height 18px
  - Tooltip Icon Box: Size 16x16px bounding box within a 24x24px container slot

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Item / State | Background Token | Text / Icon Token | Border / Divider Token |
| :--- | :--- | :--- | :--- |
| **Key-Value Label Text** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` | `transparent` |
| **Key-Value Data Text** | `transparent` | `var(--text-neutral-primary, #111827)` | `transparent` |
| **Bottom Divider Line** | `transparent` | N/A | `1px var(--border-neutral-tertiary-muted, #F4F6F9) solid` |
| **Bullet Marker & Text** | `transparent` | `var(--text-neutral-tertiary, #4B5563)` | `transparent` |
| **Radio Button Outline** | `transparent` | N/A | `1px var(--border-neutral-quaternary, #9CA3AF) solid` (Fully rounded `9999px`) |

## 6. 구현 가이드라인
- **Split Key-Value Alignment & Dividers**
  - Key-value list rows enforce a flexible split layout (`justify-content: space-between`) with right-aligned data values and full-width bottom divider lines (`height: 1px`, `#F4F6F9`) to ensure clean financial data organization.
- **Circular Radio Button Geometry**
  - Radio button controls enforce fully rounded circular geometries (`borderRadius: 9999px`) across both outer containers (`24x24px`) and inner target outlines (`20x20px`) with negative outline offsets (`-1px`) to match design system standards.
