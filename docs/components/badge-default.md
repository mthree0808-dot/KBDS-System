# Design-to-Code Specification: Badge / Status Tag Component System

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - BadgeItemContainer (Pill-shaped badge supporting solid tones, muted surfaces, and leading status icons)
    - OptionalLeadingIcon (`14x14px` status glyph slot)
    - BadgeLabelText ("NEW", "추천", "UPDATE", "진행상태", 11px bold KBFG Text)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-tone` | Tone | `notice` (Red), `blue`, `brand`, `muted`, `positive` |
| `data-variant` | Variant | `solid`, `muted`, `outlined` |
| `data-size` | Dimension | `20px` (Min-height container) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Badge Min-Height: 20px, Min-Width: 20px
  - Padding (Standard): Horizontal 6px, Vertical 0px (or 2px vertical for outlined variant with icon)
  - Padding (Outlined with Icon): Left 6px, Right 8px, Top/Bottom 2px
  - Border Radius: 9999px (Fully rounded pill shape)
  - Element Gap: 2px spacing between leading status icon and text label
- **타이포그래피 및 아이콘 스펙**
  - Badge Label Text: Font Family `KBFG Text`, Size 11px, Weight 700 (Bold), Line-height 15px, Text Center
  - Leading Status Icon Box: Size 14x14px bounding box (Icon vector: 9.99x7.69px)

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Badge Variant / Tone | Background Token | Text / Icon Token | Border / Outline Token |
| :--- | :--- | :--- | :--- |
| **Solid Notice (Red)** | `var(--surface-status-notice, #F44F4F)` | `var(--text-neutral-primary-on-fixed, white)` | `transparent` |
| **Solid Blue** | `var(--surface-accent-blue, #2974FF)` | `var(--text-neutral-primary-on-fixed, white)` | `transparent` |
| **Solid Brand** | `var(--surface-accent-brand-alt, #111827)` | `var(--text-neutral-primary-on, white)` | `transparent` |
| **Muted Brand Variant** | `var(--surface-accent-brand-alt-muted, #F4F6F9)` | `var(--text-accent-brand-alt, #111827)` | `transparent` |
| **Muted Positive Variant** | `var(--surface-status-positive-muted, #EBF6FF)` | `var(--text-status-positive, #1F6AFF)` | `transparent` |
| **Muted Red Variant** | `var(--surface-accent-red-muted, #FFF6F5)` | `var(--text-accent-red, #E53838)` | `transparent` |
| **Outlined Status Tag** | `var(--surface-neutral-quaternary-muted, white)` | `var(--text-neutral-secondary, #374151)` / `var(--icon-neutral-primary, #111827)` | `1px var(--border-neutral-secondary-muted, #E5E7EB) solid` |

## 6. 구현 가이드라인
- **Pill Shape & Geometry Constraints**
  - Badges enforce strict pill geometry (`borderRadius: 9999px`) with a fixed height of `20px` to maintain visual consistency when embedded inside table cells, list headers, or card titles.
- **Outlined State with Leading Icon**
  - Outlined badges incorporate a subtle neutral border (`1px solid #E5E7EB`) with negative outline offsets (`outlineOffset: '-1px'`) and a leading 14px icon slot, ensuring flexible support for interactive status filtering.
