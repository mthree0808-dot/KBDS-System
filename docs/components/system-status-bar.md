# Design-to-Code Specification: Mobile Status Bar Component (iOS & Android)

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - iOSStatusBarContainer (Width: 390px, Height: 44px, Padding: Top/Bottom 12px, Left 32px, Right 12px)
    - TimeLabelContainer ("9:41", SF Pro Text 15px SemiBold)
    - iOSStatusIconsContainer (Wifi, cellular, and battery graphic assets)
      - BatteryBorderFrame (Width 21.59px, height 11.23px, opacity 0.35)
      - BatteryCap (Width 1.15px, height 3.52px, opacity 0.40)
      - BatteryLevelFill (Width 18.14px, height 7.77px, radius 2.16px)
  - AndroidStatusBarContainer (Width: 390px, Height: 40px/52px, Padding: Horizontal 16px)
    - TimeLabelContainer ("9:30", Roboto Flex 14px Regular, letter-spacing 0.25px)
    - AndroidStatusIconsContainer (Wifi, signal, and battery indicator icons)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-os` | System | `iOS`, `Android` |
| `data-size` | Dimension | `390x44`, `390x40` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Standard Viewport Width: 390px
  - iOS Status Bar Height: 44px (Padding: Top 12px, Bottom 12px, Left 32px, Right 12px)
  - Android Status Bar Height: 40px (Padding: Left 16px, Right 16px)
- **타이포그래피 및 아이콘 스펙**
  - iOS Time Label: Font Family `SF Pro Text`, Size 15px, Weight 600 (SemiBold)
  - Android Time Label: Font Family `Roboto Flex`, Size 14px, Weight 400 (Regular), Line-height 20px, Letter-spacing 0.25px
  - iOS Battery Shell: Width 21.59px, Height 11.23px, Border Radius 3.71px, Stroke 0.86px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Element | Background Token | Text / Icon Token | Border / Opacity Token |
| :--- | :--- | :--- | :--- |
| **Status Bar Surface** | `transparent` | N/A | `transparent` |
| **Primary Icon & Time Elements** | `transparent` | `var(--icon-neutral-primary, #111827)` | `transparent` |
| **Battery Shell Frame** | `transparent` | `var(--icon-neutral-primary, #111827)` | Opacity 0.35, 0.86px solid |
| **Battery Terminal Cap** | `transparent` | `var(--icon-neutral-primary, #111827)` | Opacity 0.40 |

## 6. 구현 가이드라인
- **Platform-Specific Font Rendering**
  - Status bars strictly enforce platform-native typography standards (`SF Pro Text` for iOS and `Roboto Flex` for Android) to maintain design system fidelity across operating systems.
- **Flexbox Spacing & Alignment**
  - Status bar containers utilize `space-between` alignment or flex gaps (`gap: 154px` for iOS) to distribute time displays and system icon groups properly within top safe area bounds.
