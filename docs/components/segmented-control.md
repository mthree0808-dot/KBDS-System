# Design-to-Code Specification: Segmented Control / Tab Switcher Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - ControlGroupContainer (Flex column layout)
    - LabelHeaderSection (Optional title header with required badge and info tooltip)
      - TitleText ("타이틀입니다", 14px bold KBFG Text)
      - RequiredBadge ("(필수)", 11px accent red)
      - TooltipIconButton (`16x16px` icon container)
    - SegmentedTrackContainer (Muted surface track with rounded corners)
      - SegmentItem (Flex item supporting selected, default, and disabled states)
        - SegmentLabelText ("텍스트", 12px / 15px KBFG Text)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-selected` | State | `true` (Active tab), `false` (Inactive tab) |
| `data-disabled` | State | `true`, `false` |
| `data-required` | Boolean | `true` |
| `data-tooltip` | Boolean | `true` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Track Container Padding: 4px padding on all sides, Radius: 12px (Standard size) or 10px (Small size)
  - Segment Item Min-Height: 40px (Standard) or min-width 26px (Small pill tabs)
  - Segment Item Radius: 8px (Standard) or 6px (Small tabs)
- **타이포그래피 스펙**
  - Header Title Text: Font Family `KBFG Text`, Size 14px, Weight 700 (Bold), Line-height 20px
  - Selected Segment Text: Font Family `KBFG Text`, Size 15px (Standard) / 12px (Small), Weight 700 (Bold)
  - Unselected Segment Text: Font Family `KBFG Text`, Size 15px (Standard) / 12px (Small), Weight 500 (Medium)

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Element | Background Token | Text / Label Token | Shadow / Elevation Token |
| :--- | :--- | :--- | :--- |
| **Segment Track Container** | `var(--surface-neutral-secondary-muted, #F4F6F9)` | N/A | `transparent` |
| **Selected Segment Item** | `var(--surface-neutral-quaternary-muted, white)` | `var(--text-neutral-primary, #111827)` | `0px 2px 4px -1px rgba(12, 17, 29, 0.10)` |
| **Unselected Segment Item** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` | `transparent` |
| **Disabled Segment Track** | `var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10))` | `var(--text-neutral-disabled, #9CA3AF)` | `transparent` |

## 6. 구현 가이드라인
- **Segment Flex Distribution & Elevation**
  - Segment items share equal width distribution (`flex: '1 1 0'`) across the track container, utilizing distinct shadow tokens (`0px 2px 4px -1px rgba(12, 17, 29, 0.10)`) to lift the active tab visually from the background surface.
- **Disabled State Handling**
  - When `data-disabled="true"`, both the track background and active indicators switch to disabled surface tokens (`rgba(102, 112, 133, 0.10)`), and text tokens pivot uniformly to `#9CA3AF`.
