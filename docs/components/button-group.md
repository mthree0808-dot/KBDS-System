# Design-to-Code Specification: Action Button Group Component System

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - ButtonGroupContainer (Supports vertical stacks, horizontal dual/triple splits, and asymmetric widths)
    - PrimaryButton (Large variant, min-height 56px, radius 16px, accent brand background)
    - SecondaryButton (Large variant, min-height 56px, radius 16px, neutral secondary muted background)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-variant` | Variant | `primary`, `secondary` |
| `data-size` | Dimension | `large` (min-height 56px) |
| `data-disabled` | State | `false` |
| `data-pressed` | State | `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Group Container Width: 350px (Standard mobile action footer width)
  - Button Min-Height: 56px, Padding: Horizontal 12px, Vertical 2px
  - Button Corner Radius: 16px (Fully rounded smooth corners)
  - Item Gap: 8px or 12px spacing between stacked/inline buttons
- **타이포그래피 스펙**
  - Button Label Text: Font Family `KBFG Text`, Size 18px, Weight 700 (Bold), Line-height 25px, Text Alignment Center

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Button Variant / Role | Background Token | Text / Icon Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Primary Button** | `var(--surface-accent-brand-alt, #111827)` | `var(--text-neutral-primary-on, white)` | `transparent` |
| **Secondary Button** | `var(--surface-neutral-secondary-muted, #F4F6F9)` | `var(--text-accent-brand-alt, #111827)` | `transparent` |

## 6. 구현 가이드라인
- **Flexible Layout & Asymmetric Sizing**
  - Button groups support single action blocks, vertical column stacking (`gap: 12px`), equal horizontal splits (`flex: '1 1 0'`), triple button layouts, and asymmetric widths (e.g., fixed 108px secondary buttons paired with flexible primary CTAs).
- **Flexbox Alignment & Touch Targets**
  - All button items enforce a minimum height of `56px` with generous touch targets and centered flex alignment to meet mobile financial accessibility requirements.
