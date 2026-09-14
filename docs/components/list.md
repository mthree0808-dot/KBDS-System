# Design-to-Code Specification: List Item with Icon, Title, Subtitle & Trailing Chevron Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with horizontal padding 20px, vertical padding 12px, flex column layout)
  - ListItemRowContainer (Inline flex row with 8px gap)
    - LeadingIconContainer (24x24px icon bounding box with 18x18px primary neutral vector)
    - TextContentWrapper (Flex column layout with 4px gap)
      - TitleText ("타이틀입니다(15)", 15px bold KBFG Text)
      - DescriptionText ("디스크립션(13)", 13px light KBFG Text)
    - TrailingActionContainer (24x24px navigation chevron icon slot)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-variant` | Variant | `icon`, `pageIndicator` |
| `data-size` | Dimension | `24px` (Icon and chevron container size) |
| `data-disabled` | State | `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Root Padding: Horizontal 20px, Vertical 12px
  - Element Gap: 8px spacing between outer row items, 12px gap between leading icon, text group, and chevron
  - Text Stack Gap: 4px spacing between title and description
- **타이포그래피 및 아이콘 스펙**
  - Title Text: Font Family `KBFG Text`, Size 15px, Weight 700 (Bold), Line-height 21px
  - Description Text: Font Family `KBFG Text`, Size 13px, Weight 300 (Light), Line-height 18px
  - Leading Icon Bounding Box: Size 24x24px (Vector icon: 18x18px)
  - Trailing Chevron Icon: Size 24x24px bounding box with 180-degree rotation transform

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Element | Background Token | Text / Icon Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Root Container Surface** | `transparent` | N/A | `transparent` |
| **Title Text** | `transparent` | `var(--text-neutral-primary, #111827)` | `transparent` |
| **Description Text** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` | `transparent` |
| **Leading Icon Graphic** | `transparent` | `var(--icon-neutral-primary, #111827)` | `transparent` |
| **Trailing Chevron Icon** | `transparent` | `var(--icon-neutral-quaternary, #9CA3AF)` | `transparent` |

## 6. 구현 가이드라인
- **Flexible Row Sourcing**
  - List items utilize a flexible middle column (`flex: '1 1 0'`) to ensure title and subtitle text wrap cleanly or truncate without overlapping leading icons or trailing navigation chevrons.
- **Touch-Friendly Hit Targets**
  - Consistent vertical padding (`12px`) combined with standard 24px icon slots guarantees accessibility compliance across touch interfaces and mobile viewports.
