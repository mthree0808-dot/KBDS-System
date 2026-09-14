# Search Bar (검색 바)

상단 헤더 영역에서 키워드 검색을 수행하기 위한 검색 전용 인풋 컴포넌트입니다.  
뒤로가기 버튼과 통합된 캡슐형(Full Round) 검색 입력창으로 구성되며, 미입력(Default), 포커스/타이핑(Focused), 입력 완료(Entered) 상태를 지원합니다.

---

## 1. Structure & Layout

* **Container Size:** Width `390px` (Fluid `100%`), Min Height `56px`
* **Padding:** Left/Right `20px`, Top/Bottom `4px`
* **Layout:** `display: flex`, `align-items: center`, `gap: 8px`
* **Internal Structure:**
  * **Back Button (Leading):** 좌측 뒤로가기 탐색 버튼
  * **Input Track (Pill Bar):** `flex: 1 1 0` 확장형 검색창

---

## 2. Component Properties

| Property | Type | Options | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| `focused` | Boolean | `true`, `false` | `false` | 인풋 포커스 및 활성 상태 |
| `entered` | Boolean | `true`, `false` | `false` | 검색어 입력 완료 여부 |
| `value` | String | String | `""` | 현재 입력된 검색어 값 |
| `placeholder` | Text | String | `"입력해주세요"` | 기본 플레이스홀더 문구 |
| `showBackButton`| Boolean | `true`, `false` | `true` | 좌측 뒤로가기 버튼 노출 여부 |
| `showClearButton`| Boolean | `true`, `false` | `false` | 포커스 시 우측 입력 초기화(Clear) 버튼 노출 여부 |

---

## 3. Sub-Component Specifications

### 3.1 Back Button (좌측 뒤로가기 탐색)

* **Container:**
  * Size: `32x32px` (터치 영역 고려)
  * Radius: `5.33px`
  * Layout: `justify-content: center`, `align-items: center`
* **Icon Spec:**
  * Icon Bounding: `9.72 x 18.00px`
  * Color: `var(--icon-neutral-primary, #111827)`
* **Props:** `data-disabled="false"`, `data-pressed="false"`, `data-size="24"`, `data-variant="primary"`

---

### 3.2 Search Input Track (검색 인풋 영역)

* **Track Container:**
  * Layout: `flex: 1 1 0`, `align-items: center`, `padding: 12px`
  * Background: `var(--surface-neutral-tertiary-muted, #F9FAFB)`
  * Border Radius: `9999px` (Full Round Pill)
* **Search Icon (Prefix):**
  * Size: `20x20px` (Icon Bounding: `15.21 x 15.21px`)
  * Color: `var(--icon-neutral-primary, #111827)`
* **Text / Content Area:**
  * Layout: `flex: 1 1 0`, `align-items: center`, `overflow: hidden`
  * **Default (Placeholder):**
    * Typography: `KBFG Text`, Medium (`500`), `17px` / `24px`
    * Color: `var(--text-neutral-placeholder, #9CA3AF)`
  * **Focused (Typing):**
    * Typography: `KBFG Text`, Bold (`700`), `17px` / `24px`
    * Color: `var(--text-neutral-primary, #111827)`
    * Caret (텍스트 커서): Width `1.60px`, Height `24px`, Color `var(--icon-accent-brand-alt, #111827)`
  * **Entered (Filled):**
    * Typography: `KBFG Text`, Bold (`700`), `17px` / `24px`
    * Color: `var(--text-neutral-primary, #111827)`
* **Clear Button (Suffix):**
  * 노출 조건: `data-focused="true"` 상태일 때 노출
  * Container Size: `24x24px`, Radius `4px`
  * Icon Bounding: `18x18px`
  * Color: `var(--icon-neutral-quaternary, #9CA3AF)`
  * Props: `data-disabled="false"`, `data-pressed="false"`, `data-size="24"`, `data-variant="secondary"`

---

## 4. Design Tokens Mapping

| Token Name | Fallback | Property | Component Usage |
| :--- | :--- | :--- | :--- |
| `--surface-neutral-tertiary-muted` | `#F9FAFB` | `background` | 검색 인풋 트랙 배경 |
| `--text-neutral-primary` | `#111827` | `color` | 입력 중 / 입력 완료 검색어 텍스트 |
| `--text-neutral-placeholder` | `#9CA3AF` | `color` | 미입력 상태 플레이스홀더 텍스트 |
| `--icon-neutral-primary` | `#111827` | `background` / `fill` | 뒤로가기 화살표, 돋보기(Search) 아이콘 |
| `--icon-neutral-quaternary` | `#9CA3AF` | `background` / `fill` | 텍스트 지움(Clear) 아이콘 |
| `--icon-accent-brand-alt` | `#111827` | `background` | 포커스 시 점멸하는 텍스트 커서(Caret) |
| `--color-util-purple` | `#893DE7` | `border-color` | 가이드 영역 아웃라인 |

---

## 5. Interaction & Implementation Notes

* **Clear 액션 동작:** `focused="true"` 상태에서 텍스트가 1글자 이상 입력되면 우측 클리어 버튼을 활성화하며, 터치 시 입력값을 즉시 빈 값(`""`)으로 초기화하고 인풋 포커스를 유지합니다.
* **텍스트 오버플로우:** 긴 텍스트 입력 시 레이아웃 깨짐을 방지하기 위해 컨테이너에 `overflow: hidden` 및 텍스트 래핑 처리를 유지합니다.
* **키보드 액션 매핑:** 모바일 디바이스에서 가상 키보드 우측 하단 액션 키를 '검색(Search)'으로 트리거할 수 있도록 `<input type="search" enterkeyhint="search" />` 마크업 적용을 권장합니다.
