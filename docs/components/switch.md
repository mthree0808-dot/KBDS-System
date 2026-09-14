# Design-to-Code Specification: Toggle Switch Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - ToggleSwitchTrack (Pill-shaped container supporting active, inactive, and disabled states)
    - ToggleThumbHandle (Circular sliding knob, sizes 24px, 16px, or 12px)
    - StateLabelText ("켜짐" / "꺼짐", optional text inside track or badge area)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-state` | State | `on` (Checked), `off` (Unchecked), `disabled` |
| `data-size` | Dimension | `large` (24px thumb), `medium` (16px thumb), `small` (12px thumb) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Track Border Radius: 9999px (Fully rounded pill shape)
  - Toggle Switch Track Padding: 4px padding on all sides
  - Min-Width Variants: 42px (Large/Medium) or 34px (Small)
- **핸들 및 타이포그래피 스펙**
  - Large Thumb Handle: Size 24x24px, Radius: 9999px
  - Medium Thumb Handle: Size 16x16px, Radius: 9999px
  - Small Thumb Handle: Size 12x12px, Radius: 9999px
  - State Label Text: Font Family `KBFG Text`, Size 12px, Weight 700 (Bold) or 500 (Medium), Line-height 17px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Variant | Track Background Token | Thumb Handle Token | Label / Text Token |
| :--- | :--- | :--- | :--- |
| **On / Active State** | `var(--surface-accent-brand-alt, #111827)` | `var(--surface-neutral-quaternary-muted, white)` | `var(--text-neutral-primary-on, white)` |
| **Off / Inactive State** | `var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10))` | `var(--surface-neutral-quaternary-muted, white)` | `var(--text-neutral-placeholder, #9CA3AF)` |
| **Disabled Active State** | `var(--surface-accent-brand-alt-disabled, #6B7280)` | `var(--surface-neutral-primary-muted, #ECEEF2)` (Opacity 0.30) | `var(--text-neutral-secondary-on, #D1D5DB)` |
| **Disabled Inactive State** | `var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10))` | `var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10))` | `var(--text-neutral-disabled, #9CA3AF)` |

## 6. 구현 가이드라인
- **Sliding Animation & Track Alignment**
  - Toggle switches utilize flex alignment (`justify-content: flex-end` for active states vs `flex-start` for inactive states) to handle thumb handle repositioning dynamically inside the pill track.
- **Opacity Rules for Disabled Handles**
  - Disabled thumbs incorporate explicit opacity overrides (`opacity: 0.30`) over muted surface tokens (`#ECEEF2`) to clearly delineate non-interactive switch controls.
