# Component: Navigation / BottomBar (TabBar)

본 문서는 모바일 화면 최하단에 배치되는 5버튼 구조의 글로벌 내비게이션 바(Bottom Navigation Bar) 명세입니다.
선택 상태(`selected`)에 따른 투명도 변화, 상단 라운딩 및 토큰 바인딩 규칙을 준수하여 렌더링하세요.

---

## 1. 컴포넌트 개요
주요 화면 간 빠른 전환을 지원하는 최하단 탭 내비게이션 컴포넌트로, 상단 양쪽 모서리에 24px 곡률이 적용된 플로팅 형태의 컨테이너입니다.

---

## 2. 속성 (Properties & Variants)

### Container Properties
| Property | Type | Options | Default | 설명 |
|---|---|---|---|---|
| `itemsCount` | Number | `5` | `5` | 하위 탭 아이템 개수 (기본 5분할) |
| `theme` | String | `light`, `dark` | `light` | 배경 및 요소 테마 모드 |

### Tab Item Properties
| Property | Type | Options | Default | 설명 |
|---|---|---|---|---|
| `selected` | Boolean | `true`, `false` | `false` | 탭 활성화 여부 |
| `label` | String | Text | `"메뉴"` | 탭 하단 텍스트 라벨 |

---

## 3. 상세 레이아웃 스펙

### Container Spec
* **Dimensions:** Width `390px` (Fill container), Height Auto (`Hug contents`)
* **Padding:**
  * Top: `4px` (`$spacing.spacingXs`)
  * Left / Right: `20px` (`$spacing.spacing2xl`)
  * Bottom: `0px` (하단 HomeIndicator 영역과 맞닿음)
* **Corner Radius:**
  * Top-Left: `24px` (`$radius.radius3xl`)
  * Top-Right: `24px` (`$radius.radius3xl`)
  * Bottom-Left / Right: `0px`
* **Border:** Top `1px solid` (`$stroke.strokeMd`), `var(--border-neutral-tertiary-muted)`
* **Background:** `var(--background-neutral-elevated)` (`#ffffff` / `#1f2937`)
* **Layout:** Auto Layout Horizontal, Space-Between, Align Center

### Tab Item Spec (각 탭 개별 규격)
* **Dimensions:** Width `Flex: 1 1 0` (균등 5분할 분배), Height Auto
* **Layout:** Auto Layout Vertical, Align Center, Justify Start
* **Gap:** `2px` (`$spacing.spacing2xs`) (아이콘과 라벨 사이 간격)
* **Icon Box:**
  * Outer Frame: Width `32px`, Height `32px`
  * Vector Size: Width `24px`, Height `24px` (Frame 중앙 정렬)
* **Label (Typography):**
  * Font Family: `KBFG Text` (`$type.fontFamilyBase`)
  * Size: `11px` (`$type.fontSizeBody4xsFixed`)
  * Weight: `700` (Bold, `$type.fontWeightBold`)
  * Line Height: `15px` (`$type.lineHeightBody4xsFixed`)
  * Align: Text Center

---

## 4. 상태별 인터랙션 및 토큰 바인딩

| 구분 | Selected (`true`) | Unselected (`false`) |
|---|---|---|
| **아이콘 투명도 (Opacity)** | `1.0` (100%) | `0.30` (30%) |
| **아이콘 색상 (Color)** | `var(--icon-neutral-primary)` | `var(--icon-neutral-primary)` |
| **라벨 색상 (Color)** | `var(--text-neutral-primary)` | `var(--text-neutral-primary)` |

---

## 5. UI 생성 및 피그마 조립 규칙 (Figma Rules)

1. **컨테이너 너비:** 화면 프레임에 맞춰 항상 **`Fill container`**로 지정합니다.
2. **5분할 균등 정렬:** 각 탭 아이템(`div`)은 고정 너비를 주지 않고 **`Fill container` (`flex: 1`)**로 설정하여 뷰포트 너비 변화에 유연하게 대응합니다.
3. **Safe Area 결합:** 실제 모바일 화면을 구성할 때는 본 `BottomBar` 바로 아래에 `System / HomeIndicator` 컴포넌트를 이어서 배치해야 합니다.
