# pagination Carousel

캐러셀 배너, 이미지 뷰어, 리스트 등에서 현재 위치와 전체 페이지 수를 `현재페이지 / 전체페이지` 형식으로 안내하는 컴포넌트입니다.  
배경 명도 및 적용 컨테이너에 맞춰 **Light(기본)** 및 **Dark/Inverse(반전)** 테마를 지원하며, 뷰의 위계에 따라 **Small(11px)**과 **Medium(15px)** 크기 규격을 제공합니다.

---

## 1. Component Overview & Matrix

* **Typography Scale:** 전 규격 공통 `KBFG Text`, Bold (`700`), `wordWrap: break-word`
* **Size 규격:**
  * **Small (`size="small"`):** Font Size `11px` / Line Height `15px`
  * **Medium (`size="medium"`):** Font Size `15px` / Line Height `21px`
* **Theme / Tone 규격:**
  * **Light Theme (밝은 배경용):** 모든 텍스트 요소(현재/구분자/전체)가 일관된 Primary 톤 적용
  * **Dark / On-Fixed Theme (어두운 배경/오버레이용):** 현재 페이지와 구분자/전체 페이지 간의 시각적 위계(Primary vs Secondary) 분리

---

## 2. Component Properties

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `size` | Variant | `small`, `medium` | `small` | 폰트 크기 및 라인 하이트 스케일 |
| `theme` | Variant | `light`, `dark` (또는 `on-fixed`) | `light` | 적용 배경에 따른 컬러 테마 |
| `currentPage` | Number | Integer | `1` | 현재 활성 페이지 번호 |
| `totalPage` | Number | Integer | `10` | 전체 페이지 수 |

---

## 3. Detailed Specifications by Matrix

### 3.1 Light Theme (`theme="light"`)

밝은 배경 위에서 단독으로 노출되거나 라이트 뱃지 컨테이너 내부에서 사용됩니다.

* **Size: Small (`11px` / `15px`)**
  * Current Page (`1`): `var(--text-neutral-primary-fixed, #111827)`
  * Separator (`/`): `var(--text-neutral-primary-fixed, #111827)`
  * Total Page (`10`): `var(--text-neutral-primary-fixed, #111827)`
* **Size: Medium (`15px` / `21px`)**
  * Current Page (`1`): `var(--text-neutral-primary-fixed, #111827)`
  * Separator (`/`): `var(--text-neutral-primary-fixed, #111827)`
  * Total Page (`10`): `var(--text-neutral-primary-fixed, #111827)`

---

### 3.2 Dark / Inverse Theme (`theme="dark"`)

이미지 배너 상단, 반투명 블랙 캡슐 또는 어두운 서피스 위에서 오버레이로 사용됩니다. 현재 페이지를 강조하고 구분자와 전체 페이지는 서브 톤으로 위계를 낮춥니다.

* **Size: Small (`11px` / `15px`)**
  * Current Page (`1`): `var(--text-neutral-primary-on-fixed, #FFFFFF)`
  * Separator (`/`): `var(--text-neutral-secondary-on-fixed, #D1D5DB)`
  * Total Page (`10`): `var(--text-neutral-secondary-on-fixed, #D1D5DB)`
* **Size: Medium (`15px` / `21px`)**
  * Current Page (`1`): `var(--text-neutral-primary-on-fixed, #FFFFFF)`
  * Separator (`/`): `var(--text-neutral-secondary-on-fixed, #D1D5DB)`
  * Total Page (`10`): `var(--text-neutral-secondary-on-fixed, #D1D5DB)`

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Component Usage |
| :--- | :--- | :--- | :--- |
| `--text-neutral-primary-fixed` | `#111827` | `color` | Light 테마의 전체 텍스트 (현재/구분자/전체) |
| `--text-neutral-primary-on-fixed` | `#FFFFFF` | `color` | Dark 테마의 현재 페이지 번호 강조 |
| `--text-neutral-secondary-on-fixed` | `#D1D5DB` | `color` | Dark 테마의 구분자(`/`) 및 전체 페이지 수 |

---

## 5. Usage & Implementation Notes

* **텍스트 정렬 및 레이아웃:** `display: inline-flex`, `align-items: center`, `gap: 2px` 배치를 기본으로 하며, 페이지 숫자가 변경되어도 너비 흔들림을 최소화하기 위해 숫자 영역에 고정 너비 또는 테이블 넘버(`font-variant-numeric: tabular-nums`) 스타일 지정을 권장합니다.
* **접근성 (A11y):** 화면 판독기(Screen Reader)가 `1 슬래시 10`으로 불필요한 기호를 읽지 않도록 `aria-label="총 10페이지 중 1페이지"`를 상위 컨테이너에 제공하고, 내부 텍스트는 `aria-hidden="true"` 처리를 권장합니다.
