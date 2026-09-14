# Design-to-Code Specification: Account Type / Metadata Tag Breadcrumb Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - BreadcrumbRowContainer (Inline flex container for account tags and vertical dividers)
    - AccountTagItem (Text item supporting primary brand or secondary neutral colors)
      - TagLabelText ("주계좌", "모임통장", "한도계좌", 11px bold KBFG Text)
    - VerticalDividerLine (`1px` width, quartenary border token with padding)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-length` | Dimension | `full` (Divider height behavior) |
| `data-tone` | Tone | `brand` (Accent brand alt), `secondary` (Neutral dark) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Item Gap: 6px to 10px spacing between account tags and divider lines
  - Vertical Divider Padding: Top/Bottom 4px padding enclosing a `1px` width line (`flex: '1 1 0'`)
- **타이포그래피 스펙**
  - Tag Label Text: Font Family `KBFG Text`, Size 11px, Weight 700 (Bold), Line-height 15px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Element | Background Token | Text / Line Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Primary Account Tag** | `transparent` | `var(--text-accent-brand-alt, #111827)` | `transparent` |
| **Secondary Account Tag** | `transparent` | `var(--text-neutral-secondary, #374151)` | `transparent` |
| **Vertical Divider Line** | `transparent` | `var(--border-neutral-quaternary, #9CA3AF)` | `transparent` |

## 6. 구현 가이드라인
- **Compact Breadcrumb Alignment**
  - Account metadata breadcrumbs utilize inline flex layouts with tight gaps (`6px` to `10px`) to display account classifications (e.g., primary account, club account, limit account) cleanly beneath account titles.
- **Divider Line Flexibility**
  - Vertical dividers apply self-stretch alignment with vertical padding (`4px`) to match text line-height proportions perfectly without disrupting inline text flow.
