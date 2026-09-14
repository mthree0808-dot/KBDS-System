# Design-to-Code Specification: Action Bar / Filter Header Control Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Inline Flex Wrapper with 20px padding and 12px gap)
  - LeftIconButtonWrapper (`data-variant="IconButton"`)
    - IconButtonComponent (`24x24px` bounding box, radius 4px)
      - IconGraphic (`18.66x5.81px` neutral primary icon)
  - RightFilterButtonWrapper (`data-variant="Filter"`, flexible 1fr layout)
    - FilterButtonComponent (Small size, primary variant, radius 8px)
      - ButtonLabelText ("버튼명", 14px KBFG Text)
      - SuffixIconContainer (`16x16px` dropdown chevron indicator)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-variant` | Variant | `IconButton`, `Filter`, `primary` |
| `data-disabled` | State | `false` |
| `data-pressed` | State | `false` |
| `data-size` | Dimension | `24` (Icon size), `small` (Filter button) |
| `data-hassuffix` | Boolean | `true` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Root Container Padding: Left 20px, Right 20px
  - Container Gap: 12px (Between icon button and filter control)
  - Alignment: Flex items centered vertically (`align-items: center`)
- **컨트롤 및 버튼 스펙**
  - Left Icon Button Bounding Box: 24x24px, Radius: 4px
  - Right Filter Button Radius: 8px, Gap: 2px
  - Filter Button Suffix Icon: 16x16px container (Chevron graphic: 4.86x9px)
- **타이포그래피 스펙**
  - Filter Button Label Text: Font Family `KBFG Text`, Size 14px, Weight 500 (Medium), Line-height 20px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Element | Background Token | Text / Icon Token | Border / Outline Token |
| :--- | :--- | :--- | :--- |
| **Root Container** | `transparent` | N/A | `transparent` |
| **Icon Button Graphic** | `transparent` | `var(--icon-neutral-primary, #111827)` | `transparent` |
| **Filter Button Component** | `transparent` | `var(--text-accent-brand-alt, #111827)` | `transparent` |
| **Filter Chevron Icon** | `transparent` | `var(--icon-accent-brand-alt, #111827)` | `transparent` |

## 6. 구현 가이드라인
- **Flexible Layout Alignment**
  - The filter trigger button utilizes `flex: '1 1 0'` alignment to stretch dynamically alongside the fixed-width icon button wrapper inside the root container.
- **Icon Rotation & Positioning**
  - Dropdown chevron icons use explicit rotation transforms (`transform: rotate(-90deg)`) anchored at `top left` to orient directional arrows accurately within the `16x16px` suffix slot.
