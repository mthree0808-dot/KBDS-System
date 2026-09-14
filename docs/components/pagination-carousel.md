# Design-to-Code Specification: Overlay Pagination and Carousel Badge Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: n
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - OverlayPaginationPill (Fully rounded pill container with backdrop variants)
    - PrevArrowButton (Navigation control arrow)
    - PageIndicatorGroup (Current page and total page count text)
      - CurrentPageText ("1", KBFG Text)
      - SeparatorText ("/", KBFG Text with opacity)
      - TotalPageText ("10", KBFG Text with opacity)
    - NextArrowButton (Navigation control arrow)
  - PlayStateIndicatorButton (Circular control icon container)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-size` | Dimension | `small`, `medium`, `large`, `16` |
| `data-play` | State | `true` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Pill Container Radius: 9999px (Fully rounded pill shape)
  - Small Variant Padding: Horizontal 4px, Vertical 2px, Gap: 4px
  - Medium / Large Variant Padding: Horizontal 8px, Vertical 4px, Gap: 6px to 8px
- **컨트롤 및 아이콘 스펙**
  - Small Play State Button: Size 20x20px, Radius: 9999px
  - Large Play State Button: Size 32x32px, Radius: 9999px
- **타이포그래피 스펙**
  - Small Label Font: Font Family `KBFG Text`, Size 11px, Weight 700 (Bold), Line-height 15px
  - Medium / Large Label Font: Font Family `KBFG Text`, Size 15px, Weight 700 (Bold), Line-height 21px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Background Variant | Surface / Pill Token | Text / Icon Token (Light) | Text / Icon Token (Dark / Fixed) |
| :--- | :--- | :--- | :--- |
| **White 80% Translucent** | `var(--white-800, rgba(255, 255, 255, 0.80))` | `var(--text-neutral-primary-fixed, #111827)` | `var(--icon-neutral-tertiary, #6B7280)` |
| **Black 40% Translucent** | `var(--black-400, rgba(0, 0, 0, 0.40))` | `var(--text-neutral-primary-on-fixed, white)` | `var(--icon-neutral-primary-on-fixed, white)` |
| **Black 80% Translucent** | `var(--black-800, rgba(0, 0, 0, 0.80))` | `var(--text-neutral-primary-on-fixed, white)` | `var(--icon-neutral-primary-on-fixed, white)` |

## 6. 구현 가이드라인
- **Backdrop Transparency & Contrast Rules**
  - Overlay pagination pills utilize semi-transparent background tokens (`rgba(255, 255, 255, 0.80)` or `rgba(0, 0, 0, 0.40)/0.80`) to remain legible over dynamic background photography or image carousels.
- **Flexbox Spacing & Alignment**
  - Pagination elements use inline flex containers with pill border radii (`9999px`), ensuring text indicators and arrow controls stay perfectly centered vertically regardless of variant sizing.
