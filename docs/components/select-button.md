# Design-to-Code Specification: Chip / Filter Pill Selection Group Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - ChipGroupContainer (Vertical flex layout with header label)
    - TitleHeaderSection (Optional section title, required tag "(필수)", and info tooltip icon)
    - ChipFlexWrapContainer (Flexbox container supporting wrap alignment and 8px item gaps)
      - FilterChipItem (Min-height 48px, rounded 12px, supporting selected and unselected states)
        - ChipLabelText ("선택" or "선택선택", 15px bold KBFG Text)
        - TrailingCheckboxIcon (Optional 24x24px checkbox or indicator icon within chip)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-selected` | State | `true` (Active selected chip), `false` (Inactive chip) |
| `data-checked` | State | `true`, `false` |
| `data-required` | Boolean | `true`, `false` |
| `data-tooltip` | Boolean | `true`, `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Chip Item Min-Height: 48px, Padding: Top/Bottom 2px, Left 16px, Right 12px
  - Chip Border Radius: 12px (Smooth rounded pill container)
  - Element Gap: 8px spacing between wrapped chips
- **타이포그래피 스펙**
  - Section Title Text: Font Family `KBFG Text`, Size 14px, Weight 700 (Bold), Line-height 20px
  - Chip Label Text: Font Family `KBFG Text`, Size 15px, Weight 700 (Bold), Line-height 21px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Chip State / Element | Background Token | Text / Icon Token | Border / Outline Token |
| :--- | :--- | :--- | :--- |
| **Selected Chip State** | `var(--surface-accent-brand-alt, #111827)` | `var(--text-neutral-primary-on, white)` | `transparent` |
| **Unselected Chip State** | `var(--surface-neutral-quaternary-muted, white)` | `var(--text-neutral-tertiary, #4B5563)` | `1px var(--border-neutral-primary-muted, #D1D5DB) solid` |
| **Unselected Checkbox Icon** | `transparent` | `var(--icon-neutral-quaternary, #9CA3AF)` | `transparent` |

## 6. 구현 가이드라인
- **Flexbox Wrap & Alignment**
  - Chip groups utilize flex wrapping (`flexWrap: 'wrap'`, `alignContent: 'center'`) to accommodate variable text lengths and multi-row filter selections fluidly within mobile width limits (`350px`).
- **State Feedback & Checkbox Integration**
  - Selected chips invert color tokens completely to brand accent fills (`#111827`) with matching white icons, while unselected chips maintain crisp neutral borders (`#D1D5DB`) and quaternary icon tints (`#9CA3AF`).
