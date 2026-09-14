# Spacing, Radius & Stroke Foundation

본 문서는 프로젝트의 레이아웃 간격, 곡률(Radius), 선 두께(Stroke)에 대한 단일 진실 공급원(Single Source of Truth)입니다.
오토레이아웃 패딩, 마진, 갭 및 테두리 스타일링 시 임의의 픽셀 수치를 입력하지 않고 아래 토큰을 바인딩하세요.

---

## 1. Spacing System (간격 및 패딩)

오토레이아웃의 Padding(내부 여백), Gap(요소 간격), Margin(외부 여백)에 사용합니다.

| 피그마 토큰명 | CSS 변수명 | 값 (px) | 주 사용처 |
|---|---|---|---|
| `$spacing.spacing3xs` | `var(--spacing-3xs)` | `1px` | 극미세 인라인 보정 간격 |
| `$spacing.spacing2xs` | `var(--spacing-2xs)` | `2px` | 아이콘-뱃지 미세 간격, 텍스트 하단 여백 |
| `$spacing.spacingXs`  | `var(--spacing-xs)`  | `4px` | 태그/뱃지 내부 패딩, 밀집된 아이콘-텍스트 간격 |
| `$spacing.spacingSm`  | `var(--spacing-sm)`  | `6px` | 버튼 내부 요소 간격, 칩(Chip) 세로 패딩 |
| `$spacing.spacingMd`  | `var(--spacing-md)`  | `8px` | 기본 컴포넌트 내부 패딩, 작은 인라인 그룹 간격 |
| `$spacing.spacingLg`  | `var(--spacing-lg)`  | `12px`| 리스트 아이템 간격, 폼 라벨과 입력 필드 사이 |
| `$spacing.spacingXl`  | `var(--spacing-xl)`  | `16px`| **기본 그리드 거터(Gutter)**, 카드 내부 기본 패딩 |
| `$spacing.spacing2xl` | `var(--spacing-2xl)` | `20px`| 모달/시트 내부 패딩, 큰 카드 여백 |
| `$spacing.spacing3xl` | `var(--spacing-3xl)` | `24px`| 섹션 간 표준 간격, 헤더 하단 여백 |
| `$spacing.spacing4xl` | `var(--spacing-4xl)` | `28px`| 대형 섹션 분할 간격 |
| `$spacing.spacing5xl` | `var(--spacing-5xl)` | `32px`| 메인 콘텐츠 블록 간격 |
| `$spacing.spacing6xl` | `var(--spacing-6xl)` | `40px`| 페이지 주요 섹션 구분 여백 |
| `$spacing.spacing7xl` | `var(--spacing-7xl)` | `48px`| 히어로 영역 및 하단 CTA 상단 여백 |
| `$spacing.spacing8xl` | `var(--spacing-8xl)` | `80px`| 페이지 최하단 안전 여백 |

---

## 2. Corner Radius System (모서리 곡률)

컨테이너, 버튼, 카드, 팝업 등의 모서리 라운딩 처리에 사용합니다.

| 피그마 토큰명 | CSS 변수명 | 값 (px) | 주 사용처 |
|---|---|---|---|
| `$radius.radius3xs` | `var(--radius-3xs)` | `4px` | 작은 뱃지, 체크박스, 툴팁 |
| `$radius.radius2xs` | `var(--radius-2xs)` | `6px` | 인풋 필드 기본 라운딩, 스몰 버튼 |
| `$radius.radiusXs`  | `var(--radius-xs)`  | `8px` | 일반 버튼, 셀렉트 박스 |
| `$radius.radiusSm`  | `var(--radius-sm)`  | `10px`| 미디엄 컨테이너, 카드형 UI |
| `$radius.radiusMd`  | `var(--radius-md)`  | `12px`| 메인 카드 박스, 모달 알림창 |
| `$radius.radiusLg`  | `var(--radius-lg)`  | `14px`| 팝오버, 플로팅 배너 |
| `$radius.radiusXl`  | `var(--radius-xl)`  | `16px`| 바텀시트 상단 모서리, 대형 카드 |
| `$radius.radius2xl` | `var(--radius-2xl)` | `20px`| 풀스크린 모달 상단 곡률 |
| `$radius.radius3xl` | `var(--radius-3xl)` | `24px`| 특수 플로팅 컨테이너 |
| `$radius.radiusFull`| `var(--radius-full)`| `9999px`| 필(Pill) 태그, 원형 아바타, 토글 스위치 핸들 |

---

## 3. Stroke System (선 두께)

디바이더, 테두리(Border), 포커스 링, 차트 선형 그래픽에 사용합니다.

| 피그마 토큰명 | CSS 변수명 | 값 (px) | 주 사용처 |
|---|---|---|---|
| `$stroke.strokeSm`  | `var(--stroke-sm)`  | `0.5px`| 고해상도 디바이더(헤어라인), 리스트 구분선 |
| `$stroke.strokeMd`  | `var(--stroke-md)`  | `1px`  | 기본 인풋/버튼 아웃라인, 일반 보더 |
| `$stroke.strokeLg`  | `var(--stroke-lg)`  | `1.6px`| 강조 탭 바 인디케이터, 아이콘 외곽선 |
| `$stroke.strokeXl`  | `var(--stroke-xl)`  | `2px`  | 포커스 링(Focus Ring), 선택된 상태 테두리 |
| `$stroke.stroke2xl` | `var(--stroke-2xl)` | `3px`  | 접근성 고대비 테두리, 진행률 바 |
| `$stroke.stroke4xl` | `var(--stroke-4xl)` | `6px`  | 굵은 게이지 차트, 로딩 인디케이터 |

---

## 4. UI Implementation Rules

1. **기본 거터(Gutter):** 모바일 화면의 좌우 기본 패딩은 반드시 `spacingXl` (`16px`)을 적용하세요.
2. **소수점 선 두께 처리:** `strokeSm` (`0.5px`) 및 `strokeLg` (`1.6px`)는 Web 환경에서 브라우저 렌더링 엔진에 따라 `1px` 또는 `1.5px/2px`로 보정될 수 있으므로 CSS 적용 시 토큰 변수 바인딩을 유지하세요.
3. **Pill(알약) 형태 UI:** 태그나 원형 버튼의 완벽한 둥근 모서리는 개별 픽셀 값 대신 항상 `radiusFull` (`9999px`)을 지정하세요.
