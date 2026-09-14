# Design-to-Code Specification: Icon Button Component System

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - IconButtonWrapper (Supports distinct dimension sizing, tone variations, and interactive states)
    - InnerIconAssetContainer (Bounding box for system icon graphics, scales proportionally)
      - IconGraphicElement (Neutral primary, neutral quaternary, or disabled icon vector)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-size` | Dimension | `32px`, `28px`, `24px`, `20px`, `16px` |
| `data-tone` | Tone | `primary` (Neutral primary), `secondary` (Neutral quaternary), `disabled` |
| `data-state` | State | `default`, `pressed`, `disabled` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Size 32px Variant: Bounding Box 32x32px, Radius: 6px
  - Size 28px Variant: Bounding Box 28x28px, Radius: 4px
  - Size 24px Variant: Bounding Box 24x24px, Radius: 4px
  - Size 20px Variant: Bounding Box 20x20px, Radius: 4px
  - Size 16px Variant: Bounding Box 16x16px, Radius: 4px
- **아이콘 자산 스펙**
  - 32px Icon Graphic: ~24.87px width scaling
  - 28px Icon Graphic: ~21.77px width scaling
  - 24px Icon Graphic: ~18.66px width scaling
  - 20px Icon Graphic: ~15.55px width scaling
  - 16px Icon Graphic: ~12.44px width scaling

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Icon Tone / State | Background Token | Icon Graphic Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Primary Tone (Default)** | `transparent` | `var(--icon-neutral-primary, #111827)` | `transparent` |
| **Primary Tone (Pressed)** | `var(--surface-neutral-pressed, rgba(102, 112, 133, 0.05))` | `var(--icon-neutral-primary, #111827)` | `transparent` |
| **Secondary Tone (Default)** | `transparent` | `var(--icon-neutral-quaternary, #9CA3AF)` | `transparent` |
| **Secondary Tone (Pressed)** | `var(--surface-neutral-pressed, rgba(102, 112, 133, 0.05))` | `var(--icon-neutral-quaternary, #9CA3AF)` | `transparent` |
| **Disabled State** | `transparent` | `var(--icon-neutral-disabled, #D1D5DB)` | `transparent` |

## 6. 구현 가이드라인
- **Proportional Scaling & Bounding Boxes**
  - Icon buttons maintain strict square bounding boxes (`32px`, `28px`, `24px`, `20px`, `16px`) with centered flex alignment to ensure consistent touch target framing across UI layouts.
- **Pressed State Background Feedback**
  - Pressed states apply a subtle semi-transparent background overlay (`surface-neutral-pressed: rgba(102, 112, 133, 0.05)`) with matching corner radii (`6px` or `4px`) to deliver clear tactile feedback during interaction.
