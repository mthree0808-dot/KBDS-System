# Typography Foundation

본 문서는 프로젝트의 단일 타이포그래피 진실 공급원(Single Source of Truth)입니다.
UI 구현 및 텍스트 레이어 생성 시 임의의 폰트 크기나 행간 수치를 직접 입력하는 것을 금지하며, 반드시 아래 정의된 타이포그래피 토큰 및 스펙을 적용하세요.

---

## 1. Font Family & Weight

### Font Family
- **기본 본문/제목 (Base):** `KBFG Text`, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif
- **숫자 및 금융 지표 (Numeric):** `Pretendard`, sans-serif

### Font Weight
| 피그마 토큰명 | CSS 변수명 / Class | Weight 값 | 용도 |
|---|---|---|---|
| `$type.fontWeightLight` | `var(--font-weight-light)` | `300` | 특수 보조 문구 |
| `$type.fontWeightRegular` | `var(--font-weight-regular)` | `400` | 일반 본문 텍스트, 보조 설명 |
| `$type.fontWeightMedium` | `var(--font-weight-medium)` | `500` | 강조 본문, 버튼 라벨, 인풋 라벨 |
| `$type.fontWeightSemibold` | `var(--font-weight-semibold)` | `600` | 섹션 소제목, 카드 타이틀, 중요 데이터 |
| `$type.fontWeightBold` | `var(--font-weight-bold)` | `700` | 대표 헤딩, 메인 수치 표기 |

### Letter Spacing (자간)
| 토큰명 | CSS 변수명 | 자간 값 |
|---|---|---|
| `$type.letterSpacingSm` | `var(--letter-spacing-sm)` | `-0.8px` |
| `$type.letterSpacingMd` | `var(--letter-spacing-md)` | `0px` |
| `$type.letterSpacingLg` | `var(--letter-spacing-lg)` | `0.8px` |

---

## 2. Dynamic Typography Scale (모드 반응형)

기본 모드(`Default`)와 큰 글씨 모드(`Large`)에 따라 글자 크기와 행간이 유동적으로 조정되는 핵심 스케일입니다.

### Display (히어로 및 대형 수치)
| 토큰 레벨 | Default (Size / LH) | Large (Size / LH) | 주요 사용처 |
|---|---|---|---|
| `display-6xl` | `38px` / `53px` | `44px` / `62px` | 메인 계좌 총 잔액, 최상단 프로모션 |
| `display-5xl` | `32px` / `45px` | `38px` / `53px` | 주요 금융 지표, 큰 금액 강조 |
| `display-4xl` | `26px` / `36px` | `32px` / `45px` | 뷰포트 대표 타이틀 |

### Title (화면 및 섹션 제목)
| 토큰 레벨 | Default (Size / LH) | Large (Size / LH) | 주요 사용처 |
|---|---|---|---|
| `title-3xl` | `22px` / `31px` | `28px` / `39px` | 페이지 대표 헤딩, 모달 상단 타이틀 |
| `title-2xl` | `20px` / `28px` | `26px` / `36px` | 그룹/카드 대표 제목 |
| `title-xl`  | `18px` / `25px` | `24px` / `34px` | 리스트 헤더, 서브 섹션 타이틀 |

### Body (본문 및 컨트롤 라벨)
| 토큰 레벨 | Default (Size / LH) | Large (Size / LH) | 주요 사용처 |
|---|---|---|---|
| `body-lg`  | `17px` / `24px` | `23px` / `32px` | 큰 본문, 주요 강조 문장 |
| `body-md`  | `16px` / `22px` | `22px` / `31px` | 기본 본문, 인풋 기본 입력값 |
| `body-sm`  | `15px` / `21px` | `21px` / `29px` | 보조 설명, 테이블 본문 셀 |
| `body-xs`  | `14px` / `20px` | `20px` / `28px` | 폼 라벨, 헬퍼 텍스트 |
| `body-2xs` | `13px` / `18px` | `19px` / `27px` | 캡션, 메타 정보, 날짜/시간 |
| `body-3xs` | `12px` / `17px` | `18px` / `25px` | 뱃지, 태그, 인라인 부가 정보 |
| `body-4xs` | `11px` / `15px` | `17px` / `24px` | 초미세 유의사항 문구 |

---

## 3. Fixed Typography Scale (고정형)

큰 글씨 모드 설정과 관계없이 **절대 크기를 유지해야 하는 특수 영역**(예: 하단 탭바, 작은 뱃지, 협소한 테이블 인라인 셀 등)에 사용합니다.

| 토큰 레벨 | 고정 Size | 고정 Line Height | 비고 |
|---|---|---|---|
| `display-6xl-fixed` | `38px` | `53px` | 고정 대형 디스플레이 |
| `display-5xl-fixed` | `32px` | `45px` | 고정 대형 디스플레이 |
| `display-4xl-fixed` | `26px` | `36px` | 고정 대형 디스플레이 |
| `title-3xl-fixed`   | `22px` | `31px` | 고정 모달/팝업 타이틀 |
| `title-2xl-fixed`   | `20px` | `28px` | 고정 섹션 타이틀 |
| `title-xl-fixed`    | `18px` | `25px` | 고정 서브 타이틀 |
| `body-lg-fixed`     | `17px` | `24px` | 고정 상단 탭 라벨 |
| `body-md-fixed`     | `16px` | `22px` | 고정 인풋/셀렉트 박스 |
| `body-sm-fixed`     | `15px` | `21px` | 고정 버튼 라벨 |
| `body-xs-fixed`     | `14px` | `20px` | 고정 인라인 안내 |
| `body-2xs-fixed`    | `13px` | `18px` | 고정 상태 뱃지 |
| `body-3xs-fixed`    | `12px` | `17px` | 고정 하단 탭바 텍스트 |
| `body-4xs-fixed`    | `11px` | `15px` | 고정 각주 문구 |

---

## 4. UI & Layout Implementation Rules

1. **숫자/금융 데이터 폰트 적용:**  
   계좌번호, 잔액, 이자율, 수익률 등 금융 관련 숫자가 단독 또는 주력으로 들어가는 영역은 반드시 `fontFamilyNumeric`(`Pretendard`)을 우선 바인딩하세요.
2. **리사이징(Resizing) 원칙:**
   - 문단(Paragraph) 및 설명글: 수평 폭 `Fill container`, 수직 높이 `Hug contents`
   - 버튼/태그/인라인 라벨: 수평 및 수직 모두 `Hug contents`
3. **고정형(Fixed) 토큰 제한적 사용:**  
   접근성을 위해 일반적인 페이지 본문과 폼 요소에는 기본 Dynamic 토큰(`body-md`, `body-sm` 등)을 사용하고, 레이아웃 깨짐이 발생하는 고정 UI 컴포넌트(바텀 네비게이션, 인라인 뱃지 등)에만 `*-fixed` 토큰을 제한적으로 적용하세요.
