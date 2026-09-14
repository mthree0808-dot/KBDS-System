# Design-to-Code Specification: Radio Button with Label and Description Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - RadioItemWrapper (Inline flex container)
    - RadioIconBox (Interactive 24x24px container housing inner 20x20px circle indicator)
      - InnerCircleLayer (Circular radio track with outline or solid accent fill)
      - SelectedDotIndicator (Center active dot indicator for selected state)
    - TextContentContainer (Flex column alignment)
      - LabelText ("레이블", supports bold/medium weights and various sizes)
      - DescriptionText ("디스크립션", secondary caption)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-checked` | State | `true`, `false` |
| `data-disabled` | State | `true`, `false` |
| `data-invalid` | State | `true`, `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Radio Wrapper Gap: 8px (Between radio button control and text content)
  - Text Content Gap: 4px (Between label and description)
  - Radio Outer Frame: Width 24px, Height 24px, Border Radius: 9999px (Fully rounded)
  - Radio Inner Target Circle: Width 20px, Height 20px, Left/Top offset: 2px, Border Radius: 9999px
- **폰트 및 타이포그래피 스펙**
  - Label Text: Font Family `KBFG Text`, Sizes: `16px` (Line-height 22px) or `14px` (Line-height 20px), Weights: `700` (Bold) or `500` (Medium)
  - Description Text: Font Family `KBFG Text`, Sizes: `14px` (Line-height 20px) or `13px` (Line-height 18px), Weight: `300` (Light)

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Variant | Background Token | Text / Indicator Token | Outline / Border Token |
| :--- | :--- | :--- | :--- |
| **Default Unchecked** | `transparent` | N/A | `var(--border-neutral-quaternary, #9CA3AF)` (1px solid) |
| **Checked State** | `var(--border-accent-brand-alt, #111827)` | `var(--icon-neutral-primary-on, white)` (Center dot) | `transparent` |
| **Invalid / Error State** | `var(--border-status-negative, #E53838)` (if checked) | `var(--text-status-negative, #E53838)` (Label) | `var(--border-status-negative, #E53838)` (1px solid) |
| **Disabled State** | `var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10))` | `var(--text-neutral-disabled, #9CA3AF)` | `transparent` |

## 6. 구현 가이드라인
- **Circular Geometry & Inner Alignment**
  - Radio button inputs use fully rounded geometry (`borderRadius: 9999px`) across both outer containers and inner selection dots to guarantee a perfect circle presentation.
- **Validation & State Propagation**
  - When `data-invalid="true"`, border tokens and label text colors pivot to error status tokens (`#E53838`) to maintain form accessibility standards during validation failures.
- **Disabled State Interaction**
  - Disabled radio controls suppress active hover states, applying uniform disabled background tokens (`rgba(102, 112, 133, 0.10)`) and text tokens (`#9CA3AF`) across all child nodes.
