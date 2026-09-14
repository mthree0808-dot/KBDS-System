# Design-to-Code Specification: Year/Month Selector Modal

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Full Screen Overlay Wrapper)
  - BackdropOverlay (`390x844px`, Dimmed Background Layer)
  - StatusBarContainer (iOS 9:41 System Bar)
  - BottomSheetContainer (Width: 390px, Rounded Top Corners: 24px)
    - HeaderSection (Title "날짜 선택", Close Button)
    - ScrollablePickerWheel (Year/Month Picker Columns with Gradient Fades)
      - PickerRowItem (Multiple years and months, active item highlighted with surface-accent)
      - TopFadeMask
      - BottomFadeMask
    - FooterCTASection (Confirm Button)
      - ConfirmButton (Primary, Min-height: 56px, Radius: 16px)
  - HomeIndicatorContainer (iOS Bottom Indicator bar)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-mode` | Mode | `light` |
| `data-variant` | Variant | `iOS`, `primary`, `elevated` |
| `data-expanded` | State | `false` |
| `data-hasaccordian` | Boolean | `false` |
| `data-hasclosebutton` | Boolean | `true` |
| `data-hashandle` | Boolean | `false` |
| `data-hastitle` | Boolean | `true` |
| `data-count` | Number | `2` (Column count for Year & Month) |
| `data-hascta` | Boolean | `true` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Sheet Width: 390px
  - Sheet Top Position: 424px (Absolute)
  - Sheet Border Radius: 24px (Top-Left, Top-Right)
  - Header Padding: Bottom 20px, Left 20px, Right 20px
  - Picker Content Padding: Left 20px, Right 20px, Vertical 12px
- **하위 버튼 및 컨트롤 스펙**
  - Close Button Box: Size 24x24px, Internal icon size 14.61px
  - Confirm CTA Button: Min-height 56px, Padding: Top/Bottom 2px, Left/Right 12px, Radius: 16px, Font: KBFG Text, Size: 18px, Weight: 700 (Bold), Line-height: 25px
- **피커 행 치수**
  - Default Row Item: Text Size 16px, Weight 500 (Medium), Line-height: 22px
  - Active Selected Row Item: Padding Vertical 12px, Background `var(--surface-accent-brand-alt-muted)`, Radius: 12px, Font Size: 18px, Weight: 700 (Bold), Line-height: 25px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Element | Background Token | Text/Icon Token | Border / Shadow Token |
| :--- | :--- | :--- | :--- |
| **Backdrop Overlay** | `var(--background-overlay-dimmed, rgba(0, 0, 0, 0.20))` | `transparent` | `transparent` |
| **Bottom Sheet Surface** | `var(--background-neutral-elevated, white)` | `var(--text-neutral-primary, #111827)` | `transparent` |
| **Default Picker Item** | `transparent` | `var(--text-neutral-placeholder, #9CA3AF)` | `transparent` |
| **Selected Picker Item** | `var(--surface-accent-brand-alt-muted, #F4F6F9)` | `var(--text-accent-brand-alt, #111827)` | `transparent` |
| **Confirm CTA Button** | `var(--surface-accent-brand-alt, #111827)` | `var(--text-neutral-primary-on, white)` | `transparent` |

## 6. 구현 가이드라인
- **Scroll Fade Gradient Masks**
  - The year/month scroll wheel implements top and bottom linear gradient masks (`linear-gradient(180deg, ...)` transitioning from fully opaque background to transparent white `rgba(255, 255, 255, 0)`) to simulate wheel perspective clipping.
- **Layout Structure & Flexbox Rules**
  - Bottom sheet content uses a flex column layout with `overflow: hidden` to properly clip scroll items within the rounded boundary.
  - Active selected items span full available width inside padding zones (`alignSelf: 'stretch'`) with explicit border radius formatting (`borderRadius: 12`).
