# Component Specification: CenterInput (Amount & Password Flow)

Figma Component Set 메타데이터 및 Claude Design-to-Code 파이프라인 연동을 위한 전송/송금 및 인증 핵심 입력 컴포넌트 명세서입니다.

---

## 1. Figma Metadata

- **Component Set Name**: `Form / CenterInput` (Sub: `CenterInput.Amount`, `CenterInput.Password`)
- **Figma Layer Architecture**: Auto Layout (Vertical Column)
- **Design System Domain**: Banking / Financial Services Framework (KBFG System)
- **Default Frame Setup**: Fixed Width (`390px`), Hug Height (`141px`), Center Aligned

---

## 2. Component Hierarchy

```text
CenterInput Root Container (Width: 390px, Vertical Flex, Center)
├── Primary Display Row (alignSelf: stretch, Align Center, Gap: 2px)
│   ├── [Case A: Placeholder] Text Node ("얼마를 보낼까요?", 32px/45px Bold, Center)
│   ├── [Case B: Typing Focus] 
│   │   ├── Numeric Value Node ("240", 38px/53px SemiBold, Right)
│   │   └── Active Caret Indicator (1.60 x 45px, Accent Brand Fill)
│   ├── [Case C: Value Entered] 
│   │   ├── Formatted Amount Node ("2,400,000", 38px/53px SemiBold, Right)
│   │   └── Currency Unit Node ("원", 26px/36px Medium, Right)
│   └── [Case D: Error State] 
│       ├── Max Amount Node ("9,999,999,999", 38px/53px SemiBold, Status Negative Red)
│       └── Currency Unit Node ("원", 26px/36px Medium, Status Negative Red)
└── Dynamic Sub-Information Row (alignSelf: stretch, Align Center, Gap: 8px or 10px)
    ├── [State: Initial Guide with Badge] (data-hasbadge="true", data-status="amount")
    │   ├── Balance Meta Container (Gap: 1px)
    │   │   ├── Caption Label ("출금가능금액", 13px/18px Light 300)
    │   │   └── Balance Value ("3,000,000원", 13px/18px Medium 500)
    │   └── Tint Badge (data-tone="red", data-variant="tint", 20x20px Min, Radius 4px)
    │       └── Badge Label ("한도제한", 11px/15px Bold 700)
    ├── [State: Korean Currency Preview] (data-hasbadge="false", data-status="amount")
    │   └── Converted Amount Node ("240원" / "240만원", 13px/18px Medium 500)
    └── [State: Error Feedback] (data-hasbadge="true", data-status="error")
        ├── Status Negative Icon Viewport (12x12px, Inner Vector 9x9px)
        └── Validation Error Text ("에러메시지입니다.", 13px/18px Medium 500)
