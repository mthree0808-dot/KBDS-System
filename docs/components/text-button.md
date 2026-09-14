# Design-to-Code Specification: Text Link Button Component System

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - TextLinkButtonComponent (Inline flex container supporting icons, typography sizing, and underlines)
    - IconContainer (Leading icon asset, sizes 24px, 20px, 16px)
    - LabelContainer (Relative wrapper for text and bottom underline stroke)
      - LinkTextLabel ("버튼명", 22px, 16px, 14px, or 12px bold KBFG Text)
      - UnderlineBorderLine (Absolute positioned bottom accent or neutral line outline)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-size` | Dimension | Large (22px text), Medium (16px text), Small (14px text), XSmall (12px text) |
| `data-state` | State | `default`, `pressed`, `disabled` |
| `data-tone` | Tone | `brand` (Accent brand alt), `neutral` (Quaternary), `disabled` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Item Alignment: Flex row centered vertically (`align-items: center`), gap: 2px between icon and label
  - Border Radius: 8px (Container interactive wrapper)
- **타이포그래피 및 밑줄 스펙**
  - Large Text Link: Font Family `KBFG Text`, Size 22px, Weight 700 (Bold), Line-height 31px, Underline outline 1.60px
  - Medium Text Link: Font Family `KBFG Text`, Size 16px, Weight 700 (Bold), Line-height 22px, Underline outline 1.0px
  - Small Text Link: Font Family `KBFG Text`, Size 14px, Weight 700 (Bold), Line-height 20px, Underline outline 1.0px
  - XSmall Text Link: Font Family `KBFG Text`, Size 12px, Weight 700 (Bold), Line-height 17px, Underline outline 1.0px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Link Style / State | Background Token | Text / Icon Token | Underline Stroke Token |
| :--- | :--- | :--- | :--- |
| **Brand Tone (Default)** | `transparent` | `var(--text-accent-brand-alt, #111827)` | `var(--border-accent-brand-alt, #111827)` |
| **Brand Tone (Pressed)** | `var(--surface-neutral-pressed, rgba(102, 112, 133, 0.05))` | `var(--text-accent-brand-alt, #111827)` | `var(--border-accent-brand-alt, #111827)` |
| **Neutral Tone (Default)** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` | `var(--border-neutral-quaternary, #9CA3AF)` |
| **Disabled State** | `transparent` | `var(--text-neutral-disabled, #9CA3AF)` | `var(--border-neutral-disabled, #D1D5DB)` |

## 6. 구현 가이드라인
- **Absolute Underline Positioning**
  - Text link underlines use absolute positioning (`top: 31px`, `22px`, `20px`, or `17px` matching respective line-heights) with explicit width matching text bounds (`60px`, `44px`, `38px`, `33px`) to render bottom border outlines cleanly.
- **Pressed State Background Feedback**
  - Pressed states apply a subtle container background (`rgba(102, 112, 133, 0.05)`) with rounded corners (`borderRadius: 8px`) to provide visual touch feedback without shifting inline text flow.
