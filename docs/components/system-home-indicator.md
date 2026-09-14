# Component: System / HomeIndicator

본 문서는 모바일 화면 최하단 제스처 내비게이션 영역인 홈 인디케이터(Home Indicator) 명세입니다.
iOS와 Android(AOS) 플랫폼별 높이, 바(Bar) 규격 및 정렬 규칙을 준수하여 렌더링하세요.

---

## 1. 컴포넌트 개요
모바일 최하단에서 화면 전환 및 홈 복귀 제스처를 지원하는 시스템 안전 영역(Safe Area) 컴포넌트입니다.

---

## 2. 속성 (Properties & Variants)

| Property | Type | Options | Default | 설명 |
|---|---|---|---|---|
| `platform` | String | `ios`, `aos` | `ios` | OS 플랫폼 구분 |
| `theme` | String | `light`, `dark` | `light` | 하단 배경 밝기에 따른 바(Bar) 색상 모드 |

---

## 3. 플랫폼별 상세 스펙

### iOS Variant
* **Dimensions:** Width `390px` (Fill container), Height `34px`
* **Layout:** Auto Layout Horizontal / Flexbox, Align Center, Justify Center
* **Bar Dimension:**
  * Width: `134px`
  * Height: `5px`
  * Corner Radius: `100px` (`$radius.radiusFull`)
* **Color:** `var(--text-neutral-primary)` / `$color.text-neutral-primary`
* **Margin / Position:** 컨테이너 하단에서 수직 중앙 정렬 배치 (Top 기준 약 `21px ~ 26px`)

---

### AOS (Android) Variant
* **Dimensions:** Width `390px` (Fill container), Height `24px`
* **Layout:** Auto Layout Horizontal / Flexbox, Align Center, Justify Center
* **Bar Dimension:**
  * Width: `108px`
  * Height: `4px`
  * Corner Radius: `12px` (`$radius.radiusMd`)
* **Color:** `var(--text-neutral-primary)` / `$color.text-neutral-primary`
* **Margin / Position:** 상단 여백 `10px`, 수직 중앙 정렬 배치

---

## 4. 토큰 바인딩

* **Bar Fill:**
  * Light Mode: `var(--text-neutral-primary)` (`#111827`)
  * Dark Mode: `var(--text-neutral-primary)` (`#f9fafb`)
  * Fixed (어두운 배경/투명 레이어 고정 시): `var(--text-neutral-primary-on-fixed)` (`#ffffff`)
* **Background:** 기본 Transparent (하단 바텀 네비게이션 또는 전체 화면 캔버스 배경 상속)

---

## 5. UI 생성 및 피그마 조립 규칙 (Figma Rules)

1. **리사이징 설정:**
   - Container Width: 항상 **`Fill container`**
   - Container Height: iOS는 **`34px` 고정(Fixed)**, AOS는 **`24px` 고정(Fixed)**
2. **배치 위치:** 모바일 화면 프레임의 최하단(Bottom: 0)에 고정 배치하여 Safe Area Margin 역할을 수행하도록 합니다.
3. **바(Bar) 정렬:** 인디케이터 바는 컨테이너 내부에서 항상 **수평 가운데 정렬(Align Center)**을 유지해야 합니다.
