# Design-to-Code Specification: Accordion Footer Toggle & Muted Info Box Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - AccordionFooterGroup (Absolute positioned vertical stacks for expand/collapse triggers and info boxes)
    - DividerLineComponent (`1px` thickness, tertiary muted border token)
    - AccordionToggleRow (Centered inline flex row with text label and directional chevron indicator)
      - ToggleLabelText ("자세히보기", 14px medium KBFG Text)
      - DirectionalChevronIcon (`20x20px` bounding box with 90-degree or -90-degree rotation transform)
    - MutedInfoBoxContainer (Padding 20px, surface neutral tertiary muted background, 8px radius)
      - BulletContentStack (Vertical flex stack of bullet list items with 12px gap)
        - BulletMarkerSymbol ("∙", 14px light KBFG Text)
        - BulletBodyText (Descriptive guidance text, 14px light KBFG Text)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-length` | Dimension | `full` (Divider length behavior) |
| `data-thickness` | Dimension | `1px` |
| `data-tone` | Tone | `tertiaryMuted` |
| `data-depth` | Number | `1` |
| `data-variant` | Variant | `bullet` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Component Container Width: 310px fixed width across all groups
  - Positioning: Absolute positioning offsets (`left: 130px`, `461px`, `top: 80px`)
  - Accordion Toggle Row Gap: 2px spacing between toggle text and directional chevron icon
  - Muted Info Box Padding: 20px all sides, Radius: 8px, 12px vertical spacing between bullet items
  - Divider Line: Height 1px, full stretch width with 20px gap spacing above/below
- **타이포그래피 및 아이콘 스펙**
  - Accordion Toggle Text: Font Family `KBFG Text`, Size 14px, Weight 500 (Medium), Line-height 20px, Text Center
  - Muted Info Body Text: Font Family `KBFG Text`, Size 14px, Weight 300 (Light), Line-height 20px
  - Directional Chevron Icon: Size 20x20px bounding box with 90-degree or -90-degree rotation transform to indicate expanded/collapsed accordion states

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Element | Background Token | Text / Icon Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Divider Line** | `transparent` | N/A | `1px var(--border-neutral-tertiary-muted, #F4F6F9) solid` |
| **Accordion Toggle Text & Icon** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` / `var(--icon-neutral-quaternary, #9CA3AF)` | `transparent` |
| **Muted Info Box Container** | `var(--surface-neutral-tertiary-muted, #F9FAFB)` | N/A | `transparent` |
| **Muted Info Bullet Text** | `transparent` | `var(--text-neutral-tertiary, #4B5563)` | `transparent` |

## 6. 구현 가이드라인
- **Accordion Toggle Directionality**
  - Accordion footer toggles use directional rotation transforms (`90deg` or `-90deg`) on standard `20x20px` chevron icons to clearly signal collapsible state changes (expand vs. collapse) beneath card bodies.
- **Muted Info Box Containers**
  - Detailed guideline boxes utilize neutral tertiary muted background surfaces (`#F9FAFB`) with an `8px` border radius and internal padding (`20px`) to contain supplementary disclosures or multi-line bullet instructions cleanly.
