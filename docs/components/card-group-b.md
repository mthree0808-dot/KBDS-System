# Design-to-Code Specification: Financial Rates, Metadata Metadata & Status Alert Line Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - ContentWrapperGroup (Absolute positioned inline flex containers for financial data display)
    - FinancialRateInlineRow (Inline flex container separated by bullet dots)
      - InterestRateHighlight ("연2%~10%", 14px bold KBFG Text with blue accent)
      - BulletSeparatorText ("∙", 15px Pretendard medium font)
      - ConditionMetadataText ("24개월 기준", 14px medium KBFG Text)
    - AccountMetadataInfoRow (Single-line secondary account info text)
      - MetadataTextLabel ("기타 계좌 정보 기타 계좌 정보", 14px medium KBFG Text)
    - StatusAlertCalloutRow (Muted red container wrapping warning text with a trailing chevron link)
      - AlertMessageText ("출금계좌 등록이 필요합니다", 12px bold KBFG Text with negative status tone)
      - TrailingChevronIconSlot (`16x16px` bounding box with rotated arrow asset)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-size` | Dimension | `xsmall` (Status alert button) |
| `data-variant` | Variant | `primary` (Alert variant) |
| `data-hassuffix` | Boolean | `true` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Container Width: 310px fixed max width across all metadata rows
  - Positioning: Absolute positioning offsets (`left: 20px`, `top: 80px`, `140px`, `200px`)
  - Status Alert Container Padding: Top/Bottom 4px, Left 8px, Right 2px, Radius: 8px
  - Element Gap: 4px spacing between inline rate text components and alert label/icon elements
- **타이포그래피 및 아이콘 스펙**
  - Interest Rate Highlight: Font Family `KBFG Text`, Size 14px, Weight 700 (Bold), Line-height 20px
  - Condition & Metadata Text: Font Family `KBFG Text`, Size 14px, Weight 500 (Medium), Line-height 20px
  - Status Alert Text: Font Family `KBFG Text`, Size 12px, Weight 700 (Bold), Line-height 17px
  - Trailing Chevron Icon: Size 16x16px bounding box with 180-degree rotation transform

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Element | Background Token | Text / Icon Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Interest Rate Highlight** | `transparent` | `var(--text-accent-blue, #1F6AFF)` | `transparent` |
| **Bullet & Metadata Text** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` | `transparent` |
| **Status Alert Container** | `var(--surface-accent-red-muted, #FFF6F5)` | N/A | `transparent` |
| **Status Alert Text & Icon** | `transparent` | `var(--text-status-negative, #E53838)` / `var(--icon-status-negative, #E53838)` | `transparent` |

## 6. 구현 가이드라인
- **Inline Rate & Bullet Alignment**
  - Financial rate rows combine colored highlight values with neutral secondary metadata using bullet separators (`∙`) and tight inline gaps (`4px`) to preserve readability across compact card layouts.
- **Muted Status Alert Callouts**
  - Status alert rows utilize a soft red background tint (`#FFF6F5`) with rounded corners (`8px`) and negative status text coloring (`#E53838`) to highlight necessary user actions (e.g., account registration requirements) effectively.
