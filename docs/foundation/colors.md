# Color Foundation

본 문서는 프로젝트의 단일 컬러 진실 공급원(Single Source of Truth)입니다.
UI 생성 및 스타일링 시 임의의 Hex 코드 생성을 절대 금지하며, 반드시 아래 정의된 시맨틱 CSS 변수(`var(--...)`)를 우선 바인딩하세요.

---

## 1. Text Colors (텍스트)

### Neutral & Brand
| 피그마 토큰명 | CSS 변수명 | Light Mode | Dark Mode | 사용 가이드 |
|---|---|---|---|---|
| `$color.text-neutral-primary` | `var(--text-neutral-primary)` | `#111827` | `#f9fafb` | 메인 헤드라인, 핵심 텍스트 |
| `$color.text-neutral-secondary` | `var(--text-neutral-secondary)` | `#374151` | `#e5e7eb` | 서브 타이틀, 본문 기본 텍스트 |
| `$color.text-neutral-tertiary` | `var(--text-neutral-tertiary)` | `#4b5563` | `#d1d5db` | 보조 텍스트, 캡션 |
| `$color.text-neutral-quaternary` | `var(--text-neutral-quaternary)` | `#6b7280` | `#9ca3af` | 약조 메타 정보, 비강조 텍스트 |
| `$color.text-neutral-disabled` | `var(--text-neutral-disabled)` | `#9ca3af` | `#4b5563` | 비활성화 텍스트 |
| `$color.text-neutral-placeholder` | `var(--text-neutral-placeholder)` | `#9ca3af` | `#6b7280` | 인풋 필드 플레이스홀더 |
| `$color.text-accent-brand` | `var(--text-accent-brand)` | `#60584c` | `#ffd338` | 브랜드 포인트 텍스트 |
| `$color.text-accent-brand-alt` | `var(--text-accent-brand-alt)` | `#111827` | `#f9fafb` | 보조 브랜드 텍스트 |

### Contrast & Fixed (반전 및 고정)
| 피그마 토큰명 | CSS 변수명 | Light Mode | Dark Mode | 사용 가이드 |
|---|---|---|---|---|
| `$color.text-neutral-primary-on` | `var(--text-neutral-primary-on)` | `#ffffff` | `#111827` | 채도 높은 배경 위의 반전 텍스트 |
| `$color.text-neutral-secondary-on` | `var(--text-neutral-secondary-on)` | `#d1d5db` | `#374151` | 채도 높은 배경 위의 서브 반전 텍스트 |
| `$color.text-neutral-primary-fixed` | `var(--text-neutral-primary-fixed)` | `#111827` | `#111827` | 다크모드 무관 어두운 텍스트 고정 |
| `$color.text-neutral-primary-on-fixed` | `var(--text-neutral-primary-on-fixed)` | `#ffffff` | `#ffffff` | 다크모드 무관 밝은 텍스트 고정 |
| `$color.text-neutral-secondary-on-fixed` | `var(--text-neutral-secondary-on-fixed)` | `#d1d5db` | `#d1d5db` | 다크모드 무관 보조 밝은 텍스트 고정 |

### Finance & Status (금융 및 상태)
| 피그마 토큰명 | CSS 변수명 | Light Mode | Dark Mode | 사용 가이드 |
|---|---|---|---|---|
| `$color.text-status-deposit` | `var(--text-status-deposit)` | `#2974ff` | `#2974ff` | 입금 금액 표기 |
| `$color.text-status-withdrawal` | `var(--text-status-withdrawal)` | `#111827` | `#f9fafb` | 출금 금액 표기 |
| `$color.text-status-decrease` | `var(--text-status-decrease)` | `#2974ff` | `#2974ff` | 하락/감소 수치 |
| `$color.text-status-increase` | `var(--text-status-increase)` | `#f44f4f` | `#f44f4f` | 상승/증가 수치 |
| `$color.text-status-steady` | `var(--text-status-steady)` | `#374151` | `#f9fafb` | 보합 상태 |
| `$color.text-status-positive` | `var(--text-status-positive)` | `#1f6aff` | `#2974ff` | 성공/긍정 피드백 |
| `$color.text-status-negative` | `var(--text-status-negative)` | `#e53838` | `#f44f4f` | 오류/위험/취소 피드백 |
| `$color.text-status-warning` | `var(--text-status-warning)` | `#ac5d0e` | `#e57708` | 주의/경고 텍스트 |
| `$color.text-status-notice` | `var(--text-status-notice)` | `#f44f4f` | `#f96161` | 알림/강조 텍스트 |
| `$color.text-status-cancel-transaction` | `var(--text-status-cancel-transaction)` | `#6b7280` | `#9ca3af` | 거래 취소 항목 |

### Accent Palette
| 피그마 토큰명 | CSS 변수명 | Light Mode | Dark Mode |
|---|---|---|---|
| `$color.text-accent-red` | `var(--text-accent-red)` | `#e53838` | `#f96161` |
| `$color.text-accent-orange` | `var(--text-accent-orange)` | `#ac5d0e` | `#e57708` |
| `$color.text-accent-yellow` | `var(--text-accent-yellow)` | `#8f6505` | `#c28700` |
| `$color.text-accent-olive` | `var(--text-accent-olive)` | `#577400` | `#769c00` |
| `$color.text-accent-celery` | `var(--text-accent-celery)` | `#0d822e` | `#0ea91c` |
| `$color.text-accent-green` | `var(--text-accent-green)` | `#007a4d` | `#15a46e` |
| `$color.text-accent-seafoam` | `var(--text-accent-seafoam)` | `#007772` | `#00a19a` |
| `$color.text-accent-cyan` | `var(--text-accent-cyan)` | `#0680b2` | `#009bdb` |
| `$color.text-accent-blue` | `var(--text-accent-blue)` | `#1f6aff` | `#5290ff` |
| `$color.text-accent-indigo` | `var(--text-accent-indigo)` | `#6268ff` | `#8585ff` |
| `$color.text-accent-purple` | `var(--text-accent-purple)` | `#893de7` | `#ae72f9` |
| `$color.text-accent-fuchsia` | `var(--text-accent-fuchsia)` | `#b622b7` | `#e055e2` |
| `$color.text-accent-magenta` | `var(--text-accent-magenta)` | `#e83b8c` | `#f55ca3` |

---

## 2. Surface & Background Colors (배경 및 영역)

### Canvas & Surface
| 피그마 토큰명 | CSS 변수명 | Light Mode | Dark Mode | 사용 가이드 |
|---|---|---|---|---|
| `$color.background-neutral-white` | `var(--background-neutral-white)` | `#ffffff` | `#030712` | 기본 전체 페이지 배경 |
| `$color.background-neutral-light-gray` | `var(--background-neutral-light-gray)` | `#f9fafb` | `#111827` | 캔버스 보조 배경 |
| `$color.background-neutral-gray` | `var(--background-neutral-gray)` | `#f4f6f9` | `#111827` | 카드/섹션 구분 배경 |
| `$color.background-neutral-elevated` | `var(--background-neutral-elevated)` | `#ffffff` | `#1f2937` | 모달, 바텀시트, 팝오버 등 레이어 배경 |
| `$color.surface-neutral-primary` | `var(--surface-neutral-primary)` | `#111827` | `#f9fafb` | 고대비 반전 영역 배경 |
| `$color.surface-neutral-secondary` | `var(--surface-neutral-secondary)` | `#374151` | `#e5e7eb` | 2차 서피스 배경 |
| `$color.surface-neutral-tertiary` | `var(--surface-neutral-tertiary)` | `#4b5563` | `#d1d5db` | 3차 서피스 배경 |
| `$color.surface-neutral-quaternary` | `var(--surface-neutral-quaternary)` | `#6b7280` | `#9ca3af` | 4차 서피스 배경 |
| `$color.surface-neutral-primary-muted` | `var(--surface-neutral-primary-muted)` | `#eceef2` | `#111827` | 인풋/컨트롤 배경 |
| `$color.surface-neutral-secondary-muted`| `var(--surface-neutral-secondary-muted)`| `#f4f6f9` | `#ffffff19` | 연한 컨테이너 배경 |
| `$color.surface-neutral-tertiary-muted` | `var(--surface-neutral-tertiary-muted)` | `#f9fafb` | `#ffffff11` | 초미세 컨테이너 배경 |
| `$color.surface-neutral-quaternary-muted`| `var(--surface-neutral-quaternary-muted)`| `#ffffff`| `#030712` | 대체 배경 |
| `$color.surface-neutral-disabled` | `var(--surface-neutral-disabled)` | `#66708519`| `#66708533` | 비활성화 컴포넌트 배경 |
| `$color.surface-neutral-pressed` | `var(--surface-neutral-pressed)` | `#6670850c`| `#6670850c` | 컴포넌트 터치/클릭 피드백 오버레이 |
| `$color.background-overlay-dimmed` | `var(--background-overlay-dimmed)` | `#00000033`| `#00000033` | 딤드(Scrim/Backdrop) 배경 |

### Brand & Financial Status Surfaces
| 피그마 토큰명 | CSS 변수명 | Light Mode | Dark Mode | 사용 가이드 |
|---|---|---|---|---|
| `$color.surface-accent-brand` | `var(--surface-accent-brand)` | `#ffbc00` | `#ffbc00` | 대표 CTA 버튼/뱃지 배경 |
| `$color.surface-accent-brand-muted` | `var(--surface-accent-brand-muted)` | `#fffcef` | `#60584c` | 브랜드 컬러 연한 틴트 배경 |
| `$color.surface-accent-brand-alt` | `var(--surface-accent-brand-alt)` | `#111827` | `#f9fafb` | 서브 브랜드 액션 배경 |
| `$color.surface-accent-brand-alt-muted` | `var(--surface-accent-brand-alt-muted)`| `#f4f6f9`| `#1f2937` | 서브 브랜드 연한 배경 |
| `$color.surface-status-positive` | `var(--surface-status-positive)` | `#1f6aff` | `#2974ff` | 긍정/성공 강조 배경 |
| `$color.surface-status-positive-muted` | `var(--surface-status-positive-muted)` | `#ebf6ff` | `#5290ff33` | 긍정 연한 뱃지 배경 |
| `$color.surface-status-negative` | `var(--surface-status-negative)` | `#e53838` | `#f44f4f` | 위험/에러 강조 배경 |
| `$color.surface-status-negative-muted` | `var(--surface-status-negative-muted)` | `#fff6f5` | `#f9616133` | 오류 연한 뱃지/배너 배경 |
| `$color.surface-status-warning` | `var(--surface-status-warning)` | `#ac5d0e` | `#e57708` | 경고 강조 배경 |
| `$color.surface-status-warning-muted` | `var(--surface-status-warning-muted)` | `#fff7ee` | `#e57708` | 주의 연한 뱃지 배경 |
| `$color.surface-status-decrease` | `var(--surface-status-decrease)` | `#2974ff` | `#5290ff` | 주가/금액 하락 강조 배경 |
| `$color.surface-status-decrease-muted` | `var(--surface-status-decrease-muted)` | `#ebf6ff` | `#5290ff` | 하락 연한 뱃지 배경 |
| `$color.surface-status-increase` | `var(--surface-status-increase)` | `#f44f4f` | `#f96161` | 주가/금액 상승 강조 배경 |
| `$color.surface-status-increase-muted` | `var(--surface-status-increase-muted)` | `#fff6f5` | `#f96161` | 상승 연한 뱃지 배경 |
| `$color.surface-status-notice` | `var(--surface-status-notice)` | `#f44f4f` | `#f44f4f` | 알림 플래그 배경 |
| `$color.surface-status-notice-muted` | `var(--surface-status-notice-muted)` | `#ffdddb` | `#f44f4f` | 알림 연한 배경 |

### Accent Surfaces
| 피그마 토큰명 | CSS 변수명 | Light Solid | Dark Solid | Light Muted | Dark Muted |
|---|---|---|---|---|---|
| Red | `var(--surface-accent-red[-muted])` | `#f44f4f` | `#f44f4f` | `#fff6f5` | `#f9616133` |
| Orange | `var(--surface-accent-orange[-muted])` | `#cc6d0d` | `#cc6d0d` | `#fff7ee` | `#e5770833` |
| Yellow | `var(--surface-accent-yellow[-muted])` | `#b07c02` | `#b07c02` | `#fefceb` | `#c2870033` |
| Olive | `var(--surface-accent-olive[-muted])` | `#577400` | `#577400` | `#fbffeb` | `#769c0033` |
| Celery | `var(--surface-accent-celery[-muted])` | `#0d822e` | `#0d822e` | `#f0feec` | `#0ea91c33` |
| Green | `var(--surface-accent-green[-muted])` | `#008f5d` | `#008f5d` | `#edfcf4` | `#15a46e33` |
| Seafoam | `var(--surface-accent-seafoam[-muted])`| `#007772` | `#007772` | `#edfcfb` | `#00a19a33` |
| Cyan | `var(--surface-accent-cyan[-muted])` | `#038ec9` | `#038ec9` | `#ebfdff` | `#009bdb33` |
| Blue | `var(--surface-accent-blue[-muted])` | `#2974ff` | `#2974ff` | `#ebf6ff` | `#5290ff33` |
| Indigo | `var(--surface-accent-indigo[-muted])` | `#6268ff` | `#6268ff` | `#f5f5ff` | `#8585ff33` |
| Purple | `var(--surface-accent-purple[-muted])` | `#893de7` | `#893de7` | `#faf5ff` | `#ae72f933` |
| Fuchsia | `var(--surface-accent-fuchsia[-muted])`| `#b622b7` | `#b622b7` | `#fff5fe` | `#e055e233` |
| Magenta | `var(--surface-accent-magenta[-muted])`| `#e83b8c` | `#e83b8c` | `#fff5f8` | `#f55ca333` |
| Brown | `var(--surface-accent-brown[-muted])` | `#776c5d` | `#776c5d` | `#fbf9f6` | `#a5917733` |
| Monotone| `var(--surface-accent-monotone[-muted])`| `#5a6476`| `#5a6476` | `#f0f3f9` | `#8791a233` |

---

## 3. Border Colors (테두리 및 구분선)

| 피그마 토큰명 | CSS 변수명 | Light Mode | Dark Mode | 사용 가이드 |
|---|---|---|---|---|
| `$color.border-neutral-primary` | `var(--border-neutral-primary)` | `#111827` | `#f4f6f9` | 고강조 컴포넌트 외곽선 |
| `$color.border-neutral-secondary` | `var(--border-neutral-secondary)` | `#374151` | `#e5e7eb` | 기본 인풋 필드 외곽선 |
| `$color.border-neutral-tertiary` | `var(--border-neutral-tertiary)` | `#6b7280` | `#d1d5db` | 폼 컨트롤 기본 보더 |
| `$color.border-neutral-quaternary` | `var(--border-neutral-quaternary)` | `#9ca3af` | `#9ca3af` | 카드/박스 테두리 |
| `$color.border-neutral-primary-muted` | `var(--border-neutral-primary-muted)` | `#d1d5db` | `#4b5563` | 연한 컨테이너 테두리 |
| `$color.border-neutral-secondary-muted`| `var(--border-neutral-secondary-muted)`| `#e5e7eb`| `#374151` | 기본 리스트 디바이더(헤어라인) |
| `$color.border-neutral-tertiary-muted` | `var(--border-neutral-tertiary-muted)` | `#f4f6f9` | `#1f2937` | 연한 섹션 구분선 |
| `$color.border-neutral-quaternary-muted`| `var(--border-neutral-quaternary-muted)`| `#f9fafb`| `#111827` | 배경 일체형 분할선 |
| `$color.border-neutral-disabled` | `var(--border-neutral-disabled)` | `#d1d5db` | `#374151` | 비활성화 필드 테두리 |
| `$color.border-status-focus` | `var(--border-status-focus)` | `#ffbc00` | `#ffbc00` | 포커스 링 / 활성 인풋 테두리 |
| `$color.border-status-positive` | `var(--border-status-positive)` | `#1f6aff` | `#5290ff` | 긍정 피드백 보더 |
| `$color.border-status-negative` | `var(--border-status-negative)` | `#e53838` | `#e53838` | 유효성 검사 실패(에러) 테두리 |
| `$color.border-status-negative-muted` | `var(--border-status-negative-muted)` | `#ffbdbd` | `#f44f4f4c` | 연한 에러 알림 카드 테두리 |
| `$color.border-status-warning` | `var(--border-status-warning)` | `#ac5d0e` | `#e57708` | 주의 카드 보더 |
| `$color.border-status-decrease` | `var(--border-status-decrease)` | `#2974ff` | `#2974ff` | 하락 지표 보더 |
| `$color.border-status-increase` | `var(--border-status-increase)` | `#f44f4f` | `#f44f4f` | 상승 지표 보더 |
| `$color.border-accent-brand` | `var(--border-accent-brand)` | `#ffbc00` | `#ffd338` | 브랜드 강조 보더 |
| `$color.border-accent-brand-alt` | `var(--border-accent-brand-alt)` | `#111827` | `#f9fafb` | 서브 브랜드 액션 보더 |

---

## 4. Icon Colors (아이콘)

| 피그마 토큰명 | CSS 변수명 | Light Mode | Dark Mode | 사용 가이드 |
|---|---|---|---|---|
| `$color.icon-neutral-primary` | `var(--icon-neutral-primary)` | `#111827` | `#f9fafb` | 주요 액션 및 헤더 아이콘 |
| `$color.icon-neutral-secondary` | `var(--icon-neutral-secondary)` | `#374151` | `#e5e7eb` | 본문 보조 아이콘 |
| `$color.icon-neutral-tertiary` | `var(--icon-neutral-tertiary)` | `#6b7280` | `#d1d5db` | 폼 컨트롤 우측 서브 아이콘 |
| `$color.icon-neutral-quaternary` | `var(--icon-neutral-quaternary)` | `#9ca3af` | `#9ca3af` | 약조 메타 아이콘 |
| `$color.icon-neutral-disabled` | `var(--icon-neutral-disabled)` | `#d1d5db` | `#4b5563` | 비활성화 아이콘 |
| `$color.icon-neutral-primary-on` | `var(--icon-neutral-primary-on)` | `#ffffff` | `#111827` | 어두운 배경 위 반전 아이콘 |
| `$color.icon-neutral-primary-fixed` | `var(--icon-neutral-primary-fixed)` | `#111827` | `#111827` | 모드 무관 어두운 아이콘 고정 |
| `$color.icon-neutral-primary-on-fixed`| `var(--icon-neutral-primary-on-fixed)`| `#ffffff` | `#ffffff` | 모드 무관 밝은 아이콘 고정 |
| `$color.icon-status-deposit` | `var(--icon-status-deposit)` | `#2974ff` | `#2974ff` | 입금 내역 아이콘 |
| `$color.icon-status-withdrawal` | `var(--icon-status-withdrawal)` | `#111827` | `#f9fafb` | 출금 내역 아이콘 |
| `$color.icon-status-decrease` | `var(--icon-status-decrease)` | `#2974ff` | `#2974ff` | 하락/파란 화살표 아이콘 |
| `$color.icon-status-increase` | `var(--icon-status-increase)` | `#f44f4f` | `#f44f4f` | 상승/빨간 화살표 아이콘 |
| `$color.icon-status-steady` | `var(--icon-status-steady)` | `#374151` | `#f9fafb` | 보합 아이콘 |
| `$color.icon-status-positive` | `var(--icon-status-positive)` | `#1f6aff` | `#2974ff` | 성공 체크 아이콘 |
| `$color.icon-status-negative` | `var(--icon-status-negative)` | `#e53838` | `#f44f4f` | 오류 엑스 아이콘 |
| `$color.icon-status-warning` | `var(--icon-status-warning)` | `#ac5d0e` | `#e57708` | 느낌표/주의 아이콘 |
| `$color.icon-status-notice` | `var(--icon-status-notice)` | `#f44f4f` | `#f96161` | 공지 뱃지 아이콘 |
| `$color.icon-status-cancel-transaction`| `var(--icon-status-cancel-transaction)`| `#4b5563`| `#d1d5db`| 거래 취소 플래그 |
| `$color.icon-accent-brand` | `var(--icon-accent-brand)` | `#ffbc00` | `#ffd338` | 브랜드 포인트 심볼 |

---

## 5. Background Gradients & Alpha (그라디언트 및 투명도)

| 피그마 토큰명 | CSS 변수명 | Light Mode | Dark Mode | 용도 |
|---|---|---|---|---|
| `$color.background-gradient-blue` | `var(--background-gradient-blue)` | `#ebf6ff` | `#5290ff33` | 금융/상승 연출 배경 |
| `$color.background-gradient-green`| `var(--background-gradient-green)`| `#edfcf4` | `#15a46e33` | 안전/성공 연출 배경 |
| `$color.background-gradient-red` | `var(--background-gradient-red)` | `#fff6f5` | `#f9616133` | 위험/경고 연출 배경 |
| `$color.background-gradient-yellow`| `var(--background-gradient-yellow)`| `#fefceb`| `#c2870033`| 혜택/포인트 연출 배경 |
| `$color.background-gradient-gray` | `var(--background-gradient-gray)` | `#f4f6f9` | `#4b5362` | 일반 비주얼 백그라운드 |
| `$color.background-neutral-white-a-0` | `var(--background-neutral-white-a-0)` | `#ffffff00` | `#0c111d00` | 스크롤 페이드아웃 마스크 |
| `$color.background-neutral-gray-a-0` | `var(--background-neutral-gray-a-0)` | `#f0f4fa00` | `#10182800` | 스크롤 그라디언트 시작점 |

---

## 6. AI & Engineering Generation Rules

1. **하드코딩 금지:** `#111827`, `#ffbc00` 등의 Hex 코드 대신 반드시 표의 **CSS 변수명**(`var(--...)`)을 사용하여 렌더링하세요.
2. **입출금/금융 UI 상태 준수:**
   - 입금/하락 지표: `--text-status-deposit`, `--text-status-decrease` (`#2974ff`)
   - 출금 지표: `--text-status-withdrawal` (`#111827`)
   - 상승 지표: `--text-status-increase` (`#f44f4f`)
3. **입력 필드 상태 매핑:**
   - 기본 보더: `var(--border-neutral-secondary)` 또는 `var(--border-neutral-tertiary)`
   - 포커스 보더: `var(--border-status-focus)`
   - 에러 보더: `var(--border-status-negative)`
4. **리스트 구분선:** 리스트 아이템 사이 구분선은 기본적으로 `var(--border-neutral-secondary-muted)` (1px solid)를 적용하세요.
