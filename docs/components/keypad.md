# Design-to-Code Specification: Numeric Keypad / Security Keypad Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - KeypadBottomSheetContainer (Width: 390px, Background: White)
    - QuickAmountSelectorBar (Optional pill buttons for quick values like "전액", "100만", "10만", "5만", "1만")
    - KeypadGridSection (Grid layout for numbers 0-9, 00, refresh/shuffle, and backspace/remove)
      - KeypadButtonCell (Height 60px, rounded 12px interactive touch target)
        - NumericKeyText (22px bold KBFG Text) or ActionIcon
    - FooterCTASection (Primary confirm button container, min-height 56px, radius 16px)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-variant` | Variant | `amount`, `security`, `numeric`, `remove`, `refresh` |
| `data-pressed` | State | `true`, `false` |
| `data-hascta` | Boolean | `true` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Keypad Sheet Width: 390px
  - Keypad Button Cell Height: 60px, Padding: 4px
  - Quick Amount Pill Height: Min-height 32px, Padding: 8px, Radius: 9999px
- **컨트롤 및 버튼 스펙**
  - Numeric Key Font: Font Family `KBFG Text`, Size 22px, Weight 700 (Bold), Line-height 31px
  - Quick Amount Pill Font: Font Family `KBFG Text`, Size 12px, Weight 700 (Bold), Line-height 17px
  - Confirm CTA Button: Min-height 56px, Radius: 16px, Background: `var(--surface-accent-brand-alt)`

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Element | Background Token | Text / Icon Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Keypad Surface** | `var(--background-neutral-white, white)` | N/A | `transparent` |
| **Quick Amount Pill** | `var(--surface-neutral-secondary-muted, #F4F6F9)` | `var(--text-accent-brand-alt, #111827)` | `transparent` |
| **Keypad Cell Text** | `transparent` | `var(--text-neutral-primary, #111827)` | `transparent` |
| **Confirm CTA Button** | `var(--surface-accent-brand-alt, #111827)` | `var(--text-neutral-primary-on, white)` | `transparent` |

## 6. 구현 가이드라인
- **Security Keypad Shuffling & Layouts**
  - Security variants support randomized number sequencing (e.g., shuffling digits 0-9) to prevent pattern tracking, with refresh/shuffle triggers (`data-variant="refresh"`) updating cell mappings dynamically.
- **Touch Target Optimization**
  - Each keypad cell enforces a strict 60px height with centered text alignment and generous padding to ensure reliable touch registration on mobile viewports.
