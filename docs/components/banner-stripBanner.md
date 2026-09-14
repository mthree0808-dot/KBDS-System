# Design-to-Code Specification: Notice Banner / Information Row Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - NoticeBannerWrapper (Width: 390px, supporting full-bleed or rounded container variants)
    - BannerContentContainer (Flex row with 8px gap)
      - LeadingIconContainer (`24x24px` icon asset slot)
      - NoticeMessageText ("배너 문구 출력 최대 00자 (1줄)", 14px medium KBFG Text)
    - TrailingActionLinkContainer (Link button slot with right chevron icon)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-variant` | Variant | `full-bleed`, `contained` (Rounded 12px) |
| `data-size` | Dimension | `24px` (Icon container size) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Banner Width: 390px
  - Full-Bleed Variant Padding: Horizontal 20px, Vertical 16px, Radius: 0px
  - Contained Variant Outer Padding: Horizontal 20px, Vertical 0px
  - Contained Inner Wrapper Padding: Horizontal 16px, Vertical 12px, Radius: 12px
  - Element Gap: 8px spacing between leading icon, message text, and trailing arrow
- **타이포그래피 및 아이콘 스펙**
  - Notice Message Text: Font Family `KBFG Text`, Size 14px, Weight 500 (Medium), Line-height 20px
  - Leading Icon Box: Size 24x24px bounding box
  - Trailing Chevron Icon: Size 20x20px bounding box

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Variant / Element | Background Token | Text / Icon Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Banner Container Surface** | `var(--surface-neutral-tertiary-muted, #F9FAFB)` | N/A | `transparent` |
| **Notice Message Text** | `transparent` | `var(--text-neutral-secondary, #374151)` | `transparent` |
| **Leading Icon Graphic** | `transparent` | `var(--icon-neutral-primary, #111827)` | `transparent` |
| **Trailing Chevron Icon** | `transparent` | `var(--icon-neutral-quaternary, #9CA3AF)` | `transparent` |

## 6. 구현 가이드라인
- **Full-Bleed vs. Contained Layouts**
  - Notice banners support both edge-to-edge full-bleed layouts (with horizontal padding directly on the 390px container) and inset card containers featuring a `12px` border radius and internal padding (`16px` horizontal, `12px` vertical).
- **Flexbox Alignment & Single-Line Constraints**
  - Message items use flexible width distribution (`flex: '1 1 0'`) to ensure notice text truncates cleanly or wraps appropriately while preserving vertical alignment with leading icons and trailing action links.
