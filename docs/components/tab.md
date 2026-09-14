# Design-to-Code Specification: Multi-Depth Navigation Tabs Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - TabNavigationContainer (Horizontal container with gradient edge masks)
    - Depth1TabBar (Primary tabs with bottom border indicator, e.g., 2px neutral primary stroke)
    - Depth2TabBar (Pill button tabs with solid background active state)
    - Depth3TabBar (Compact pill tabs separated by vertical divider lines)
      - TabItem (Supports selected and unselected text states)
      - DividerLine (`1px` width tertiary muted separator)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-variant` | Variant | `1depth`, `2depth`, `3depth` |
| `data-selected` | State | `true`, `false` |
| `data-hasicon` | Boolean | `false` |
| `data-hasiconbadge` | Boolean | `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Container Width: 390px (Standard mobile width)
  - Depth 1 Padding: Horizontal 24px or 20px, Vertical padding with bottom border (`1px` tertiary muted)
  - Depth 2 Pill Padding: Horizontal 12px, Vertical 8px, Radius: 9999px (Fully rounded)
  - Depth 3 Pill Padding: Horizontal 8px, Vertical 4px, Min-Width 64px
- **타이포그래피 스펙**
  - Depth 1 Selected Text: Font Family `KBFG Text`, Size 16px, Weight 700 (Bold), Line-height 22px
  - Depth 2/3 Selected Text: Font Family `KBFG Text`, Size 14px, Weight 700 (Bold), Line-height 20px
  - Unselected Text: Font Family `KBFG Text`, Size 14px/16px, Weight 500 (Medium), Line-height 20px/22px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Element / Depth | Background Token | Text / Label Token | Active Indicator / Border Token |
| :--- | :--- | :--- | :--- |
| **Depth 1 Selected Tab** | `transparent` | `var(--text-neutral-primary, #111827)` | `2px var(--border-neutral-primary, #111827) solid` |
| **Depth 1 Unselected Tab** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` | `1px var(--border-neutral-tertiary-muted, #F4F6F9) solid` (Bottom) |
| **Depth 2 Selected Tab** | `var(--surface-neutral-primary, #111827)` | `var(--text-neutral-primary-on, white)` | `transparent` |
| **Depth 2 Unselected Tab** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` | `transparent` |
| **Depth 3 Divider Line** | `var(--border-neutral-tertiary-muted, #F4F6F9)` | N/A | `transparent` |

## 6. 구현 가이드라인
- **Horizontal Scroll & Edge Gradient Masking**
  - Overflowing tab lists incorporate linear gradient masks (`linear-gradient(90deg, rgba(255,255,255,0) 0%, white 5%, white 95%, rgba(255,255,255,0) 100%)`) over boundary edges to provide smooth visual fade-out cues for scrollable content.
- **Active Border Indicator Handling**
  - Depth 1 tabs apply a strict 2px bottom border indicator (`border-bottom: 2px var(--border-neutral-primary) solid`) directly to active items, aligning with standard underline tab interaction models.
