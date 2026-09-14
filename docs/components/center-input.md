# Center Input (금액 입력 필드)

송금, 이체, 결제 등 금융 서비스에서 사용자가 송금할 금액을 입력할 때 사용하는 대형 금액 입력 컴포넌트입니다.  
입력 전 플레이스홀더 상태부터 타이핑(커서 노출), 입력 완료(한글 금액 변환 표기), 유효성 검증 실패(한도 초과/에러) 상태까지 총 4가지 상태를 제공합니다.

---

## 1. Component Overview & States

* **Container Size:** Width `390px` (Fluid `100%`)
* **Padding:** Left/Right `20px`, Top/Bottom `16px`
* **Layout:** `flex-direction: column`, `align-items: center`, `gap: 12px`
* **Background:** `var(--background-neutral-white, white)`
* **4대 핵심 상태:**
  * **Placeholder (기본/입력 전):** 질문형 안내 문구와 함께 하단에 출금 가능 금액 및 한도제한 뱃지 노출
  * **Typing (입력 중):** 실시간 입력 수치 및 깜빡이는 텍스트 커서(Caret) 표시, 하단에 실시간 원 단위 금액 환산 노출
  * **Filled (입력 완료):** 3자리 콤마 포맷팅된 수치와 단위("원") 표시, 하단에 가독성을 위한 한글 단위(예: 240만원) 환산 표기
  * **Error (오류/한도 초과):** 입력 금액 및 하단 헬퍼 영역이 에러 톤(Negative Red)으로 반전되며 에러 아이콘과 안내 메시지 노출

---

## 2. Component Properties

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `status` | Variant | `placeholder`, `typing`, `filled`, `error` | `placeholder` | 입력 필드의 현재 인터랙션 상태 |
| `value` | String / Number | String | `""` | 현재 입력된 금액 수치 (콤마 포함) |
| `placeholder` | Text | String | `"얼마를 보낼까요?"` | 미입력 상태 플레이스홀더 문구 |
| `hasBadge` | Boolean | `true`, `false` | `false` | 하단 보조 정보 영역 내 뱃지(예: 한도제한) 포함 여부 |
| `badgeText` | Text | String | `"한도제한"` | 상태 뱃지 텍스트 |
| `subText` | Text | String | `""` | 하단 서브 텍스트 (출금가능금액, 한글 금액, 에러 메시지) |

---

## 3. Sub-Component Specifications

### 3.1 Main Display Area (상단 메인 영역)

* **Layout:** `justify-content: center`, `align-items: center`, `gap: 2px`
* **State별 스펙:**

| State | 요소 | Typography & Style | Color Token |
| :--- | :--- | :--- | :--- |
| **Placeholder** | 안내 문구 | `KBFG Text`, Bold (`700`), `32px` / `45px` | `var(--text-neutral-secondary-on, #D1D5DB)` |
| **Typing** | 입력 수치 | `Pretendard`, SemiBold (`600`), `38px` / `53px` | `var(--text-neutral-primary, #111827)` |
| | 텍스트 커서 (Caret) | Width `1.60px`, Height `45px` | `var(--icon-accent-brand-alt, #111827)` |
| **Filled** | 포맷팅 수치 | `Pretendard`, SemiBold (`600`), `38px` / `53px` | `var(--text-neutral-primary, #111827)` |
| | 화폐 단위 ("원") | `KBFG Text`, Medium (`500`), `26px` / `36px` | `var(--text-neutral-primary, #111827)` |
| **Error** | 포맷팅 수치 | `Pretendard`, SemiBold (`600`), `38px` / `53px` | `var(--text-status-negative, #E53838)` |
| | 화폐 단위 ("원") | `KBFG Text`, Medium (`500`), `26px` / `36px` | `var(--text-status-negative, #E53838)` |

---

### 3.2 Helper / Sub-Information Area (하단 보조 영역)

* **Layout:** `justify-content: center`, `align-items: center`, `padding: 1px 0px`
* **State별 서브 구조:**

#### A. Placeholder 상태 (출금 가능 금액 & 뱃지)
* **Gap:** `8px`
* **텍스트 레이블 (출금가능금액 + 잔액):**
  * Title ("출금가능금액"): `KBFG Text`, Light (`300`), `13px` / `18px`, `var(--text-neutral-quaternary, #6B7280)`
  * Value ("3,000,000원"): `KBFG Text`, Medium (`500`), `13px` / `18px`, `var(--text-neutral-quaternary, #6B7280)`
* **상태 뱃지 (한도제한):**
  * Size: Height `20px`, Min-width/height `20px`, Padding Left/Right `6px`
  * Radius: `4px`
  * Background: `var(--surface-accent-red-muted, #FFF6F5)`
  * Typography: `KBFG Text`, Bold (`700`), `11px` / `15px`
  * Color: `var(--text-accent-red, #E53838)`
  * Props: `data-tone="red"`, `data-variant="tint"`

#### B. Typing / Filled 상태 (실시간 금액 환산)
* **Gap:** `10px`
* **한글 금액 표기 (예: "240원", "240만원"):**
  * Typography: `KBFG Text`, Medium (`500`), `13px` / `18px`
  * Color: `var(--text-neutral-quaternary, #6B7280)`
  * Props: `data-hasbadge="false"`, `data-status="amount"`

#### C. Error 상태 (경고 안내 메시지)
* **Gap:** `8px` (Icon과 Text 사이 Inner Gap `1px`)
* **에러 아이콘:**
  * Container Size: `12x12px` (Icon Bounding `9x9px`)
  * Color: `var(--icon-status-negative, #E53838)`
* **에러 문구:**
  * Typography: `KBFG Text`, Medium (`500`), `13px` / `18px`
  * Color: `var(--text-status-negative, #E53838)`
  * Props: `data-hasbadge="true"`, `data-status="error"`

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Component Usage |
| :--- | :--- | :--- | :--- |
| `--background-neutral-white` | `#FFFFFF` | `background` | 입력 필드 컨테이너 기본 배경 |
| `--text-neutral-primary` | `#111827` | `color` | Typing / Filled 상태의 메인 금액 및 단위 텍스트 |
| `--text-neutral-secondary-on` | `#D1D5DB` | `color` | Placeholder 문구 ("얼마를 보낼까요?") |
| `--text-neutral-quaternary` | `#6B7280` | `color` | 하단 출금가능금액, 한글 환산 금액 텍스트 |
| `--text-status-negative` | `#E53838` | `color` | Error 상태의 메인 금액, 단위, 하단 에러 메시지 |
| `--text-accent-red` | `#E53838` | `color` | '한도제한' 틴트 뱃지 텍스트 |
| `--surface-accent-red-muted` | `#FFF6F5` | `background` | '한도제한' 틴트 뱃지 배경 |
| `--icon-accent-brand-alt` | `#111827` | `background` | Typing 상태의 커서(Caret) 바 |
| `--icon-status-negative` | `#E53838` | `background` / `fill` | Error 상태의 좌측 경고 아이콘 |
| `--color-util-purple` | `#893DE7` | `border-color` | 가이드 영역 아웃라인 |

---

## 5. Interaction & Usability Rules

* **폰트 패밀리 분리 (Font Role):** 
  * 메인 수치(숫자) 영역은 자간과 가독성이 최적화된 `Pretendard`를 적용합니다.
  * 한글 텍스트 및 단위("원"), 하단 안내 영역은 시스템 전용 글꼴인 `KBFG Text`를 적용합니다.
* **실시간 한글 환산 표기:** 금액 입력 시 사용자 착오 송금을 방지하기 위해 하단 서브 텍스트에 만/억/조 단위의 한글 표기(예: `2,400,000` 입력 시 `240만원`)를 실시간으로 렌더링합니다.
* **오류 시 전환 피드백:** 1회/1일 이체 한도를 초과하거나 잔액을 초과할 경우 즉시 `error` 상태로 전환하며, 에러 메시지로 구체적인 사유(예: "1회 이체 한도를 초과했습니다.")를 노출합니다.
