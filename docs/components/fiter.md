# Component Specification: FilterBar / ControlBar

Figma Component Set 메타데이터 및 Claude Design-to-Code 파이프라인 연동을 위한 UI 명세서입니다.

---

## 1. Figma Metadata

- **Component Set Name**: `Navigation / FilterBar` (Sub: `ControlBar`)
- **Figma Layer Architecture**: Auto Layout (Horizontal)
- **Design System Domain**: Banking / Financial Services Framework
- **Default Frame Setup**: Hug Contents (Width: Fill container, Height: Hug/100%)

---

## 2. Component Hierarchy

```text
Root Container (inline-flex, Row)
├── Item 1: IconButton Container (data-variant="IconButton")
│   └── Base: Icon Action Button (data-variant="primary", data-size="24")
│       └── Frame: Icon Viewport (24x24px, overflow: hidden)
│           └── Vector Path (18.66 x 5.81px, absolute)
└── Item 2: Filter Container (data-variant="Filter", flex: 1 1 0)
    └── Base: Filter Button (data-size="small", data-hassuffix="true")
        ├── Text Container
        │   └── Label: Text Node ("버튼명")
        └── Suffix Icon Viewport (16x16px, overflow: hidden)
            └── Vector Path (4.86 x 9px, absolute, rotate: -90deg)
```

---

## 3. Properties & Variants

### 3.1 Root Container Attributes

| Target Layer | Attribute | Type | Default Value | Available Values | Description |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Container | `layout` | String | `inline-flex` | `inline-flex`, `flex` | Flexbox 수평 정렬 컨테이너 |
| Container | `justify` | String | `flex-end` | `flex-end`, `space-between` | 아이템 가로축 우측 정렬 |

### 3.2 Sub-Component Variants (`data-*`)

| Component | Attribute | Type | Value | Description |
| :--- | :--- | :--- | :--- | :--- |
| **IconButton** | `data-variant` | String | `IconButton` / `primary` | 컴포넌트 래퍼 구분 및 시각적 위계 타입 |
| | `data-size` | Number/String | `24` | 아이콘 버튼 규격 (24x24px) |
| | `data-disabled` | Boolean | `false` | 비활성화 여부 |
| | `data-pressed` | Boolean | `false` | 터치/클릭 프레스 활성화 상태 |
| **Filter** | `data-variant` | String | `Filter` / `primary` | 필터 컨트롤 래퍼 및 버튼 스타일 |
| | `data-size` | String | `small` | 버튼 크기 규격 (Small) |
| | `data-hasprefix` | Boolean | `false` | 선행 아이콘 노출 플래그 |
| | `data-hassuffix` | Boolean | `true` | 후행 화살표 아이콘 노출 플래그 |
| | `data-loading` | Boolean | `false` | 로딩 인디케이터 전환 상태 |
| | `data-pressed` | Boolean | `false` | 눌림 상호작용 피드백 상태 |
| | `data-underline` | Boolean | `false` | 텍스트 하단 밑줄 강조 여부 |
| | `data-disabled` | Boolean | `false` | 인터랙션 차단 상태 |

---

## 4. Detailed Layout Specifications

### 4.1 Root Container

- **Width**: `100%`
- **Height**: `100%` (또는 유동적 Auto Height)
- **Padding**: Left `20px`, Right `20px`, Top `0px`, Bottom `0px`
- **Gap**: `12px`
- **Border Radius**: `6px`
- **Alignment**: Horizontal Row (`flex-direction: row`), `justify-content: flex-end`, `align-items: center`

### 4.2 Sub-Component Layout & Typography

#### A. Left Action: `IconButton`
- **Wrapper**: `display: flex`, `justify-content: flex-start`, `align-items: flex-start`
- **Hit Target Size**: Min-Width `24px`, Min-Height `24px`
- **Border Radius**: `4px`
- **Alignment**: `display: flex`, `justify-content: center`, `align-items: center`
- **Icon Viewport**:
  - Width: `24px` / Height: `24px`
  - Clipping: `overflow: hidden`
  - Position: `relative`
- **Vector Path Dimensions**:
  - Width: `18.66px`
  - Height: `5.81px`
  - Inset: Top `9.09px`, Left `2.67px`
  - Position: `absolute`

#### B. Right Action: `Filter` Button
- **Wrapper**: `flex: 1 1 0` (남은 너비 가변 확장), `justify-content: flex-end`, `align-items: center`
- **Button Base**:
  - Min-Height: `20px` (내부 콘텐츠 기준 Hug)
  - Border Radius: `8px`
  - Padding: Top `0px`, Bottom `0px`, Left `0px`, Right `0px` (텍스트/아이콘 Gap으로 간격 제어)
  - Gap: `2px`
  - Alignment: `display: flex`, `justify-content: center`, `align-items: center`
- **Typography (Label)**:
  - Text Content: `"버튼명"`
  - Font Family: `'KBFG Text', -apple-system, sans-serif`
  - Font Size: `14px`
  - Font Weight: `500` (Medium)
  - Line Height: `20px` (142.85%)
  - Word Wrap: `break-word`
- **Suffix Icon Viewport (Caret/Arrow)**:
  - Width: `16px` / Height: `16px`
  - Clipping: `overflow: hidden`
  - Position: `relative`
- **Vector Path Dimensions**:
  - Width: `4.86px`
  - Height: `9.00px`
  - Inset: Top `10.53px`, Left `3.50px`
  - Position: `absolute`
  - Transform: `rotate(-90deg)`
  - Transform Origin: `top left`

---

## 5. Token Mapping Matrix

| State | CSS Token Variable | Fallback HEX | Applied Target Layer | Property |
| :--- | :--- | :--- | :--- | :--- |
| **Default** | `var(--icon-neutral-primary, #111827)` | `#111827` | IconButton > Vector Path | `background` (Fill) |
| **Default** | `var(--text-accent-brand-alt, #111827)` | `#111827` | Filter > Label Text | `color` |
| **Default** | `var(--icon-accent-brand-alt, #111827)` | `#111827` | Filter > Suffix Icon Vector | `background` (Fill) |
| **Pressed / Active** | `var(--interaction-pressed, rgba(17, 24, 39, 0.08))` | `rgba(17, 24, 39, 0.08)` | Button Base Layers | `background-color` |
| **Disabled** | `var(--interaction-disabled-opacity, 0.4)` | `0.4` | Component Containers | `opacity` / `pointer-events: none` |

---

## 6. Implementation Guidelines

### 6.1 Flexible Allocation & Layout Integrity
- 우측 필터 영역에는 `flex: 1 1 0`이 선언되어 있어 부모 컨테이너 너비 확장 시 영역 전체를 채우며, 내부 버튼은 `justify-content: flex-end`에 의해 우측 끝에 안정적으로 고정 배치됩니다.
- 모바일 뷰포트 축소 시 텍스트 노드가 2줄 이상으로 떨어지지 않도록 필요한 경우 `white-space: nowrap` 처리를 권장합니다.

### 6.2 SVG / Icon Rendering Rule
- 아이콘 회전 속성(`transform: rotate(-90deg)`) 적용 시 `transform-origin: top left` 기준점이 정확히 유지되어야 Viewport(16x16px) 경계 밖으로 클리핑되지 않습니다.
- SVG 벡터 렌더링 시 Fill 색상은 시맨틱 토큰 매핑을 보장하기 위해 `currentColor` 또는 상속 스타일을 적용합니다.

```css
/* Filter Suffix Arrow Render Rule */
.filter-suffix-icon {
  width: 16px;
  height: 16px;
  position: relative;
  overflow: hidden;
}

.filter-suffix-icon > .arrow-vector {
  width: 4.86px;
  height: 9px;
  position: absolute;
  top: 10.53px;
  left: 3.5px;
  transform: rotate(-90deg);
  transform-origin: top left;
  background-color: var(--icon-accent-brand-alt, #111827);
}
```
