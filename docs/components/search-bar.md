# Design-to-Code Specification: Search / Input Bar with Action Icon Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - InputFieldContainer (Inline flex container with min-height 56px)
    - LeadingActionButton (Back or navigation action icon wrapper, 32x32px bounding box)
    - InputBoxWrapper (Pill-shaped input field wrapper, background surface neutral tertiary muted)
      - SearchIcon (`20x20px` prefix icon container)
      - InputTextContent (Placeholder text, entered text value, or active cursor indicator)
      - ClearActionButton (Optional secondary clear button container, 24x24px)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-entered` | State | `true`, `false` |
| `data-focused` | State | `true`, `false` |
| `data-size` | Dimension | `24`, `32` |
| `data-variant` | Variant | `primary`, `secondary` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Root Input Bar Min-Height: 56px, Padding: Left/Right 20px, Top/Bottom 4px
  - Input Pill Box Radius: 9999px (Fully rounded pill shape), Internal Padding: 12px
  - Element Gap: 8px spacing between leading button and input pill
- **컨트롤 및 아이콘 스펙**
  - Leading Action Button Box: Size 32x32px (Icon size: 9.72x18px)
  - Prefix Search Icon: Size 20x20px (Internal graphic: 15.21x15.21px)
  - Input Cursor Indicator: Width 1.60px, Height 24px, Background `var(--icon-accent-brand-alt)`
- **타이포그래피 스펙**
  - Placeholder Text: Font Family `KBFG Text`, Size 17px, Weight 500 (Medium), Line-height 24px
  - Entered Text / Value: Font Family `KBFG Text`, Size 17px, Weight 700 (Bold), Line-height 24px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Element | Background Token | Text / Icon Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Input Pill Background** | `var(--surface-neutral-tertiary-muted, #F9FAFB)` | N/A | `transparent` |
| **Placeholder Text** | `transparent` | `var(--text-neutral-placeholder, #9CA3AF)` | `transparent` |
| **Entered / Active Text** | `transparent` | `var(--text-neutral-primary, #111827)` | `transparent` |
| **Leading & Search Icons** | `transparent` | `var(--icon-neutral-primary, #111827)` | `transparent` |
| **Input Cursor & Focus** | `transparent` | `var(--icon-accent-brand-alt, #111827)` (Cursor bar) | `transparent` |

## 6. 구현 가이드라인
- **Pill Input Container & Flex Flow**
  - Input fields use fully rounded pill wrappers (`borderRadius: 9999px`) with flexible widths (`flex: '1 1 0'`) to adapt fluidly inside mobile screen layouts alongside navigation buttons.
- **Cursor and Clear Action Positioning**
  - Active focused states render a vertical text cursor (`1.60x24px`) alongside entered typography, while active inputs display a secondary clear button (`24x24px`) positioned at the trailing edge of the pill box.
