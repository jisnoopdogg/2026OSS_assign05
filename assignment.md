1. 과제 목표
HTML/CSS와 JavaScript의 DOM, Event, Array를 활용하여 한 페이지에서 동작하는 간단한 CRUD Service UI를 구현합니다.  이번 과제에서는 서버와 Database를 사용하지 않고, JavaScript Array를 데이터 저장소처럼 사용합니다.

Practice Flow

HTML Form
↓
JavaScript Event
↓
Validation
↓
JavaScript Array
↓
Create / Read / Update / Delete
↓
DOM
↓
화면 갱신

수행 내용
STEP 1. JavaScript DOM 연습

HTML, CSS, JavaScript를 이용하여 간단한 동적 페이지를 제작합니다.

파일명: js_dynamic.html

구현 기능

input type="text"에 내용 입력
[추가] 버튼 클릭
입력한 내용을 하단 List에 추가
추가 후 Input 내용 초기화
각 항목에 [삭제] 버튼 생성
[삭제] 버튼 클릭 시 해당 항목 삭제
활용할 수 있는 JavaScript

window.onload
document.getElementById()
document.querySelector()
addEventListener()
createElement()
appendChild()
remove()
value
innerText
동작 예

[ apple             ] [추가]

apple       [삭제]
banana      [삭제]
kiwi        [삭제]
STEP 2. CRUD Service 주제 선정

JavaScript를 이용하여 구현할 간단한 데이터 관리 서비스를 하나 선정합니다.

* 주제 예) 도서관리/ 친구관리 / 상품관리 / Todo 관리 / 영화관리 / 메모관리 / 자유주제

* 관리할 데이터는 5개 이상의 Field로 구성합니다.   예) id, title, author, category, price

STEP 3. JavaScript Array 데이터 구성

Database 대신 JavaScript Array를 데이터 저장소처럼 사용합니다.

초기 데이터는 3개 이상 작성합니다.

예:

let books = [

    {

        id: 1,

        title: "HTML",

        author: "Kim",

        category: "Web",

        price: 10000

    },

    {

        id: 2,

        title: "CSS",

        author: "Lee",

        category: "Web",

        price: 12000

    },

    {

        id: 3,

        title: "JavaScript",

        author: "Park",

        category: "Web",

        price: 15000

    }

];

CRUD 구현에 필요한 Array 기능은 수업에서 배운 내용과 검색 또는 AI를 활용하여 찾아 적용해보세요.

함수 예:   push(),  forEach(),  find(), filter(), splice()

(단, 사용한 코드의 동작을 설명할 수 있어야 합니다.)

 

STEP 4. CRUD UI 제작

파일명: crud.html

하나의 페이지 안에 입력 영역과 출력 영역을 구성합니다.

입력 영역

데이터 입력 Form
5개 이상의 입력 Field
[Add] 또는 [저장] 버튼
출력 영역

데이터 List 또는 Table
[수정] 버튼
[삭제] 버튼
예:

Book Management

 

제목       [____________]

저자       [____________]

카테고리   [____________]

가격       [____________]

 

                     [Add]

 

------------------------------------------------

 

ID   제목          저자       카테고리     가격

1    HTML          Kim        Web         10000    [수정] [삭제]

2    CSS           Lee        Web         12000    [수정] [삭제]

3    JavaScript    Park       Web         15000    [수정] [삭제]

STEP 5. Create 구현

Form에 입력한 데이터를 JavaScript Array에 추가합니다.

Form 입력

   ↓

Validation

   ↓

[Add]

   ↓

Array에 데이터 추가

   ↓

화면 갱신

입력값이 올바른 경우에만 데이터를 추가
데이터 추가 후 Form 입력값 초기화
잘못된 입력은 추가하지 않음
STEP 6. Read 구현

JavaScript Array의 데이터를 Table 또는 List 형태로 화면에 출력합니다.

페이지가 처음 실행되었을 때 STEP 3의 초기 데이터가 화면에 표시되어야 합니다.

다음 상황에서 화면을 다시 갱신합니다.

페이지 최초 실행
데이터 추가 후
데이터 수정 후
데이터 삭제 후
Array의 내용을 화면에 출력하는 render() 형태의 함수를 만들어 사용하는 것을 권장합니다.

JavaScript Array

       ↓

    render()

       ↓

      DOM

       ↓

 Table / List

STEP 7. Update 구현

목록의 [수정] 버튼을 클릭하면 기존 데이터를 Form에 표시합니다.

사용자가 내용을 수정하고 저장하면 JavaScript Array와 화면이 함께 변경되어야 합니다.

[수정]

   ↓

기존 데이터 Form에 표시

   ↓

내용 수정

   ↓

Validation

   ↓

[저장]

   ↓

Array 수정

   ↓

화면 갱신

STEP 8. Delete 구현

각 데이터에 [삭제] 버튼을 추가합니다.

삭제 전 confirm()으로 사용자에게 삭제 여부를 확인합니다.

예:

confirm("삭제하시겠습니까?");

사용자가 확인한 경우에만 삭제합니다.

[삭제]

   ↓

confirm()

   ↓

Array에서 데이터 삭제

   ↓

화면 갱신

주의: 화면의 HTML 요소만 삭제하는 것이 아니라 JavaScript Array에서도 해당 데이터가 삭제되어야 합니다.

STEP 9. Validation 적용

CRUD 입력 Form에 Validation 기능을 3개 이상 적용합니다.

예:

필수 입력값 확인
문자열 길이 확인
숫자 범위 확인
Select 선택 여부 확인
이메일 형식 확인
예:

if (title.value.trim() === "") {

    alert("도서명을 입력하세요.");

    title.focus();

    return;

}

HTML Validation을 활용할 수도 있습니다.

<input type="text" required>

<input type="number" min="1">

<input type="email">

필요한 경우 다음 기능도 활용할 수 있습니다.

checkValidity()

Create와 Update 모두 Validation이 적용되어야 합니다.

STEP 10. CSS 적용

CRUD Service가 하나의 서비스 화면처럼 보이도록 CSS를 적용합니다.

다음 요소를 적절하게 스타일링합니다.

전체 Page Layout
Form
Input / Select
Button
Table 또는 List
수정 / 삭제 버튼
Hover 효과
디자인의 화려함보다 HTML 구조에 CSS를 적절하게 적용했는지를 확인합니다.

STEP 11. index.html 연결 및 배포

index.html에 이번 주에 제작한 페이지의 링크를 추가합니다.

JavaScript DOM Practice → js_dynamic.html

Simple CRUD Service → crud.html

모든 변경 내용을 Git으로 관리하고 GitHub에 Push합니다.

Vercel에 배포한 후 다음 내용을 확인합니다.

index.html 정상 접속
js_dynamic.html 정상 동작
crud.html 정상 동작
Create 정상 동작
Read 정상 동작
Update 정상 동작
Delete 정상 동작
Git Commit
이번 과제에서는 결과물뿐 아니라 개발 과정도 확인합니다.

필수 조건

Git Commit 10회 이상
기능 구현 순서에 따라 단계적으로 Commit
Commit Message에 작업 내용을 구체적으로 작성
예:

Create initial files
Add DOM practice
Implement add function
Implement delete function
Create CRUD layout
Add initial array data
Implement render function
Implement create function
Implement update function
Implement delete function
Add validation
Apply CSS
Update README
단순히 Commit 횟수를 맞추기 위한 의미 없는 Commit은 인정하지 않을 수 있습니다. Git History를 통해 실제 구현 과정이 확인될 수 있도록 작업합니다.

AI Usage
이번 과제에서는 AI 사용을 허용합니다.

단, AI가 과제 전체를 대신 작성하는 방식이 아니라 학습을 위한 도구로 사용합니다.

STEP 1. Target Page 참고

AI를 이용하여 자신이 만들고 싶은 CRUD 서비스의 예시 화면이나 Target Page를 생성하여 참고할 수 있습니다.

단, AI가 생성한 전체 코드를 그대로 제출하지 않습니다.

STEP 2. 필요한 기능 질문

과제를 직접 구현하면서 필요한 함수나 기능, 처리방법, flow 등의 내용을 AI 또는 검색을 이용하여 확인할 수 있습니다.

예:

push() 사용 방법
find() 사용 방법
DOM 요소 추가 방법
Event 처리 방법
Validation 방법
오류 원인 확인
STEP 3. 코드 이해 및 수정

AI가 제안한 코드를 사용할 경우

코드의 역할을 이해하고
자신의 과제에 맞게 수정하며
해당 코드를 설명할 수 있어야 합니다.
STEP 4. AI Usage 기록

README.md에 AI 사용 내용을 간단하게 기록합니다.

예: ### AI / Search Usage

Tool - ChatGPT

Purpose - Array에서 특정 데이터를 찾는 방법 확인

Used - find() 사용 방법을 확인하여 Update 기능에 적용

What I Learned - find()가 조건에 맞는 첫 번째 데이터를 반환한다는 것을 이해함

AI 사용 시 주의

다음과 같은 경우에는 추가 확인을 진행할 수 있습니다.

과제 전체를 AI로 한 번에 생성한 경우
짧은 시간에 많은 코드가 한꺼번에 작성된 경우
Git Commit까지 AI가 자동으로 수행한 것으로 보이는 경우
수업에서 배우지 않은 기능을 다수 사용한 경우
본인이 설명하지 못하는 코드가 포함된 경우
Git History에서 실제 구현 과정이 확인되지 않는 경우
필요한 경우 제출한 코드에 대해 구술 확인을 진행할 수 있습니다.

예:

이 코드는 어떤 역할을 하는가?
Array의 데이터는 어디에서 변경되는가?
render() 함수는 왜 필요한가?
이 Event는 언제 실행되는가?
사용한 JavaScript 기능을 설명할 수 있는가?
제출한 코드는 반드시 본인이 이해하고 설명할 수 있어야 합니다.

최종 파일
Repository에는 최소 다음 파일이 포함되어 있어야 합니다.

index.html
js_dynamic.html
crud.html
README.md
CSS와 JavaScript는 HTML 내부에 작성하거나 별도의 .css, .js 파일로 분리하여 작성할 수 있습니다.

README.md – Weekly Review
README.md에 이번 주 학습 내용과 배포 정보를 정리합니다.

Deployment

Vercel 배포 URL
URL을 클릭했을 때 실제 배포 사이트에 정상적으로 접속되어야 함
Key Learning

이번 주에 배운 핵심 내용 3가지

CRUD Service

구현한 서비스 주제
사용하는 데이터 Field
Create / Read / Update / Delete 구현 방법
JavaScript

이번 과제에서 사용한 주요 JavaScript 기능을 설명합니다.

예:

querySelector()
addEventListener()
createElement()
appendChild()
Array
render()
AI / Search Usage

사용한 AI 또는 검색 도구
어떤 문제를 해결하기 위해 사용했는지
실제 코드에 어떻게 적용했는지
새롭게 이해한 내용
Problem & Solution

구현 중 발생한 문제와 해결 방법

Reflection

이번 과제를 통해 새롭게 알게 된 점 또는 궁금한 점

Weekly Question
이번 주 수업 및 실습 내용을 바탕으로 퀴즈 2문제를 출제하여 Google Form으로 제출합니다.

Google Form:
https://forms.gle/QoxoyWP8ZiJTyJu67

문제 유형 : 객관식 / OX / 단답형 / 주관식

작성 조건

직접 출제 가능
AI 도구를 활용하여 생성 후 수정 가능
각 문제에 정답과 간단한 해설 포함
이번 주 핵심 내용을 이해했는지 확인할 수 있는 문제로 작성
※ 제출된 문제는 수업의 Weekly Quiz에 활용될 수 있습니다.

제출 내용
LMS에 다음 내용을 제출합니다.

GitHub Repository URL
Vercel 배포 URL
Google Form을 통한 Weekly Question 2문제
Self-Check
JavaScript DOM Practice

js_dynamic.html을 작성했는가?
Input에 입력한 데이터를 List에 추가할 수 있는가?
추가 후 Input 내용이 초기화되는가?
각 데이터의 삭제 버튼이 동작하는가?
CRUD Service

CRUD Service 주제를 선정했는가?
데이터 Field를 5개 이상 구성했는가?
JavaScript Array에 초기 데이터 3개 이상을 작성했는가?
crud.html을 작성했는가?
Create 기능이 정상적으로 동작하는가?
Read 기능이 정상적으로 동작하는가?
Update 기능이 정상적으로 동작하는가?
Delete 기능이 정상적으로 동작하는가?
삭제 시 confirm()을 적용했는가?
Create와 Update에 Validation을 적용했는가?
Validation 조건을 3개 이상 적용했는가?
CRUD Service에 CSS를 적용했는가?
Git / AI

Git Commit을 10회 이상 수행했는가?
기능 구현 과정에 따라 단계적으로 Commit했는가?
Commit Message에 작업 내용을 작성했는가?
AI가 만든 전체 코드를 그대로 제출하지 않았는가?
사용한 코드를 직접 설명할 수 있는가?
README.md에 AI / Search Usage를 작성했는가?
제출 및 배포

index.html에 두 페이지의 링크를 추가했는가?
Git으로 변경 내용을 관리했는가?
GitHub에 Commit & Push했는가?
Vercel에 정상적으로 배포했는가?
README.md에 Vercel 배포 URL을 작성했는가?
README.md의 Vercel URL이 실제 배포 사이트로 연결되는가?
배포 사이트에서 전체 기능이 정상적으로 동작하는가?
README.md에 Weekly Review를 작성했는가?
Weekly Question 2문제를 제출했는가?