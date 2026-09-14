# Design-to-Code Specification: Promo / Informational Illustration Card Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - CardContainer (Width: 350px, supporting neutral or brand-accented muted surfaces)
    - TextContentWrapper (Flex column layout for main titles, subtitles, and emphasis tags)
      - EmphasisSubLabelText (Optional category or accent subtitle, 14px medium KBFG Text)
      - MainTitleText ("메인텍스트 최대 N자", 16px/17px/18px bold KBFG Text)
      - DescriptionBodyText (Secondary descriptive text, 14px light KBFG Text)
    - IllustrationAssetContainer (Trailing image slot containing 80x80px or 96x96px graphics)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-variant` | Variant | `neutral-secondary`, `brand-accent-muted` |
| `data-size` | Dimension | `standard` (102px height), `tall` (132px height), `large` (148px height) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Card Width: 350px fixed across all card variants
  - Standard Card Height: 102px, Padding: Top/Bottom 12px, Left 20px, Right 16px, Radius: 16px
  - Tall Card Height: 132px, Padding: 20px all sides, Radius: 16px
  - Large Card Height: 148px, Padding: Left 20px (Internal text padding: Top/Bottom 20px), Radius: 16px
  - Element Gap: 4px spacing between text stack elements, 12px spacing between text and illustration asset
- **타이포그래피 및 이미지 자산 스펙**
  - Main Title Text: Font Family `KBFG Text`, Size 16px to 18px, Weight 700 (Bold), Line-height 22px to 25px
  - Subtitle / Description Text: Font Family `KBFG Text`, Size 14px, Weight 300 (Light), Line-height 20px
  - Illustration Asset: 80x80px graphic within a 96x96px bounding frame (Standard/Tall) or direct 96x96px asset (Large)

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Card Variant / Element | Background Token | Text / Asset Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Neutral Secondary Card** | `var(--surface-neutral-secondary-muted, #F4F6F9)` | `var(--text-neutral-primary, #111827)` | `transparent` |
| **Brand Accent Muted Card** | `var(--surface-accent-brand-muted, #FFFCEF)` | `var(--text-accent-orange, #AC5D0E)` | `transparent` |
| **Description Text Token** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` / `var(--text-neutral-tertiary, #4B5563)` | `transparent` |

## 6. 구현 가이드라인
- **Flexible Flex Layout & Illustration Sizing**
  - Promo cards utilize horizontal flex layouts (`justify-content: flex-start`, `align-items: center` or `flex-start`) to balance text blocks against trailing 80px-96px promotional illustrations without breaking layout flows.
- **Surface Token Stratification**
  - Background surface tokens alternate between muted neutral (`#F4F6F9`) and warm brand accent fills (`#FFFCEF`) to categorize product highlights or special financial promotions effectively within mobile viewports.
