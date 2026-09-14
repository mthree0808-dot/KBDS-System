# Design-to-Code Specification: Home Indicator Bar Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - HomeIndicatorContainerVariant1 (iOS / General Device Bottom Bar, width 390px, height 34px)
    - IndicatorBarPill (Length 134px, height 5px, rounded 100px)
  - HomeIndicatorContainerVariant2 (Alternate System Bar, width 390px, height 24px)
    - IndicatorBarPillThin (Length 108px, height 4px, rounded 12px)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-variant` | Variant | `iOS`, `system-default` |
| `data-size` | Dimension | `390x34`, `390x24` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Container Width: 390px (Standard mobile viewport width)
  - iOS Home Indicator Container Height: 34px
  - Alternate Indicator Container Height: 24px
- **인디케이터 바 수치 스펙**
  - iOS Indicator Bar: Width 134px, Height 5px, Radius: 100px (Fully rounded pill)
  - Thin Indicator Bar: Width 108px, Height 4px, Radius: 12px
- **위치 지정 규칙**
  - Absolute positioning within viewport bottom margins, ensuring safe area padding compliance.

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Element | Background Token | Text / Icon Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Home Indicator Bar** | `var(--text-neutral-primary, #111827)` | N/A | `transparent` |
| **Container Surface** | `transparent` | N/A | `transparent` |

## 6. 구현 가이드라인
- **Transform & Origin Rules**
  - Home indicator bars implement rotation transformation matrices (`transform: rotate(180deg)`) anchored at `top left` where required by legacy flex export coordinates to align accurately within device bottom safe areas.
- **Border Radius & Scaling**
  - High-radius pill shapes (`borderRadius: 100px` or `12px`) ensure smooth anti-aliased rendering across high-density mobile viewports.
