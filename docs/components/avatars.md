# Design-to-Code Specification: Avatar / Profile Image Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - AvatarWrapper (Circular frame with fully rounded geometry, supporting solid background or image fallback)
    - IconOrImageContainer (Centered inner slot for placeholder graphics or profile image assets)
      - FallbackVectorIcon (Internal vector glyph or placeholder asset)
      - ProfileImageThumbnail (Optional image placeholder with absolute positioning)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-tone` | Tone | `white`, `muted`, `brand` |
| `data-size` | Dimension | `24px`, `32px`, `40px`, `48px` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Small Variant: Width 24px, Height 24px, Radius: 9999px (Inner Icon Box: 16x16px)
  - Medium Variant: Width 32px, Height 32px, Radius: 9999px (Inner Icon Box: 20x20px or 21.33x21.33px)
  - Large Variant: Width 40px, Height 40px, Radius: 9999px (Inner Icon Box: 24x24px or 26.67x26.67px)
  - XLarge Variant: Width 48px, Height 48px, Radius: 9999px (Inner Icon Box: 32x32px)
- **위치 지정 규칙**
  - Inner containers use absolute positioning offset (`left` and `top` matching padding proportions, e.g., 4px to 12px offsets) to center profile glyphs and image thumbnails precisely.

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Avatar Style / State | Background Token | Inner Icon / Graphic Token | Outline / Border Token |
| :--- | :--- | :--- | :--- |
| **Solid Gray Avatar** | `var(--gray-300, #D1D5DB)` | `var(--surface-neutral-quaternary-muted, white)` | `transparent` |
| **Outlined Muted Avatar** | `var(--surface-neutral-primary-muted, #ECEEF2)` | `var(--surface-neutral-quaternary-muted, white)` | `1px var(--border-neutral-primary-muted, #D1D5DB) solid` |

## 6. 구현 가이드라인
- **Circular Geometry & Asset Clipping**
  - Avatars strictly enforce full rounding (`borderRadius: 9999px`) across both root containers and fallback asset slots, ensuring clean circular clipping for profile image thumbnails (`<img src="...">`).
- **Border and Outline Handling**
  - Outlined variants apply negative outline offsets (`outlineOffset: '-1px'`) with neutral border tokens (`#D1D5DB`) to maintain crisp boundaries without increasing component bounding dimensions.
