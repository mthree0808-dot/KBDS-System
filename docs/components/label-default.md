# Design-to-Code Specification: Accent Tag / Category Label Component System

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - TagItemContainer (Rectangular pill container supporting solid accents, muted tones, and outlined border styles)
    - TagLabelText ("레이블", 11px bold KBFG Text)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-tone` | Tone | `red`, `orange`, `yellow`, `olive`, `celery`, `green`, `seafoam`, `cyan`, `blue`, `indigo`, `purple`, `fuchsia`, `magenta`, `monotone` |
| `data-variant` | Variant | `solid`, `muted`, `outlined` |
| `data-size` | Dimension | `20px` (Min-height container) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Tag Min-Height: 20px, Min-Width: 20px
  - Padding: Horizontal 6px, Vertical 0px (Outlined / Muted variants use consistent inner padding)
  - Border Radius: 4px (Soft rounded rectangular geometry)
- **타이포그래피 스펙**
  - Tag Label Text: Font Family `KBFG Text`, Size 11px, Weight 700 (Bold), Line-height 15px, Text Center

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Tag Variant / Tone | Background Token | Text Token | Border / Outline Token |
| :--- | :--- | :--- | :--- |
| **Solid Red Accent** | `var(--surface-accent-red, #F44F4F)` | `var(--text-neutral-primary-on, white)` | `transparent` |
| **Muted Red Variant** | `var(--surface-accent-red-muted, #FFF6F5)` | `var(--text-accent-red, #E53838)` | `transparent` |
| **Outlined Red Variant** | `transparent` | `var(--text-accent-red, #E53838)` | `1px var(--border-accent-red, #F96161) solid` |
| **Solid Seafoam Accent** | `var(--surface-accent-seafoam, #007772)` | `var(--text-neutral-primary-on, white)` | `transparent` |
| **Muted Seafoam Variant** | `var(--surface-accent-seafoam-muted, #EDFCFB)` | `var(--text-accent-seafoam, #007772)` | `transparent` |
| **Outlined Seafoam Variant** | `transparent` | `var(--text-accent-seafoam, #007772)` | `1px var(--border-accent-seafoam, #00A19A) solid` |

## 6. 구현 가이드라인
- **Border Radius & Shape Consistency**
  - Unlike circular notification dots, accent category tags utilize a softer rectangular radius (`borderRadius: 4px`) and a fixed height of `20px` to distinguish category classifications from unread count indicators.
- **Outlined State with Negative Offsets**
  - Outlined variants apply explicit semantic border color tokens (e.g., `#F96161`, `#00A19A`) with negative outline offsets (`outlineOffset: '-1px'`) to maintain exact geometric proportions inside layout grids.
