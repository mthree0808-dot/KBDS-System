# Component: System / StatusBar

본 문서는 모바일 화면 최상단에 배치되는 OS 표준 상태 바(Status Bar) 명세입니다.
iOS와 Android(AOS) 플랫폼별 높이 및 패딩 차이를 준수하여 렌더링하세요.

---

## 1. 컴포넌트 개요
모바일 최상단에서 현재 시각, 네트워크 신호, Wi-Fi, 배터리 상태를 표시하는 시스템 컴포넌트입니다.

---

## 2. 속성 (Properties & Variants)

| Property | Type | Options | Default | 설명 |
|---|---|---|---|---|
| `platform` | String | `ios`, `aos` | `ios` | OS 플랫폼 구분 |
| `theme` | String | `light`, `dark` | `light` | 배경 밝기에 따른 텍스트/아이콘 색상 모드 |

---

## 3. 플랫폼별 상세 스펙

### iOS Variant
* **Dimensions:** Width `390px` (Fill container), Height `44px`
* **Padding:**
  * Top / Bottom: `12px` (`$spacing.spacingLg`)
  * Left: `32px` (`$spacing.spacing5xl`)
  * Right: `12px` (`$spacing.spacingLg`)
* **Layout:** Auto Layout Horizontal, Align Center, Space-Between (or Flex-1 gap)
* **Left Item (Time):**
  * Typography: `SF Pro Text` (or Base System Font), Size `15px` (`$type.fontSizeBodySmFixed`), Weight `600` (SemiBold)
  * Color: `var(--icon-neutral-primary)` / `$color.icon-neutral-primary`
* **Right Items (Signal / Wi-Fi / Battery):**
  * Container Size: Width `74.7px`, Height `19px`
  * Item Gap: `6px` (`$spacing.spacingSm`)
  * Color: `var(--icon-neutral-primary)` / `$color.icon-neutral-primary`

---

### AOS (Android) Variant
* **Dimensions:** Width `390px` (Fill container), Height `40px` (Container: `52px` bounds)
* **Padding:**
  * Top / Bottom: `0px`
  * Left: `16px` (`$spacing.spacingXl`)
  * Right: `16px` (`$spacing.spacingXl`)
* **Layout:** Auto Layout Horizontal, Align Center, Space-Between
* **Left Item (Time):**
  * Typography: `Roboto Flex` (or Base System Font), Size `14px` (`$type.fontSizeBodyXsFixed`), Weight `400` (Regular), Line Height `20px`
  * Color: `var(--icon-neutral-primary)` / `$color.icon-neutral-primary`
* **Right Items (Icons):**
  * Container Gap: `2px` (`$spacing.spacing2xs`)
  * Individual Icon Box: `16px x 16px`
  * Color: `var(--icon-neutral-primary)` / `$color.icon-neutral-primary`

---

## 4. 토큰 바인딩

* **Foreground (Time & Icons):**
  * Light Mode: `var(--icon-neutral-primary)` (`#111827`)
  * Dark Mode: `var(--icon-neutral-primary)` (`#f9fafb`)
  * Fixed (White 배경/투명 헤더 위): `var(--icon-neutral-primary-fixed)`
* **Background:** 기본 Transparent (스크린 최상단 컨테이너 배경을 상속받음)

---

## 5. UI 생성 및 피그마 조립 규칙 (Figma Rules)

1. **리사이징 설정:**
   - Width: 모바일 뷰포트 폭에 맞춰 항상 **`Fill container`**로 지정합니다.
   - Height: iOS는 **`44px` 고정(Fixed)**, AOS는 **`40px` 고정(Fixed)**을 적용합니다.
2. **배치 위치:** 화면 전체 최상단(Top: 0)에 위치하며, 하단 스크롤 영역과 겹치지 않도록 플로우 최상위에 배치합니다.
3. **토큰 연결:** 시간 텍스트와 모든 아이콘 벡터의 Fill 색상은 반드시 `$color.icon-neutral-primary`를 바인딩하세요.
