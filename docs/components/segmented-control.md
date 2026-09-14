# Component: Selection / SegmentedControl

본 문서는 상호 배타적인 옵션 그룹 중 하나를 선택할 때 사용되는 세그먼트 컨트롤(Segmented Control / Tab Switcher) 명세입니다.
상단 타이틀 영역이 결합된 대형(Large) 규격과 단독 스위처 형태의 소형(Small) 규격을 단일 명세로 통합 지원합니다.

---

## 1. 컴포넌트 구조 (Hierarchy)

SegmentedControl은 상단 레이블(Title Area)과 옵션을 감싸는 트랙 컨테이너(Track Container)로 구성됩니다.

```text
[SegmentedControl Container] (Gap: 8px)
  ├── 1. Title Area (Optional: Large Size 전용)
  │     ├── Title Text ('타이틀입니다')
  │     ├── Required Indicator ('(필수)')
  │     └── Tooltip Icon Button (16px)
  └── 2. Track Container (Padding: 4px, Gap: 2px)
        ├── [Item: Selected]   : 활성화 세그먼트 (카드 플로팅 배경 + 그림자)
        └── [Item: Unselected] : 비활성화 세그먼트 (투명 배경)
```

---

## 2. 속성 (Properties & Variants)

| Property | Type | Options | Default | 설명 |
|---|---|---|---|---|
| `size` | String | `large`, `small` | `large` | 컴포넌트 크기 및 타이틀 포함 여부 |
| `disabled` | Boolean | `true`, `false` | `false` | 전체 컨트롤 비활성화 상태 |
| `required` | Boolean | `true`, `false` | `false` | 필수 선택 표시 여부 (`(필수)`) |
| `tooltip` | Boolean | `true`, `false` | `false` | 툴팁 도움말 아이콘 표시 여부 |
| `selected` | Boolean | `true`, `false` | `false` | 각 세그먼트 아이템의 선택 상태 |

---

## 3. 상세 레이아웃 스펙

### 1. Large Size (기본 폼 입력형)
* **전체 너비:** `Fill container` (기준폭: `350px`)
* **상단 타이틀 영역 (Title Area):**
  * Padding: Horizontal `6px` (`$spacing.spacingSm`)
  * Layout: Auto Layout Horizontal, Align Center, Gap `2px` (`$spacing.spacing2xs`)
  * 타이틀: `KBFG Text`, Size `14px` (`$type.fontSizeBodyXsFixed`), Weight `700`, Line Height `20px`, Color `var(--text-neutral-primary)`
  * 필수 표시: `(필수)`, `KBFG Text`, Size `11px`, Weight `500`, Color `var(--text-accent-red)`
  * 툴팁 아이콘: `16px x 16px`, Radius `4px`, Vector `12px x 12px`, Color `var(--icon-neutral-quaternary)`
* **트랙 컨테이너 (Track):**
  * Dimensions: Width `Fill container`, Padding All `4px` (`$spacing.spacingXs`)
  * Corner Radius: `12px` (`$radius.radiusMd`)
  * Gap: `2px` (`$spacing.spacing2xs`)
  * Background: `var(--surface-neutral-secondary-muted)` (`#f4f6f9`)
* **세그먼트 아이템 (Segment Item):**
  * Dimensions: `flex: 1 1 0` (균등 분할), Min Height `40px`
  * Padding: Vertical `8px` (`$spacing.spacingMd`), Horizontal `16px` (`$spacing.spacingXl`)
  * Corner Radius: `8px` (`$radius.radiusXs`)
  * Typography: `KBFG Text`, Size `15px` (`$type.fontSizeBodySmFixed`), Line Height `21px`

### 2. Small Size (인라인/필터형)
* **전체 너비:** `Hug contents` (단독 스위처)
* **트랙 컨테이너 (Track):**
  * Dimensions: Height `Hug contents`, Padding All `4px` (`$spacing.spacingXs`)
  * Corner Radius: `10px` (`$radius.radiusSm`)
  * Gap: `2px` (`$spacing.spacing2xs`)
  * Background: `var(--surface-neutral-secondary-muted)` (`#f4f6f9`)
* **세그먼트 아이템 (Segment Item):**
  * Dimensions: Min Width `26px`, Height `Hug contents`
  * Padding: All `4px` (`$spacing.spacingXs`), Inner Text Padding Horizontal `2px`
  * Corner Radius: `6px` (`$radius.radius2xs`)
  * Typography: `KBFG Text`, Size `12px` (`$type.fontSizeBody3xsFixed`), Line Height `17px`

---

## 4. 토큰 바인딩 종합 (Token Mapping Matrix)

| 구분 (Area) | UI 요소 (Element) | Selected (`true`) | Unselected (`false`) | Disabled (`true`) |
|---|---|---|---|---|
| **Track** | 트랙 배경 (Background) | `var(--surface-neutral-secondary-muted)` | `var(--surface-neutral-secondary-muted)` | `var(--surface-neutral-disabled)` (10%) |
| **Large Item** | 아이템 배경 (Background) | `var(--surface-neutral-quaternary-muted)` (`#ffffff`) | Transparent | 활성: `var(--surface-neutral-disabled)` / 비활성: Transparent |
| | 그림자 (Box Shadow) | `0px 2px 4px -1px rgba(12, 17, 29, 0.10)` | `0px 4px 6px rgba(12, 17, 29, 0.10)` | None |
| | 텍스트 (Typography) | Weight `700`, `var(--text-neutral-primary)` | Weight `500`, `var(--text-neutral-quaternary)` | `var(--text-neutral-disabled)` (`#9ca3af`) |
| **Small Item** | 아이템 배경 (Background) | `var(--surface-neutral-quaternary-muted)` (`#ffffff`) | Transparent | 활성: `var(--surface-neutral-disabled)` / 비활성: Transparent |
| | 그림자 (Box Shadow) | `0px 2px 4px -1px rgba(12, 17, 29, 0.10)` | `0px 4px 6px rgba(12, 17, 29, 0.10)` | None |
| | 텍스트 (Typography) | Weight `700`, `var(--text-neutral-secondary)` | Weight `500`, `var(--text-neutral-quaternary)` | `var(--text-neutral-disabled)` (`#9ca3af`) |

---

## 5. AI UI 생성 규칙 (Generation Rules)

1. **폼 화면 내 2~3개 양자택일형 옵션:**
   - 폼 입력 단계에서 단일 선택을 요구할 때는 `size: 'large'`를 적용하고 상단 타이틀 영역을 포함합니다.
   - 각 세그먼트 아이템은 트랙 폭에 맞춰 균등 분할(`flex: 1`)되도록 배치하세요.
2. **리스트 필터 및 테이블 소형 스위처:**
   - 화면 우측 상단 필터나 인라인 단위 전환(예: 월/년, 건수/금액)에는 상단 타이틀이 없는 `size: 'small'`을 적용하세요.
3. **선택 상태 스타일 전환:**
   - 활성화된 세그먼트는 화이트 배경(`var(--surface-neutral-quaternary-muted)`)과 볼드 폰트, 입체감 그림자(`box-shadow`)를 부여해 비활성 탭과 명확히 구분되도록 렌더링하세요.
