# Design-to-Code Specification: Component Analysis & Pipeline Guide

## 1. 피그마 메타데이터
- Library Name: Financial UI Design System Core
- Page: Components / Date Picker
- Component Name: DateRangePicker
- Figma Link: https://www.figma.com/design/... (Placeholder for future code injection)

## 2. 컴포넌트 구조 (Hierarchy)
- DateRangePicker (Root Container)
  - HeaderSection (Month/Year Title, Navigation Controls)
    - PrevButton
    - TitleLabel (Month & Year)
    - NextButton
  - CalendarGridContainer
    - WeekdayHeaderRow (Sun - Sat)
    - DateGrid (7 Columns Uniform Grid)
      - DateCell (Default, Today, Selected, Start/End, Middle, Disabled variants)
        - PseudoBackground (`::before` for range half-fill / connecting bar)
        - DayTextIndicator (32x32px circular interactive layer)
  - FooterSection (Optional Actions: Today Button, Confirm CTA)
    - TodayButton
    - ConfirmCTAButton

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-state` | State | `default`, `today`, `selected`, `range-start`, `range-end`, `range-middle`, `disabled` |
| `data-interaction` | Interactive | `hover`, `active`, `focus` |
| `data-size` | Dimension | `fixed-grid-cell` (40px cell, 32px inner target) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Root Container Width: 320px
  - Root Container Height: Auto (approx. 360px)
  - Root Container Padding: 16px (All sides)
  - Grid Gap: 4px row / column gap
  - Root Container Radius: 12px
- **하위 버튼 및 컨트롤 스펙**
  - Navigation Arrows / Buttons: Min-height 32px, Padding: 6px 8px, Radius: 6px
  - Confirm CTA / Today Button: Min-height 36px, Internal Padding: 8px 16px, Radius: 8px, Font: Pretendard, Size: 14px, Weight: 600 (SemiBold), Line-height: 20px
- **일자 그리드 및 셀 치수**
  - Grid Layout: 7-column uniform split (`grid-template-columns: repeat(7, 1fr)`)
  - Cell Dimension: Width 40px, Height 40px
  - Inner Circular Target: Width 32px, Height 32px, Radius: 16px (Perfect circle)

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State | Background Token | Text/Icon Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Default** | `var(--color-bg-surface)` | `var(--color-text-primary)` | `transparent` |
| **Today** | `var(--color-bg-surface)` | `var(--color-primary-600)` | `var(--color-primary-600)` (1px solid) |
| **Selected / Start / End** | `var(--color-primary-600)` | `var(--color-text-inverse)` | `transparent` |
| **Range Middle** | `var(--color-primary-50)` | `var(--color-primary-900)` | `transparent` |
| **Disabled** | `var(--color-bg-disabled)` | `var(--color-text-disabled)` | `transparent` |

## 6. 구현 가이드라인
- **Range Cell & Virtual Element Rendering (`::before`)**
  - Range selection spanning multiple cells utilizes CSS pseudo-elements (`::before`) for background color bridging without layout shifts.
  - Middle range cells apply a solid horizontal block background (`width: 100%`, `height: 32px`, `background: var(--color-primary-50)`).
  - Start and End cells render a half-fill background (`width: 50%`, `height: 32px`) positioned absolutely to extend outward toward the connecting direction.
  - Circular date indicator (`32x32px`) maintains `z-index: 2` to sit cleanly above the range connector bar (`z-index: 1`), ensuring clear visual distinction for interactive touch targets.
