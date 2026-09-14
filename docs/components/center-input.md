# Center Input (센터 인풋)

화면 중앙에 배치되어 사용자의 핵심 인터랙션을 유도하는 대형 입력 컴포넌트입니다.  
금액을 입력하고 실시간 한글 단위를 안내하는 **Amount(금액)** 타입과, 계좌 비밀번호/간편 비밀번호/주민번호 뒷자리 등을 마스킹 및 박스 형태로 입력하는 **Password(비밀번호/PIN)** 타입으로 구성됩니다.

---

## 1. Component Overview & Types

* **Amount Type (금액형):**
  * 송금, 이체, 결제 시 대형 수치 타이핑 및 포맷팅 금액 안내
  * Placeholder, Typing(커서), Filled(한글 환산 금액), Error(경고) 상태 지원
* **Password Type (비밀번호/PIN형):**
  * 4자리/6자리/7자리 등 보안 키패드 연동 입력창
  * **전체 도트형 (Full Dot):** 기본 7자리 마스킹 인디케이터
  * **복합/박스형 (Box & Dot):** 고정 마스킹 도트와 입력용 사각 박스 조합 (예: 앞 2자리 박스 + 뒤 도트)
  * **전체 박스형 (Full Box):** 4자리 전체 사각 PIN 박스 입력 형태

---

## 2. Component Properties

### 2.1 General Properties

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `type` | Variant | `amount`, `password` | `amount` | 인풋 폼 성격 및 레이아웃 유형 |
| `status` | Variant | `placeholder`, `typing`, `entered` (또는 `filled`), `error` | `placeholder` | 현재 입력 및 유효성 검증 상태 |
| `helperText` | Text | String | `""` | 하단 보조 안내 문구 또는 에러 메시지 |

### 2.2 Amount Type Properties

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `value` | String / Number | String | `""` | 현재 입력된 금액 수치 |
| `placeholder` | Text | String | `"얼마를 보낼까요?"` | 미입력 상태 플레이스홀더 문구 |
| `hasBadge` | Boolean | `true`, `false` | `false` | 보조 영역 내 상태 뱃지 노출 여부 |
| `badgeText` | Text | String | `"한도제한"` | 상태 뱃지 레이블 |

### 2.3 Password Type Properties

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `layoutStyle` | Variant | `dotOnly`, `boxAndDot`, `boxOnly` | `dotOnly` | 비밀번호 슬롯 레이아웃 구성 방식 |
| `length` | Number | `4`, `6`, `7` 등 | `7` | 전체 입력/마스킹 자릿수 |
| `enteredCount` | Number | Integer | `0` | 현재 입력 완료된 자릿수 |

---

## 3. Sub-Component Specifications

### 3.1 Type: `amount` (금액 입력)

* **Container:** Width `390px`, Padding Top/Bottom `16px`, Left/Right `20px`, Gap `12px`
* **Main Value Display:**
  * Layout: `justify-content: center`, `align-items: center`, `gap: 2px`
  * **Placeholder:** `KBFG Text`, Bold (`700`), `32px` / `45px`, Color `var(--text-neutral-secondary-on, #D1D5DB)`
  * **Typing:** 
    * 수치: `Pretendard`, SemiBold (`600`), `38px` / `53px`, Color `var(--text-neutral-primary, #111827)`
    * Caret (커서): Width `1.60px`, Height `45px`, Color `var(--icon-accent-brand-alt, #111827)`
  * **Filled:**
    * 수치: `Pretendard`, SemiBold (`600`), `38px` / `53px`, Color `var(--text-neutral-primary, #111827)`
    * 단위("원"): `KBFG Text`, Medium (`500`), `26px` / `36px`, Color `var(--text-neutral-primary, #111827)`
  * **Error:** 
    * 수치: `Pretendard`, SemiBold (`600`), `38px` / `53px`, Color `var(--text-status-negative, #E53838)`
    * 단위("원"): `KBFG Text`, Medium (`500`), `26px` / `36px`, Color `var(--text-status-negative, #E53838)`
* **Sub Information Area:**
  * **출금가능금액 + 뱃지 (Placeholder):**
    * 타이틀/금액: `KBFG Text`, `13px` / `18px`, Color `var(--text-neutral-quaternary, #6B7280)`
    * 뱃지: Height `20px`, Padding `0 6px`, Radius `4px`, Background `var(--surface-accent-red-muted, #FFF6F5)`, Text `var(--text-accent-red, #E53838)`, `11px` / `15px` Bold
  * **실시간 한글 환산 표기 (Typing / Filled):**
    * 텍스트: `KBFG Text`, Medium (`500`), `13px` / `18px`, Color `var(--text-neutral-quaternary, #6B7280)`
  * **에러 메시지 (Error):**
    * 아이콘: `12x12px` (Bounding `9x9px`), Color `var(--icon-status-negative, #E53838)`
    * 텍스트: `KBFG Text`, Medium (`500`), `13px` / `18px`, Color `var(--text-status-negative, #E53838)`

---

### 3.2 Type: `password` (비밀번호 / PIN 입력)

* **Container:** Width `390px`, Padding Top/Bottom `28px`, Left/Right `20px`, Gap `20px`
* **Slots Area:** `align-self: stretch`, `justify-content: center`, `align-items: center`, `gap: 8px`, `flex-wrap: wrap`

#### A. Dot Slots (원형 마스킹)
* **공통 규격:** Container Padding `2px`, Inner Dot `16x16px`, Radius `9999px`
* **Disabled / Empty:** 
  * Background `var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10))`
  * Border `1px solid var(--border-neutral-disabled, #D1D5DB)`
* **Entered (입력 완료):**
  * Background `var(--icon-neutral-primary, #111827)`
* **Error:**
  * Background `var(--icon-status-negative, #E53838)`

#### B. Box Slots (사각 입력 박스)
* **공통 규격:** Width `48px`, Height `56px` (Min-width/height 동일), Radius `12px`
* **Empty (대기 상태):**
  * Background `var(--surface-neutral-secondary-muted, #F4F6F9)`
  * Border `1px solid var(--border-neutral-primary-muted, #D1D5DB)`
* **Focus / Active (입력 중 포커스):**
  * Background `var(--surface-neutral-quaternary-muted, white)`
  * Border `3px solid var(--border-accent-brand-alt, #111827)`
  * Box Shadow `0px 4px 6px rgba(12, 17, 29, 0.10)`
* **Entered (숫자 입력 완료):**
  * Background `var(--surface-neutral-secondary-muted, #F4F6F9)`
  * Outline `1px solid var(--border-neutral-primary-muted, #D1D5DB)` (Offset: `-1px`)
  * Typography: `Pretendard`, SemiBold (`600`), `22px` / `31px`, Color `var(--text-neutral-primary, #111827)`
* **Error (오류 상태):**
  * Background `var(--surface-status-negative-muted, #FFF6F5)`
  * Outline `1px solid var(--border-status-negative-muted, #FFBDBD)` (Offset: `-1px`)
  * Typography: `Pretendard`, SemiBold (`600`), `22px` / `31px`, Color `var(--text-status-negative, #E53838)`

#### C. Password Helper Text Area
* **Info (안내 메시지):**
  * Typography: `KBFG Text`, Light (`300`), `13px` / `18px`, Color `var(--text-neutral-quaternary, #6B7280)`
* **Error (에러 메시지):**
  * 아이콘: `12x12px` (Bounding `9x9px`), Color `var(--icon-status-negative, #E53838)`
  * Typography: `KBFG Text`, Medium (`500`), `13px` / `18px`, Color `var(--text-status-negative, #E53838)`

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Component Usage |
| :--- | :--- | :--- | :--- |
| `--background-neutral-white` | `#FFFFFF` | `background` | 컴포넌트 전체 배경 |
| `--text-neutral-primary` | `#111827` | `color` | Amount 입력값 및 Password Box 숫자 텍스트 |
| `--text-neutral-secondary-on` | `#D1D5DB` | `color` | Amount 미입력 플레이스홀더 문구 |
| `--text-neutral-quaternary` | `#6B7280` | `color` | 출금가능금액, 한글 환산 표기, Password 안내 문구 |
| `--text-status-negative` | `#E53838` | `color` | 에러 상태 메인 금액, Box 숫자 및 에러 메시지 |
| `--text-accent-red` | `#E53838` | `color` | '한도제한' 뱃지 텍스트 |
| `--surface-accent-red-muted` | `#FFF6F5` | `background` | '한도제한' 뱃지 배경 |
| `--surface-neutral-secondary-muted`| `#F4F6F9` | `background` | Password Box Empty / Entered 기본 배경 |
| `--surface-neutral-quaternary-muted`| `#FFFFFF` | `background` | Password Box Focus 활성 배경 |
| `--surface-neutral-disabled` | `rgba(102, 112, 133, 0.10)` | `background` | Password Dot Empty/Disabled 배경 |
| `--surface-status-negative-muted` | `#FFF6F5` | `background` | Password Box Error 배경 |
| `--border-neutral-primary-muted` | `#D1D5DB` | `border` / `outline` | Password Box Empty / Entered 기본 보더 |
| `--border-neutral-disabled` | `#D1D5DB` | `border-color` | Password Dot Empty 외곽선 |
| `--border-accent-brand-alt` | `#111827` | `border-color` | Password Box Focus 보더 (3px) |
| `--border-status-negative-muted` | `#FFBDBD` | `outline-color` | Password Box Error 아웃라인 |
| `--icon-neutral-primary` | `#111827` | `background` | Password Dot Entered 채움 |
| `--icon-accent-brand-alt` | `#111827` | `background` | Amount Typing 텍스트 커서(Caret) |
| `--icon-status-negative` | `#E53838` | `background` / `fill` | Password Dot Error 채움 및 에러 경고 아이콘 |
| `--color-util-purple` | `#893DE7` | `border-color` | 가이드 영역 아웃라인 |

---

## 5. Interaction & Implementation Notes

* **Amount 타입 한글 변환 규칙:** 수치 입력 즉시 콤마 포맷팅과 함께 하단에 만/억/조 단위의 축약 텍스트(예: `240만원`)를 실시간 매핑합니다.
* **Password 타입 슬롯 포커스 이동:**
  * Box 입력 방식은 현재 입력할 차례의 박스에 `type="outline"` (두께 3px 및 그림자) 포커스 스타일을 부여합니다.
  * 한 자리 입력이 완료될 때마다 다음 슬롯으로 포커스를 자동 이동합니다.
* **보안 키패드 연동:** 입력 시 시스템 기본 키보드가 아닌 보안 가상 키패드가 호출되도록 인풋 이벤트를 제어합니다.
