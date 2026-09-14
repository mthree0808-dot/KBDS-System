# Design-to-Code Specification: Checkbox with Label and Description Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - CheckboxItemWrapper (Inline flex container)
    - CheckboxIconBox (Interactive 24x24px container housing inner 20x20px box and check/indeterminate indicator)
      - InnerBoxLayer (Rounded box with outline or background fill)
      - IconIndicatorLayer (Checkmark `svg` / Check icon or Indeterminate horizontal bar)
    - TextContentContainer (Flex column alignment)
      - LabelText ("레이블", supports bold/medium weights and various sizes)
      - DescriptionText ("디스크립션", secondary caption)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-checked` | State | `true`, `false` |
| `data-disabled` | State | `true`, `false` |
| `data-indeterminate` | State | `true`, `false` |
| `data-invalid` | State | `true`, `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Checkbox Wrapper Gap: 8px (Between box and text content)
  - Text Content Gap: 4px (Between label and description)
  - Checkbox Outer Frame: Width 24px, Height 24px, Border Radius: 8px
  - Checkbox Inner Target Box: Width 20px, Height 20px, Left/Top offset: 2px, Border Radius: 6px
- **폰트 및 타이포그래피 스펙**
  - Label Text: Font Family `KBFG Text`, Sizes: `16px` (Line-height 22px) or `14px` (Line-height 20px), Weights: `700` (Bold) or `500` (Medium)
  - Description Text: Font Family `KBFG Text`, Sizes: `14px` (Line-height 20px) or `13px` (Line-height 18px), Weight: `300` (Light)

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Variant | Background Token | Text / Icon Token | Outline / Border Token |
| :--- | :--- | :--- | :--- |
| **Default Unchecked** | `transparent` | `var(--icon-accent-brand-alt, #111827)` (10% opacity icon) | `var(--border-neutral-quaternary, #9CA3AF)` (1px solid) |
| **Checked State** | `var(--surface-accent-brand-alt, #111827)` | `var(--icon-neutral-primary-on, white)` | `transparent` |
| **Indeterminate State** | `var(--surface-accent-brand-alt, #111827)` | `var(--icon-neutral-primary-on, white)` | `transparent` |
| **Invalid / Error State** | `var(--surface-status-negative, #E53838)` (if checked) | `var(--text-status-negative, #E53838)` (Label) | `var(--border-status-negative, #E53838)` (1px solid) |
| **Disabled State** | `var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10))` | `var(--text-neutral-disabled, #9CA3AF)` | `transparent` |

## 6. 구현 가이드라인
- **Box Model & Indeterminate Alignment**
  - The checkbox indicator uses a nested container layout to ensure precise offset positioning (`2px` inset) for the inner `20x20px` interactive target.
  - Indeterminate states render a centered horizontal bar (`12.14px` width, `2.14px` height) inside the box container instead of a full checkmark glyph.
- **Validation & State Handling**
  - When `data-invalid="true"`, border tokens and label text colors automatically pivot to error status tokens (`#E53838`) to maintain visual accessibility during form validation failures.
- **Disabled State Interaction**
  - Disabled checkboxes suppress hover and active states, applying a uniform disabled background token (`rgba(102, 112, 133, 0.10)`) and text token (`#9CA3AF`) across all child elements.
