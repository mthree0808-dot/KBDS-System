# Component: Form / InputField

본 문서는 서비스 전반에서 사용되는 단일 라인 텍스트 입력 필드(InputField) 명세입니다.
피그마의 Instance Swap 구조를 지원하기 위해 상위 컨테이너 구조(Label / Input Body / Help Message)와 내부 슬롯 합성 패턴(Prefix / Core / Suffix)을 표준화하여 정의합니다.

---

## 1. 컴포넌트 구조 (Hierarchy)

InputField는 세로 방향(Auto Layout Vertical)의 3단 복합 구조로 조립됩니다.

```text
[InputField Container] (Gap: 8px)
  ├── 1. Title Area (Label + Required + Tooltip)
  ├── 2. Input Box (Min-Height: 56px, Radius: 12px)
  │     ├── [Prefix Slot]   : 은행/카드 로고, 통화 기호, 국가번호 등
  │     ├── [Core Slot]     : 텍스트 입력값 / Placeholder, 커서 인디케이터
  │     └── [Suffix Slot]   : 삭제(X), 타이머, 단위('원'), 비밀번호 마스킹, 인라인 버튼 등
  └── 3. Message Area (Error Message + Sub Label / Counter)
