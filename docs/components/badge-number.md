# Design-to-Code Specification: Notification Badge / Counter Dot Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - NotificationBadgeContainer (Circular or pill-shaped container supporting numeric counts)
    - CounterNumberText ("5", 11px bold KBFG Text)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-tone` | Tone | `notice` (Red), `secondary` (Neutral dark) |
| `data-size` | Dimension | `20px` (Min-height and min-width container) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Badge Min-Height: 20px, Min-Width: 20px
  - Padding: Horizontal 4px, Vertical 0px
  - Border Radius: 9999px (Fully rounded circular or pill shape for multi-digit counts)
- **타이포그래피 스펙**
  - Counter Text: Font Family `KBFG Text`, Size 11px, Weight 700 (Bold), Line-height 15px, Text Center

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Badge Tone / Variant | Background Token | Text / Counter Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Notice Tone (Red)** | `var(--surface-status-notice, #F44F4F)` | `var(--text-neutral-primary-on, white)` | `transparent` |
| **Secondary Tone (Neutral)** | `var(--surface-neutral-secondary, #374151)` | `var(--text-neutral-primary-on, white)` | `transparent` |

## 6. 구현 가이드라인
- **Circular Geometry & Auto-Scaling**
  - Notification badges maintain a strict minimum height and width of `20px` with full rounding (`borderRadius: 9999px`). Single digits render as perfect circles, while multi-digit numbers expand horizontally into pill shapes automatically via horizontal padding (`4px`).
- **Absolute Positioning Context**
  - Typically positioned absolutely relative to parent icon buttons or navigation avatars (e.g., top-right corners) to signal unread alert counts without disrupting underlying layouts.
