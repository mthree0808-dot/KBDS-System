# Design-to-Code Specification: Primary & Secondary Button Component System

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - ButtonComponent (Supports multiple size variants, interaction states, and tonal styles)
    - IconContainer (Optional leading icon asset, sizes 24px, 20px, 16px, or 12px)
    - ButtonLabelText ("버튼명", 18px, 14px, or 12px KBFG Text)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-variant` | Variant | `primary`, `secondary`, `tertiary` |
| `data-size` | Dimension | `large` (56px), `medium` (40px), `small` (32px), `xsmall` (24px) |
| `data-state` | State | `default`, `pressed`, `disabled` |
| `data-pressed` | State | `true`, `false` |
| `data-disabled` | State | `true`, `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Large Button Height: Min-height 56px, Padding: Horizontal 12px, Vertical 2px, Radius: 16px, Gap: 2px
  - Medium Button Height: Min-height 40px, Padding: Horizontal 8px, Vertical 2px, Radius: 10px, Gap: 2px
  - Small Button Height: Min-height 32px, Padding: Horizontal 8px, Vertical 2px, Radius: 8px, Gap: 2px
  - XSmall Button Height: Min-height 24px, Padding: Horizontal 4px, Vertical 2px, Radius: 6px, Gap: 2px
- **타이포그래피 및 아이콘 스펙**
  - Large Button Label: Font Family `KBFG Text`, Size 18px, Weight 700 (Bold), Line-height 25px
  - Medium Button Label: Font Family `KBFG Text`, Size 14px, Weight 700 (Bold), Line-height 20px
  - Small / XSmall Button Label: Font Family `KBFG Text`, Size 12px, Weight 700 (Bold), Line-height 17px
  - Leading Icon Box: Size 24x24px (Large), 20x20px (Medium), 16x16px (Small), 12x12px (XSmall)

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Button Style / State | Background Token | Text / Icon Token | Border / Outline Token |
| :--- | :--- | :--- | :--- |
| **Primary (Default)** | `var(--surface-accent-brand-alt, #111827)` | `var(--text-neutral-primary-on, white)` | `transparent` |
| **Primary (Pressed)** | `linear-gradient(0deg, var(--surface-neutral-pressed, rgba(102, 112, 133, 0.05)), ...), var(--surface-accent-brand-alt)` | `var(--text-neutral-primary-on, white)` | `transparent` |
| **Secondary (Default)** | `var(--surface-neutral-secondary-muted, #F4F6F9)` | `var(--text-accent-brand-alt, #111827)` | `transparent` |
| **Outlined / Tertiary** | `var(--surface-neutral-quaternary-muted, white)` | `var(--text-neutral-primary, #111827)` | `1px var(--border-neutral-primary-muted, #D1D5DB) solid` |
| **Disabled State** | `var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10))` | `var(--text-neutral-disabled, #9CA3AF)` | `transparent` |

## 6. 구현 가이드라인
- **Pressed State Overlay Rendering**
  - Pressed interaction states stack a semi-transparent surface gradient (`rgba(102, 112, 133, 0.05)`) over the base button background token to simulate touch feedback without layout shifts.
- **Icon and Text Scaling**
  - Button height variants scale leading icon boxes and typography line-heights proportionally (e.g., 24px icon with 18px text vs 12px icon with 12px text) to preserve visual balance across all dimension tokens.
