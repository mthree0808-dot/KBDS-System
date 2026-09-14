# Design-to-Code Specification: Notification Dot / Status Indicator Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - DotContainer (Absolute positioned container holding the circular status indicator)
    - StatusIndicatorDot (Fully rounded dot asset with notice color token)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-size` | Dimension | `4px`, `6px` |
| `data-tone` | Tone | `notice` (Red status) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Small Dot Variant: Width 4px, Height 4px, Radius: 9999px (Fully rounded)
  - Medium Dot Variant: Width 6px, Height 6px, Radius: 9999px (Fully rounded)
- **위치 지정 규칙**
  - Absolute positioning within parent icon containers, tab items, or list headers to denote unread updates or active alert states.

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component State / Variant | Background Token | Text / Icon Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Notice Status Dot** | `var(--icon-status-notice, #F44F4F)` | N/A | `transparent` |

## 6. 구현 가이드라인
- **Perfect Circular Geometry**
  - Notification dots enforce full rounding (`borderRadius: 9999px`) across exact pixel dimensions (`4x4px` or `6x6px`) to prevent rendering artifacts on high-density mobile screens.
- **Absolute Positioning Context**
  - Designed for absolute placement over navigation items or profile badges to signal notifications without altering inline layout typography.
