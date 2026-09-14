# Design-to-Code Specification: Floating Action Button (FAB) Component System

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - FloatingActionButtonWrapper (Elevated floating container supporting icon-only and extended label variants)
    - LeadingIconContainer (Icon asset bounding box, fixed 24x24px dimensions)
    - ButtonLabelText ("Button", optional text label, 16px bold KBFG Text)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-variant` | Variant | `primary`, `secondary` (Elevated white surface) |
| `data-state` | State | `default`, `pressed`, `disabled` |
| `data-size` | Dimension | `extended` (Label + Icon), `icon-only` (Circular 48px height) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - FAB Container Height: Min-height 48px, Padding: 12px all sides
  - Border Radius: 24px (Fully rounded pill shape for extended FAB or circular container for icon-only variants)
  - Element Gap: 4px spacing between leading icon and button label text
- **타이포그래피 및 아이콘 스펙**
  - Button Label Text: Font Family `KBFG Text`, Size 16px, Weight 700 (Bold), Line-height 22px
  - Leading Icon Box: Size 24x24px bounding box (Icon vector: 18.66x5.81px)
  - Box Shadow Elevation: `0px 4px 6px rgba(12, 17, 29, 0.10)` across all variants

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| FAB Style / State | Background Token | Text / Icon Token | Elevation / Shadow Token |
| :--- | :--- | :--- | :--- |
| **Primary (Default)** | `var(--surface-accent-brand-alt, #111827)` | `var(--text-neutral-primary-on, white)` | `0px 4px 6px rgba(12, 17, 29, 0.10)` |
| **Primary (Pressed)** | `linear-gradient(0deg, var(--surface-neutral-pressed, rgba(102, 112, 133, 0.05)), ...), var(--surface-accent-brand-alt)` | `var(--text-neutral-primary-on, white)` | `0px 4px 6px rgba(12, 17, 29, 0.10)` |
| **Secondary (Default)** | `var(--background-neutral-elevated, white)` | `var(--text-neutral-primary, #111827)` | `0px 4px 6px rgba(12, 17, 29, 0.10)` |
| **Secondary (Pressed)** | `linear-gradient(0deg, var(--surface-neutral-pressed, rgba(102, 112, 133, 0.05)), ...), var(--background-neutral-elevated)` | `var(--text-neutral-primary, #111827)` | `0px 4px 6px rgba(12, 17, 29, 0.10)` |
| **Disabled State** | `var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10))` | `var(--text-neutral-disabled, #9CA3AF)` | `0px 4px 6px rgba(12, 17, 29, 0.10)` |

## 6. 구현 가이드라인
- **Elevation & Drop Shadows**
  - Floating action buttons enforce a standard elevation shadow token (`0px 4px 6px rgba(12, 17, 29, 0.10)`) to maintain visual prominence above scrollable viewports.
- **Icon-Only vs. Extended Morphing**
  - Icon-only variants collapse text padding while retaining the 48px height and 24px internal icon centering, whereas extended variants incorporate flexible label padding (`padding: 12px` symmetric) with a 4px gap.
