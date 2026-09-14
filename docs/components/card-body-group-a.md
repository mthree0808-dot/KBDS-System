# Design-to-Code Specification: Section Title, Subtitle & Metadata Typography Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - ContentWrapperGroup (Absolute positioned vertical stacks for headers and descriptive blocks)
    - HeadingLevel1Text ("타이틀입니다", 20px bold KBFG Text)
    - HeadingLevel2Text ("타이틀입니다", 17px bold KBFG Text)
    - HeadingLevel3Text ("타이틀입니다", 15px bold KBFG Text)
    - InlineActionTextButton (XSmall secondary button with trailing icon slot)
      - ButtonLabelText ("버튼명", 12px bold KBFG Text)
      - TrailingIconAsset (`16x16px` bounding box with neutral quaternary vector)
    - DescriptionBodyText ("디스크립션", 14px medium KBFG Text)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-size` | Dimension | `xsmall` (Action button), `heading-lg`, `heading-md`, `heading-sm` |
| `data-variant` | Variant | `secondary` (Button variant) |
| `data-hassuffix` | Boolean | `true` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Content Container Width: 310px fixed max width across all text groups
  - Positioning: Absolute positioning offsets (`left: 20px`, `top: 80px`, `148px`, `212px`, `273px`, `330px`)
  - Action Button Gap: 2px spacing between button text and trailing icon
- **타이포그래피 및 아이콘 스펙**
  - Heading Level 1 (20px): Font Family `KBFG Text`, Size 20px, Weight 700 (Bold), Line-height 28px
  - Heading Level 2 (17px): Font Family `KBFG Text`, Size 17px, Weight 700 (Bold), Line-height 24px
  - Heading Level 3 (15px): Font Family `KBFG Text`, Size 15px, Weight 700 (Bold), Line-height 21px
  - Description Text: Font Family `KBFG Text`, Size 14px, Weight 500 (Medium), Line-height 20px
  - Action Button Text: Font Family `KBFG Text`, Size 12px, Weight 700 (Bold), Line-height 17px, Trailing Icon: 16x16px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Typography Element | Background Token | Text / Icon Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Primary Headings** | `transparent` | `var(--text-neutral-primary, #111827)` | `transparent` |
| **Description Text** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` | `transparent` |
| **Inline Action Button** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` / `var(--icon-neutral-quaternary, #9CA3AF)` | `transparent` |

## 6. 구현 가이드라인
- **Typography Scale Hierarchy**
  - Section headers enforce a strict proportional scale (`20px`, `17px`, `15px`) using the `KBFG Text` font family with bold weighting to maintain clear document structure and scannability across financial views.
- **Inline Action Button Integration**
  - Compact inline action buttons use an xsmall dimension token with a trailing icon slot, maintaining touch-friendly alignment alongside section headers without requiring full-width container blocks.
