# 구현

### 기본 조건

- 구현되는 모든 코드는 순수 자바스크립트로 구현합니다.
  - 외부 의존성 모듈(개발 의존성 모듈 제외) 및 라이브러리를 사용하지 않고 직접 구현합니다.
- UI는 Todo 입력부와 Todo 목록 출력부, 정보 출력부로 나뉩니다.
  - UI는 기능만 동일하다면 첨부 영상과 동일하지 않아도 됩니다.
  - UI/UX 관점에서 옳다고 생각하는 방향으로 구현합니다.
- Todo 아이템은 `완료 전`, `완료` 두 가지 상태를 갖습니다.
  - 기본 상태 : `완료 전`

### 입력부

- Todo를 입력받을 수 있는 input이 존재합니다.
- input을 통해 Todo를 입력할 수 있으며, enter키로 Todo를 등록할 수 있습니다.
- 등록된 Todo 아이템은 Todo 목록 상단에 추가됩니다.
- 등록과 동시에 input의 내용은 초기화되어야 합니다.

### 목록부

- 등록된 Todo 목록이 출력됩니다.
- Todo는 등록 순으로 정렬되어 최근 목록이 상단에 위치해야 합니다.
- Todo 아이템 구성
  - 완료 여부를 나타내는 checkbox
    - preview에는 checkbox가 없지만 의미적으로 존재하도록 구현합니다.
  - 내용을 나타내는 textNode
  - `완료 상태`와 `완료 전` 상태를 구분할 수 있도록 시각적으로 자유롭게 표현합니다.
    - 예) 취소선과 폰트 컬러 변경으로 완료 여부가 구분되어야 합니다.
  - 삭제 버튼
- checkbox를 클릭 또는 textNode를 클릭하여 완료 처리할 수 있습니다.
- Todo 아이템은 토글 방식으로 상태를 변경할 수 있습니다.
  - `완료` : checkbox의 checked 상태
  - `완료 전` : checkbox의 unchecked 상태
- 완료된 Todo 아이템은 Todo 목록의 하단으로 이동시킵니다.
- 이미 완료된 Todo 아이템을 `완료 전` 상태로 되돌린 경우, 등록된 시간 기준의 위치로 되돌아가도록 합니다.
- 삭제 버튼 클릭시 해당되는 Todo 아이템을 삭제 합니다.

### 하단 정보부

- `전체`, `완료 전`, `완료` Todo 아이템을 필터 할 수 있는 기능을 제공합니다.
- 필터 조건에 맞는 Todo 아이템의 개수를 출력합니다.
- 완료 된 Todo 항목을 제거하는 삭제 기능을 제공합니다.

### Drag & Drop 기능

- 라이브러리를 사용하지 않고 마우스 이벤트를 사용하여 드래그 앤 드롭 기능을 구현합니다.
  - dragstart dragend 이벤트는 사용하지 않습니다.
  - `mousedown, mouseup, mousemove 이벤트로 구현합니다.`
- `완료 전` 상태를 갖는 Todo 아이템들만 드래그 앤 드롭으로 위치를 변경할 수 있습니다.
  - 전체, 완료 전 필터 모두에서 드래그앤 드롭이 가능해야합니다.
- 드래그 시 어디로 이동되는지 가이드 엘리먼트가(mirror) 표시합니다.
- 리스트 외부로 드롭 하는 경우 드래그가 취소됩니다.
- 드래그 도중 ESC를 누른 경우 드래그가 취소됩니다.
- 이동시킬 시킬 위치에서 약 2초간 머무른 경우 블러 처리가 된 Todo 아이템이 해당 위치에 임시로 적용되어 preview가 나타납니다.
  - 리스트 외부로 드롭 또는 ESC를 누른 경우 preview가 제거됩니다.
