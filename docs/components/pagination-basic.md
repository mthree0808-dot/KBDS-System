# Design-to-Code Specification: Pagination, Carousel Indicator & Pill Action Button Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - PaginationControllerGroup (Page Navigation Variant)
    - PrevStepButtons (Double and single backward control arrows)
    - PageIndicatorText ("1 / 10", 22px bold KBFG Text)
    - NextStepButtons (Double and single forward control arrows)
  - CarouselIndicatorGroup (Dot & Arrow Indicator Variant)
    - PrevArrowButton (16x16px control)
    - IndicatorDotList (Pill active indicator + circular inactive dots)
    - PlayPauseIndicator (8x8px state icon)
    - NextArrowButton (16x16px control)
  - ActionBadgePillContainer (Accent Pill Badge Variant)
    - PillBackgroundContainer (Muted surface background, fully rounded)
      - PrefixIcon (`16x16px` bounding box with `10.33px` inner asset)
      - ButtonLabelText ("버튼명", 14px bold KBFG Text)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-size` | Dimension | `large`, `small`, `16`, `24` |
| `data-selected` | State | `true` (Active pill indicator), `false` (Inactive dot) |
| `data-play` | State | `true` |
| `data-hasprefix` | Boolean | `true` |

## 4. 상세 레이아웃 스펙
- **페이지네이션 치수 (Pagination Controller)**
  - Numeric Display Font: Font Family `KBFG Text`, Size 22px, Weight 700 (Bold), Line-height 31px
  - Control Arrow Box: Size 24x24px, Radius: 4px
- **캐러셀 인디케이터 치수 (Carousel Indicator)**
  - Active Indicator Pill: Width 18px, Height 8px, Radius: 9999px (Fully rounded)
  - Inactive Dot: Size 8x8px, Radius: 9999px, Gap: 6px between items
- **필 버튼 치수 (Pill Action Badge)**
  - Pill Padding: Horizontal 12px, Vertical 8px, Radius: 9999px
  - Label Font: Font Family `KBFG Text`, Size 14px, Weight 700 (Bold), Line-height 20px, Gap: 6px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Element | Background Token | Text / Icon Token | Border / Pill Token |
| :--- | :--- | :--- | :--- |
| **Pagination Controls** | `transparent` | `var(--icon-neutral-tertiary, #6B7280)` | `transparent` |
| **Page Indicator Text** | `transparent` | `var(--text-neutral-secondary, #374151)` (Active) / `var(--text-neutral-placeholder, #9CA3AF)` (Divider) | `transparent` |
| **Active Carousel Pill** | `var(--surface-neutral-primary, #111827)` | N/A | `transparent` |
| **Inactive Carousel Dot** | `var(--surface-neutral-primary-muted, #ECEEF2)` | N/A | `transparent` |
| **Action Badge Pill** | `var(--surface-accent-brand-alt-muted, #F4F6F9)` | `var(--text-accent-brand-alt, #111827)` | `transparent` |

## 6. 구현 가이드라인
- **Carousel Pill Indicator Morphing**
  - The active carousel indicator uses a pill shape (`18x8px`) to distinguish itself from standard circular inactive dots (`8x8px`), transitioning smoothly via width updates during slide changes.
- **Icon Rotation & Arrow Alignment**
  - Control arrows utilize directional rotation transforms (`transform: rotate(180deg)`) anchored at `top left` to mirror back-and-forth step triggers consistently across pagination controls.
