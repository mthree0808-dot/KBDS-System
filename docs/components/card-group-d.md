# Design-to-Code Specification: Account Balance Display, Currency Value & Percentage Yield Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - BalanceDisplayWrapperGroup (Absolute positioned inline flex containers for financial balances and rates)
    - LargeBalanceRow (Inline flex row for main account balance with hide action button)
      - BalanceLabelText ("잔액", 14px medium KBFG Text)
      - CurrencyAmountText ("3,000,000", 26px semibold Pretendard font)
      - CurrencyUnitText ("원", 15px medium KBFG Text)
      - ActionTextButton ("숨김", XSmall tertiary button with 6px radius and neutral primary outline)
    - MediumBalanceRow (Inline flex row with trailing navigation chevron)
      - BalanceLabelText ("잔액", 14px medium KBFG Text)
      - CurrencyAmountText ("1,000,000", 20px semibold Pretendard font)
      - CurrencyUnitText ("원", 14px medium KBFG Text)
      - TrailingChevronIconSlot (`20x20px` bounding box with rotated arrow asset)
    - PercentageYieldIndicatorRow (Inline flex row for financial growth or yield percentage)
      - YieldPercentageText ("+00.00%", 13px bold KBFG Text with increase status color)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-size` | Dimension | `xsmall` (Hide action button), `20px` (Chevron container) |
| `data-variant` | Variant | `tertiary`, `primary` |
| `data-disabled` | State | `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Container Width: 310px fixed max width across all balance rows
  - Positioning: Absolute positioning offsets (`left: 20px`, `top: 80px`, `148px`, `213px`)
  - Hide Action Button: Min-height 24px, Padding: Horizontal 4px, Vertical 2px, Radius: 6px
  - Element Gap: 4px to 8px spacing between label, numeric value, currency unit, and action controls
- **타이포그래피 및 아이콘 스펙**
  - Large Balance Amount: Font Family `Pretendard`, Size 26px, Weight 600 (Semibold), Line-height 36px
  - Medium Balance Amount: Font Family `Pretendard`, Size 20px, Weight 600 (Semibold), Line-height 28px
  - Balance Label Text: Font Family `KBFG Text`, Size 14px, Weight 500 (Medium), Line-height 20px
  - Yield Percentage Text: Font Family `KBFG Text`, Size 13px, Weight 700 (Bold), Line-height 18px, Color `#F44F4F` (Increase status)
  - Action Button Text: Font Family `KBFG Text`, Size 12px, Weight 700 (Bold), Line-height 17px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Element | Background Token | Text / Icon Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Balance Label & Unit** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` / `var(--text-neutral-primary, #111827)` | `transparent` |
| **Numeric Currency Value** | `transparent` | `var(--text-neutral-primary, #111827)` | `transparent` |
| **Hide Action Button** | `transparent` | `var(--text-neutral-primary, #111827)` | `1px var(--border-neutral-primary-muted, #D1D5DB) solid` |
| **Percentage Yield Text** | `transparent` | `var(--text-status-increase, #F44F4F)` | `transparent` |

## 6. 구현 가이드라인
- **Typography Pairing (Pretendard & KBFG Text)**
  - Financial numeric values leverage the `Pretendard` font family (weights 600) for enhanced readability of numbers and commas, while accompanying labels and units utilize `KBFG Text` (weights 500/700) in strict alignment with brand design standards.
- **Action Button & Chevron Integration**
  - Account balance rows support interactive utility buttons (such as balance masking "숨김") or trailing navigation chevrons, maintaining compact horizontal alignments (`align-items: center`, `gap: 8px`) across mobile account cards.
