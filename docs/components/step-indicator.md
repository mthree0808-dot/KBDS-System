# Step Indicator

진행 중인 프로세스나 단계(Step)의 진행 상황을 상단 프로그레스 바와 함께 타이틀 및 페이지네이션/스텝 넘버(예: 1/3)로 안내하는 컴포넌트입니다.

---

## 1. Structure & Layout

* **Container:**
  * Width: `100%` (기준 화면 너비 `390px`)
  * Padding: Top/Bottom `16px`, Left/Right `20px`
  * Layout: `flex-direction: column`, `gap: 16px`
  * Background: `var(--background-neutral-light-gray, #F9FAFB)`
* **Inner Structure:**
  * **Top Area (Progress Bar Track):** 컨테이너 상단 고정 (`position: absolute`, `top: 0`, `left: 0`)
  * **Content Area:** 가로 정렬 (`display: inline-flex`, `justify-content: flex-start`, `align-items: center`, `gap: 20px`)
    * **Title Area:** 좌측 가변 확장 (`flex: 1 1 0`)
    * **Step Counter Area:** 우측 고정 배치

---

## 2. Component Properties

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `title` | Text | String | `"타이틀"` | 프로세스 단계 안내 타이틀 문구 |
| `currentStep` | Number | Number | `1` | 현재 진행 중인 단계 번호 |
| `totalStep` | Number | Number | `3` | 전체 단계 번호 |
| `showProgressBar`| Boolean | `true`, `false` | `true` | 상단 게이지 바 표시 여부 |

---

## 3. Sub-Component Specifications

### 3.1 Progress Bar (Top Track & Fill)
* **Track (배경 레일):**
  * Width: `390px` (반응형 대응 시 `100%`)
  * Height: `3px`
  * Color: `var(--background-neutral-gray, #F4F6F9)`
* **Indicator (진행 게이지):**
  * Width: 계산식 적용 (`(currentStep / totalStep) * 100%`, 기본 코드 기준 `130px` / `33.3%`)
  * Height: `3px`
  * Style: `border-bottom: 3px solid var(--border-neutral-primary, #111827)`

---

### 3.2 Content Area (Title & Counter)

#### Title
* **Typography:**
  * Font Family: `KBFG Text`
  * Font Size / Line Height: `14px` / `20px`
  * Font Weight: `500` (Medium)
  * Text Color: `var(--text-neutral-primary, #111827)`
* **Layout:** `flex: 1 1 0`, `word-wrap: break-word`

#### Step Counter (페이지네이션/인덱스)
* **Container:** Padding Top/Bottom `2px`, Border Radius `8px`, Inner Gap `2px`
* **Typography & Color:**
  * Font Family: `KBFG Text`
  * Font Size / Line Height: `12px` / `17px`
  * Font Weight: `700` (Bold)
  * Current Step (`1`): `var(--text-neutral-primary, #111827)`
  * Separator (`/`): `var(--text-neutral-placeholder, #9CA3AF)`
  * Total Step (`3`): `var(--text-neutral-placeholder, #9CA3AF)`

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Component Usage |
| :--- | :--- | :--- | :--- |
| `--background-neutral-light-gray` | `#F9FAFB` | `background` | 컴포넌트 전체 배경색 |
| `--background-neutral-gray` | `#F4F6F9` | `background` | 상단 프로그레스 트랙(Track) 배경 |
| `--border-neutral-primary` | `#111827` | `border-bottom-color` | 상단 프로그레스 활성 게이지 |
| `--text-neutral-primary` | `#111827` | `color` | 좌측 타이틀, 스텝 카운터 현재 값 |
| `--text-neutral-placeholder` | `#9CA3AF` | `color` | 스텝 카운터 구분자(`/`) 및 전체 단계 값 |

---

## 5. Interaction & Implementation Notes

* **진행률 계산식:** 게이지 바의 너비는 `(currentStep / totalStep) * 100%`로 동적 스타일 바인딩을 적용합니다.
* **접근성 (A11y):** 스크린 리더 지원을 위해 컨테이너에 `role="progressbar"`, `aria-valuenow={currentStep}`, `aria-valuemin="1"`, `aria-valuemax={totalStep}` 및 타이틀과의 레이블 연결(`aria-label` 또는 `aria-labelledby`)을 권장합니다.
