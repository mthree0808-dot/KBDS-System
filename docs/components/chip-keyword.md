# Design-to-Code Specification: Keyword Badge / Removable Tag Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - KeywordBadgeItem (Pill container supporting size variants & tone states)
    - KeywordLabelText ("키워드", 13px or 14px KBFG Text)
    - CloseButtonIconContainer (16x16px bounding box for delete/dismiss icon)
      - CloseIconCross (9.74x9.74px cross graphic)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-size` | Dimension | `medium` (Height 36px), `small` (Min-height 32px) |
| `data-tone` | Tone | `neutral`, `red`, `blue` |
| `data-variant` | Style Variant | `filled` (Surface background), `outlined` (Border stroke) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Medium Chip Size: Height 36px (Min-Height 36px), Padding: Left 16px, Right 12px, Gap: 4px
  - Small Chip Size: Min-Height 32px, Padding: Left 12px, Right 8px, Gap: 4px
  - Border Radius: 9999px (Fully rounded pill shape)
- **아이콘 및 타이포그래피 스펙**
  - Close Icon Box: Width 16px, Height 16px (Internal cross symbol: 9.74x9.74px)
  - Medium Label Font: Font Family `KBFG Text`, Size 14px, Weight 500 (Medium), Line-height 20px
  - Small Label Font: Font Family `KBFG Text`, Size 13px, Weight 500 (Medium), Line-height 18px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Tone / Variant | Background Token | Text / Label Token | Outline / Border Token |
| :--- | :--- | :--- | :--- |
| **Neutral (Filled)** | `var(--surface-neutral-secondary-muted, #F4F6F9)` | `var(--text-neutral-primary, #111827)` | `transparent` |
| **Neutral (Outlined)** | `transparent` | `var(--text-neutral-primary, #111827)` | `var(--border-neutral-secondary-muted, #E5E7EB)` (1px solid) |
| **Red / Accent (Filled)** | `var(--surface-accent-red-muted, #FFF6F5)` | `var(--text-accent-red, #E53838)` | `transparent` |
| **Red / Accent (Outlined)** | `transparent` | `var(--text-accent-red, #E53838)` | `var(--border-accent-red-muted, #FFD1D1)` (1px solid) |
| **Blue / Accent (Filled)** | `var(--surface-accent-blue-muted, #EBF6FF)` | `var(--text-accent-blue, #1F6AFF)` | `transparent` |
| **Blue / Accent (Outlined)** | `transparent` | `var(--text-accent-blue, #1F6AFF)` | `var(--border-accent-blue-muted, #C5DDFF)` (1px solid) |

## 6. 구현 가이드라인
- **Compact Alignment & Flex Wrapping**
  - Keyword badges utilize inline flex layout with tight gap sizing (`gap: 4px`) between the keyword text and the trailing dismiss button to ensure responsive resizing.
- **Outline Offset Handling**
  - Outlined variants apply `outline: 1px [token] solid` with `outline-offset: -1px` to stay cleanly within the pill's bounding box without border clipping on high-density displays.
- **Interactive States**
  - The close button container acts as an independent touch/click target within the pill, maintaining a consistent `16x16px` interactive area regardless of the badge height variant.
