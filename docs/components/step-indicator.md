# Design-to-Code Specification: Progress Tracker Card Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with light gray background `#F9FAFB` and 16px padding)
  - TopProgressBarIndicator (3px height linear progress bar container spanning full width)
    - ActiveProgressFill (130px width active fill with solid border-bottom)
  - ContentRowContainer (Flex inline layout for title and step counter)
    - TitleLabelText ("타이틀", 14px KBFG Text)
    - StepCounterGroup (Inline page/step indicator badge)
      - CurrentStepText ("1", 12px bold KBFG Text)
      - SeparatorText ("/", 12px placeholder token)
      - TotalStepText ("3", 12px placeholder token)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-state` | State | `default`, `active` |
| `data-size` | Dimension | `3px` (Progress indicator thickness) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Card Padding: Left 20px, Right 20px, Top 16px, Bottom 16px
  - Top Progress Bar Height: 3px, Background Width: 390px (Full mobile container)
  - Active Progress Fill Width: 130px (Approx. 33% completion state for step 1 of 3)
  - Item Alignment: Flex row with space-between/gap 20px (`align-items: center`)
- **타이포그래피 스펙**
  - Title Text: Font Family `KBFG Text`, Size 14px, Weight 500 (Medium), Line-height 20px
  - Step Counter Numbers: Font Family `KBFG Text`, Size 12px, Weight 700 (Bold), Line-height 17px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Element | Background / Surface Token | Text / Stroke Token | Border / Track Token |
| :--- | :--- | :--- | :--- |
| **Card Container** | `var(--background-neutral-light-gray, #F9FAFB)` | N/A | `transparent` |
| **Progress Track Bar** | `var(--background-neutral-gray, #F4F6F9)` | N/A | `transparent` |
| **Active Progress Fill** | `transparent` | `var(--border-neutral-primary, #111827)` (3px solid bottom) | `var(--border-neutral-primary, #111827)` |
| **Title Text** | `transparent` | `var(--text-neutral-primary, #111827)` | `transparent` |
| **Step Counter Text** | `transparent` | `var(--text-neutral-primary, #111827)` (Current) / `var(--text-neutral-placeholder, #9CA3AF)` (Total) | `transparent` |

## 6. 구현 가이드라인
- **Top Progress Bar Rendering**
  - The linear progress bar sits anchored at the absolute top (`top: 0`, `left: 0`) of the container with a fixed height of `3px`. The active fill uses a solid bottom border stroke (`3px var(--border-neutral-primary) solid`) to represent completion progress dynamically based on step ratios.
- **Flexbox Alignment**
  - The content row utilizes `justify-content: flex-start` with an item gap of `20px` to separate the section title from the compact step indicator counter.
