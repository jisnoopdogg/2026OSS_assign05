22100310 박진수
# Assignment 05
## Deployment
[Vercel Deploy URL](https://2026-oss-assign05-orcin.vercel.app)


### 페이지 구성
| 페이지 | 설명 |
| --- | --- |
| [index.html](https://2026-oss-assign05-orcin.vercel.app/index.html) | 인덱스 페이지 |
| [js_dynamic.html](https://2026-oss-assign05-orcin.vercel.app/js_dynamic.html) | JavaScript DOM Practice |
| [crud.html](https://2026-oss-assign05-orcin.vercel.app/crud.html) | Simple CRUD Service (당근 물품 관리) |
| [labs.html](https://2026-oss-assign05-orcin.vercel.app/labs.html) | 월요일 실습 |
| [labs_thurs.html](https://2026-oss-assign05-orcin.vercel.app/labs_thurs.html) | 목요일 실습 |

## Weekly Review - Week 5

### Key Learning
1. `querySelector`, `createElement`, `appendChild`, `window.onload`등 DOM과 JavaScript를 활용하여 HTML 요소를 관리하는 방법을 익혔습니다.
2. 서버와 DB 없이 JavaScript Array를 데이터 저장소로 사용하고, `render()` 함수를 만들어 Array의 내용을 화면에 다시 그리는 방식을 익혔습니다.
3. HTML validation, alert, reportValidity() 등 다양한 validation을 배웠습니다.

### CRUD Service
**주제**: 당근 물품 관리 (중고 거래 물품을 조회, 등록, 수정, 삭제하기 위한 관리 서비스)

**데이터 Field**
| Field | 의미 | 입력 형태 |
| --- | --- | --- |
| `id` | 고유 번호 | 자동 생성 (`nextId`) |
| `title` | 품목 | `input type="text"` |
| `category` | 카테고리 | `input type="text"` + `datalist` |
| `price` | 가격 | `input type="number"` |
| `condition` | 상태 (새상품 / 사용감 적음 / 사용감 많음) | `select` |
| `status` | 판매 상태 (판매중 / 예약중 / 거래 완료) | `input type="radio"` + `fieldset`/`legend` |

**구현 방법**
| 기능 | 구현 방법 |
| --- | --- |
| Create | ADD 버튼 클릭 시 form에 입력된 값을 읽어 객체를 만들고 `items.push()`로 Array에 추가 |
| Read | `items.forEach()`로 객체마다 `tr`/`td`를 만들어 JavaScript Array 데이터를 Table 형식으로 출력. 페이지 최초 실행, 추가, 수정, 삭제 시 `render()`함수로 데이터를 다시 출력 |
| Update | [수정] 클릭 시 `editForm()`으로 기존 값을 Form에 채우고 `editId`에 id 저장. ADD 클릭 시 `editId`가 없으면 기존 추가 기능, 있으면 `items.find()`로 객체를 찾아 값을 변경 |
| Delete | [삭제] 클릭 시 `confirm()`으로 확인 후 `items.filter()`로 해당 id를 제외한 새 Array를 만든 후 `render()`로 삭제 구현 |

### JavaScript
| 기능 | 설명 |
| --- | --- |
| `window.onload` | 페이지 로드가 끝난 뒤 코드를 실행|
| `querySelector()` / `getElementById()` | 요소 찾기. `querySelector`는 (`#id`), `getElementById`는 id 이름만 사용 |
| `addEventListener()` | 버튼 click 이벤트 등록에 사용 |
| `createElement()` / `appendChild()` | 요소를 만들고 부모 요소 안에 추가 |
| `push()` | Array 끝에 요소 추가 (add에 사용) |
| `find()` | 조건에 맞는 첫 번째 요소 반환 (edit시 기존 id 사용)|
| `filter()` | 조건에 맞는 요소만 모은 새 Array 반환 (delete에 사용) |
| `render()` | Array 내용을 Table에 다시 그리는 함수. Array 추가, 삭제, 수정 후 다시 그리는 용도 |
| `reportValidity()` | Form의 HTML Validation을 직접 실행하고 말풍선 경고 표시 |

### AI / Search Usage
| TOOL | Purpose | Used | 새로 배운 점 |
| --- | --- | --- | --- |
| Claude CLI | `required`가 동작하지 않아 질문 | required 대신`reportValidity()`으로 validation 적용 | HTML Validation은 submit 시에만 자동 실행됨 |
| Claude CLI | 코딩 후 필요한 요소들이 모두 반영되었는지 step 별로 확인 + 질문이 생겼을 때 질문 내용 align 목적 | assignment.md 생성 해서 step별 과제 requirements 정리 | X |
| Claude CLI | `push()`,`find()`,`filter()`등 모르는 Array 기능 질문 및 예시로 이해  | `push()`,`find()`,`filter()` 기능 이해 및 적용 (add, edit, delete) | 3가지 Array 기능에 대한 개념 이해 및 활용 방법 |

### Problem & Solution

- **Problem**: HTML에 `required`를 적용하였는데도 빈 값이 그대로 추가되고, 경고 없이 넘어갔습니다.
- **Solution**: ADD 버튼이 `type="button"`이라 submit이 일어나지 않아 검사가 실행되지 않는 것이 원인이었습니다. click 함수 맨 앞에서 `reportValidity()`를 호출하여 `required`를 대체하고, 공백만 입력한 경우도 막기 위해 검사 전에 `trim()`한 값을 input에 다시 넣었습니다. 다른 HTML Validation들도 적절히 함께 활용하여 validation을 적용하였습니다.



### Reflection
- 배운 방식으로 JavaScript Array를 추가, 수정, 삭제하여 Array를 조정해도 실행 창을 껐다 다시 켜면 기존에 입력되어 있는 Array로 돌아가는 점을 확인하였습니다. 자연스럽게 내가 처음에 선언한 코드 자체를 바꾸는 방법도 궁금해졌습니다.