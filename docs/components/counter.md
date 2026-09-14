# Design-to-Code Specification: Stepper / Counter Control Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - StepperControlGroup (Inline flex container with 4px gap)
    - DecrementButton (Minus action control button, rounded 6px, surface white with subtle shadow)
    - ValueDisplayBox (Min-height 32px, min-width 38px, container for current numeric value)
      - NumericValueText ("999" or "1", 16px KBFG Text)
    - IncrementButton (Plus action control button, rounded 6px, surface white with subtle shadow)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-disabled` | State | `true`, `false` |
| `data-pressed` | State | `false` |
| `data-size` | Dimension | `16` (Icon size) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Stepper Control Item Gap: 4px spacing between buttons and value display box
  - Action Button Padding: 8px (Square bounding box with 6px border radius)
  - Value Box Height: 32px, Min-Width: 38px, Padding: Horizontal 4px, Vertical 8px, Radius: 6px
- **타이포그래피 및 아이콘 스펙**
  - Control Icons: Size 16x16px bounding box (Minus line asset: 10.33x1px, Plus cross asset: 10.33x10.33px)
  - Numeric Value Text: Font Family `KBFG Text`, Size 16px, Weight 500 (Medium) / 700, Line-height 22px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Element | Background Token | Text / Icon Token | Border / Shadow Token |
| :--- | :--- | :--- | :--- |
| **Active Stepper Button** | `var(--surface-neutral-quaternary-muted, white)` | `var(--icon-neutral-primary, #111827)` | `0px 2px 4px -1px rgba(12, 17, 29, 0.10)`, 1px solid `var(--border-neutral-primary-muted, #D1D5DB)` |
| **Active Value Display** | `transparent` | `var(--text-neutral-primary, #111827)` | `0px 4px 6px rgba(12, 17, 29, 0.10)` |
| **Disabled Stepper Button** | `linear-gradient(0deg, var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10)) 0%, ...)` | `var(--icon-neutral-disabled, #D1D5DB)` | `0px 2px 4px -1px rgba(12, 17, 29, 0.10)` |
| **Disabled Value Display** | `transparent` | `var(--text-neutral-disabled, #9CA3AF)` | `0px 4px 6px rgba(12, 17, 29, 0.10)` |

## 6. 구현 가이드라인
- **Compact Flex Alignment & Grouping**
  - Stepper controls group decrement and increment buttons tightly around the central numeric display using inline flex layouts (`gap: 4px`) with consistent 6px border radii across all elements.
- **Disabled State Gradient Layering**
  - Disabled buttons apply a combined background token stack using linear gradients over white surfaces to produce a flattened, non-interactive visual treatment.
