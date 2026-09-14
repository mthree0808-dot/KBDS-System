# Design-to-Code Specification: System Icon Assets & Semantic Color Variants

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - IconAssetContainer (Fixed dimension bounding box scaling core vector glyphs)
    - VectorGraphicAsset (Semantic system icon path supporting sizing and color tint tokens)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-size` | Dimension | `24px` (Standard icon size), `28px` (Large icon size) |
| `data-tone` | Tone | `muted` (Secondary muted), `brand` (Accent brand), `red`, `orange`, `yellow` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Standard Icon Frame: Width 24px, Height 24px, Position: Absolute
  - Large Icon Frame: Width 28px, Height 28px, Position: Absolute
- **벡터 자산 스펙**
  - 24px Bounding Assets: Scaled vector glyphs spanning ~15px to 18.60px width/height
  - 28px Bounding Assets: Scaled vector glyphs spanning ~18px to 22.52px width/height

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Icon Tone / Variant | Fill / Background Token | Hex Color Code Reference |
| :--- | :--- | :--- |
| **Neutral Muted** | `var(--icon-neutral-secondary-muted, #E5E7EB)` | `#E5E7EB` |
| **Accent Brand** | `var(--icon-accent-brand, #FFBC00)` | `#FFBC00` |
| **Accent Red** | `var(--icon-accent-red, #E53838)` | `#E53838` |
| **Accent Orange** | `var(--icon-accent-orange, #F6810C)` | `#F6810C` |
| **Accent Yellow** | `var(--icon-accent-yellow, #F6C12C)` | `#F6C12C` |

## 6. 구현 가이드라인
- **Vector Scalability & Bounding Box Rigidity**
  - All system icons are housed within strict square bounding wrappers (`24x24px` or `28x28px`) with absolute centering to prevent layout distortion during dynamic state changes or inline badge integration.
- **Semantic Color Token Mapping**
  - Icon fills must leverage CSS variable tokens (`var(--icon-...)`) to inherit correct light/dark mode and state-specific accent color treatments seamlessly across financial UI components.
