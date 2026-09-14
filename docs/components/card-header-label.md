# Design-to-Code Specification: Composite Status, Breadcrumb & Accent Tag Component Group

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - CompositeRowContainer (Absolute positioned inline flex groups containing distinct sub-components)
    - StatusBadgeTag (Outlined pill container with leading status icon and text label)
    - BreadcrumbContainer (Neutral secondary muted container wrapping account tags separated by vertical dividers)
    - MutedAccentTag (Rectangular pill container with red surface tint and red accent text label)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-tone` | Tone | `red`, `redTint` |
| `data-variant` | Variant | `division`, `text`, `tint` |
| `data-count` | Number | `2` (Number of items in breadcrumb) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Status Badge Tag: Min-width 20px, Min-height 20px, Padding: Horizontal 6px (Right 8px), Vertical 2px, Radius: 9999px
  - Breadcrumb Container: Padding: Horizontal 6px, Vertical 4px, Radius: 6px, Gap: 6px between tags and divider
  - Muted Accent Tag: Height 20px, Min-width 20px, Padding: Horizontal 6px, Vertical 0px, Radius: 4px
- **타이포그래피 및 아이콘 스펙**
  - Tag & Breadcrumb Text: Font Family `KBFG Text`, Size 11px, Weight 700 (Bold), Line-height 15px
  - Leading Status Icon Box: Size 14x14px bounding box (Icon vector: 9.99x7.69px)
  - Breadcrumb Divider Line: Width 1px, self-stretch height with vertical padding

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Item / State | Background Token | Text / Icon Token | Border / Outline Token |
| :--- | :--- | :--- | :--- |
| **Status Badge Tag** | `var(--surface-neutral-quaternary-muted, white)` | `var(--text-neutral-secondary, #374151)` / `var(--icon-neutral-primary, #111827)` | `1px var(--border-neutral-secondary-muted, #E5E7EB) solid` |
| **Breadcrumb Container** | `var(--surface-neutral-secondary-muted, #F4F6F9)` | `var(--text-neutral-secondary, #374151)` | `transparent` |
| **Breadcrumb Divider Line** | `transparent` | `var(--border-neutral-quaternary, #9CA3AF)` | `transparent` |
| **Muted Accent Tag** | `var(--surface-accent-red-muted, #FFF6F5)` | `var(--text-accent-red, #E53838)` | `transparent` |

## 6. 구현 가이드라인
- **Mixed Geometry Rendering**
  - Composite component layouts combine fully rounded pill containers (`borderRadius: 9999px` for status tags) with rectangular radius containers (`borderRadius: 6px` for breadcrumb wrappers and `4px` for muted accent tags) to maintain strict hierarchical distinction across component types.
- **Divider Alignment & Flex Spacing**
  - Breadcrumb segments utilize tight inline spacing (`gap: 6px`) and vertical divider lines with self-stretch height rules to ensure clean visual separation of metadata tags without text wrapping anomalies.
