# HUR Lab 홈페이지 수정 안내

HTML을 몰라도 할 수 있는 것부터 순서대로 적었습니다.
자주 하는 작업은 대부분 **한 줄 복사해서 내용만 바꾸기**입니다.

파일은 메모장 말고 VS Code나 PyCharm 같은 편집기로 여세요.
저장할 때 인코딩은 반드시 **UTF-8**이어야 한글이 깨지지 않습니다.

---

---

## 0. GitHub Pages에 올리기 (처음 한 번)

터미널 없이 웹에서 다 됩니다.

**저장소 만들기** — github.com 가입 후 우상단 **+ → New repository**.
이름은 `hurlab-site` 정도. **Public을 선택하세요** — 무료 계정은 공개
저장소에서만 Pages가 됩니다. Create repository.

**파일 올리기** — 새 저장소 화면의 "uploading an existing file" 링크를 누르고,
압축을 푼 `hurlab-site` **폴더 안의 파일들**을 드래그해 넣습니다.
폴더째로 끌면 주소가 한 단계 깊어지니 파일만 넣으세요. 아래 Commit changes.

**Pages 켜기** — 저장소 **Settings → 왼쪽 Pages**.
Source는 "Deploy from a branch", Branch는 `main` / `/(root)` 로 두고 Save.
1~2분 뒤 `https://<아이디>.github.io/hurlab-site/` 에서 열립니다.

**도메인 연결** — Settings → Pages → Custom domain 에 `thehurlab.com` 입력 후 Save.
그다음 도메인 등록기관의 DNS에 A 레코드 4개를 추가합니다.

    185.199.108.153
    185.199.109.153
    185.199.110.153
    185.199.111.153

`www`로도 들어오게 하려면 CNAME 레코드를 `<아이디>.github.io` 로 하나 더.
DNS가 퍼진 뒤 **Enforce HTTPS** 에 체크하면 끝입니다.

주의 두 가지.
저장소가 공개된다는 건 HTML 소스가 공개된다는 뜻입니다 — 공개 사이트라
문제는 없지만 비공개로 둘 내용은 넣지 마세요.
도메인을 Wix에서 사셨다면 DNS 관리가 Wix 안에 있습니다. **새 주소에서 잘
뜨는 걸 확인한 뒤에** Wix 요금제를 정리하세요.

이후 수정은 저장소에서 파일 클릭 → 연필 아이콘 → 고치고 Commit.
1분 안에 반영됩니다.

---

## 0-2. 사이트 안의 편집기 — `edit.html`

**Claude 없이 혼자 다 하실 수 있습니다.** 사이트 주소 뒤에 `edit.html` 을
붙여서 여시면 됩니다.

    https://thehurlab2022.github.io/Hurlab/hurlab-site/edit.html

논문·사람·과제·뉴스·연구 다섯 탭이 그대로 있고, 폼에 입력하면 됩니다.
**이 페이지는 스스로 저장하지 않습니다.** 다 고치신 뒤 오른쪽 위
**Get the code → Copy → Open on GitHub** 순서로 누르시면, GitHub 편집 화면이
바로 열립니다. 전체 선택 후 붙여넣고 Commit 하시면 1분 뒤 반영됩니다.

주소를 즐겨찾기에 넣어두시면 편합니다. (검색엔진에 잡히지 않게 하려면
`edit.html` 을 `edit-x9q2.html` 처럼 아무도 모를 이름으로 바꿔두셔도 됩니다.)

### 엑셀로 고치기

같은 페이지 위쪽의 **Excel ↓ / Excel ↑** 버튼입니다.

1. 탭을 고르고 **Excel ↓** — 그 탭이 `.csv` 파일로 내려받아집니다
2. 엑셀에서 열어 편집합니다. 학생분들께 이 파일만 보내셔도 됩니다
3. 저장한 뒤 **Excel ↑** 로 그 파일을 다시 올립니다 (`.csv`, `.xlsx` 둘 다 됩니다)
4. 화면에 반영된 걸 확인하고 **Get the code** 로 평소처럼 커밋합니다

규칙은 두 가지뿐입니다. **첫 줄(제목 행)과 `id` 칸은 건드리지 않습니다.**
새로 추가하는 줄은 **`id` 를 비워두시면** 알아서 붙습니다. `kind` 칸이
그 줄이 무엇인지를 정합니다 — 예를 들어 논문 탭에서는 `paper`(게재 완료)와
`pipeline`(투고 중), 사람 탭에서는 `member` 와 `alumni` 입니다.

뉴스와 연구 탭은 **줄 순서가 곧 구조**입니다. `story` 줄 아래에 오는
`article` 줄들이 그 story에 붙고, `programme` 줄 아래의 `grant`·`work` 줄이
그 프로그램에 붙습니다. 줄 순서를 섞지 마세요.

> 엑셀 파일을 어딘가에 올려두면 사이트가 알아서 바뀌는 방식은 GitHub Pages
> 에서는 안 됩니다 — 서버가 없어서 파일을 감시할 주체가 없습니다. 위의
> Excel ↑ → Get the code 가 그것과 가장 가까운 방법이고, 클릭 두 번 차이입니다.

### `editor/` 폴더는?

Claude 아티팩트 편집기의 코드 백업본입니다. **열어도 동작하지 않습니다** —
저장이 Claude 안에서만 되기 때문입니다. 위의 `edit.html` 을 쓰시면 됩니다.

## 1. 내용 고치기 — `content/` 폴더

**HTML은 건드리지 않습니다.** 사이트의 모든 글은 `content/` 안의 다섯 파일에
들어 있고, 페이지는 그걸 읽어서 그립니다.

    content/publications.js   논문 목록, 투고 현황
    content/people.js         연구원, 동문
    content/projects.js       과제와 기간
    content/news.js           보도 자료
    content/research.js       세 프로그램의 설명·과제·대표 논문

### 방법 A — 사이트의 `edit.html` 에서 (권장)

1. `.../edit.html` 을 엽니다
2. 탭을 고르고 폼에서 고칩니다 (또는 Excel ↓ / Excel ↑)
3. 오른쪽 위 **Get the code** → `content/<이름>.js` 파일 전체가 나옵니다
4. **Copy** → **Open on GitHub →**
5. 연필 아이콘 → 전체 선택 → 붙여넣기 → **Commit changes**

1분 뒤 사이트에 반영됩니다. 반영이 안 보이면 Ctrl/Cmd + Shift + R 로 새로고침.

### 방법 B — GitHub에서 바로

`content/` 안의 파일을 열고 연필 아이콘을 눌러 고치면 됩니다. 형식은 보시면
바로 아실 만큼 단순합니다. 예를 들어 논문 한 편 추가는 `papers` 목록 맨 앞에
이렇게 한 덩어리 넣는 것입니다.

    {
     "id": "w99",
     "year": "2027",
     "authors": "S.-M. Song, H.-C. Song*, S. Hur*",
     "title": "논문 제목",
     "journal": "저널 이름",
     "detail": "45, 3, 117851"
    },

`id` 는 서로 겹치지만 않으면 아무 값이나 괜찮습니다.
저자 표기에서 `S. Hur` 은 자동으로 굵게, `S. Hur*` 처럼 별표가 있으면
제목 옆에 "Corresponding" 배지가 자동으로 붙습니다.

**JSON 문법 두 가지만 지키면 됩니다.** 값은 큰따옴표로 감싸고, 항목 사이에는
쉼표를 넣되 **마지막 항목 뒤에는 쉼표를 넣지 않습니다.** GitHub 편집 화면이
문법 오류를 빨간 줄로 표시해 줍니다.

### 과제 기간

`projects.js` 는 `"start": "2027-03"`, `"end": "2030-12"` 형식으로만 적으면
됩니다. 타임라인 막대 위치와 "Today" 선은 페이지가 알아서 계산합니다.
계산할 일이 없어졌습니다.

### 사진과 그림

멤버 사진은 `images/` 폴더를 만들어 넣고 `people.js` 의 해당 사람에게
`"photo": "images/hong.jpg"` 를 추가하면 됩니다. 연구 그림은 HTML 안에 직접
들어 있어서, 바꾸실 때는 Claude에게 이미지를 보내주세요.

---

## 2. 참고 — 옛 방식

아래쪽 `const GROUPS = [` 목록에 과정별(포닥 / 통합과정 / 석사)로 나뉘어 있습니다.

```
{ name: "홍길동", since: "2027–",
  where: "고려대학교 · 기계공학과",
  co: "Co-advised with Prof. 지도교수", mail: "id@kist.re.kr", photo: null },
```

- 공동지도가 없으면 `co: ""` 로 비웁니다.
- 그룹 위의 인원수(1, 7, 4)는 **자동으로 세어집니다.** 손댈 필요 없습니다.
- 졸업하면 이 줄을 지우고, 파일 중간의 `<ul class="alumni">` 안에 한 줄 추가하세요.

```
<li>
  <span class="a-name">홍길동</span>
  <span class="a-term">M.S. · 2025–2027</span>
  <span class="a-now">Now at <b>현재 소속</b></span>
</li>
```

### 사진 넣기

사진 파일을 `images/` 폴더를 만들어 넣고, `photo: null` 을 이렇게 바꾸면 됩니다.

```
photo: "images/hong.jpg"
```

세로로 긴 증명사진이 잘 맞습니다(3:4). 가로세로 400px 정도면 충분하고,
그보다 크면 페이지가 무거워집니다.

---

## 3. 뉴스 추가하기  → `news.html`

뉴스는 **연구별로 묶여** 있습니다. 기존 보도에 매체가 하나 늘었다면
그 연구 블록의 `<ul class="coverage">` 안에 한 줄만 넣으세요.

```
<li><a href="기사주소" target="_blank" rel="noopener"><span class="o">매체명</span><span class="h">기사 제목</span></a></li>
```

영상이면 `class="h"` 를 `class="h vid"` 로 바꾸면 video 표시가 붙습니다.

새 연구가 보도됐다면 `<section class="story" id="s2025">` 블록을 통째로 복사해서
맨 위에 붙이고, `id` 를 새로 짓고(예: `s2027`) 날짜·제목·설명·논문을 바꾸세요.
그 다음 파일 위쪽 `<style>` 안에 색을 정해줍니다.

```
#s2027 { --edge: var(--therm); }
```

`--therm`(주황)은 열, `--elec`(보라)은 에너지, `--mech`(파랑)은 트랜스듀서입니다.

---

## 4. 과제 추가하기  → `projects.html`

여기만 계산이 필요합니다. 타임라인이 **2020년 1월부터 2032년 1월까지 12년**이라,
막대의 시작 위치와 길이를 백분율로 넣어야 합니다.

```
위치(%) = (연도 + (월 - 1) ÷ 12 - 2020) ÷ 12 × 100
```

예를 들어 2027년 3월부터 2030년 12월까지인 과제라면,

- 시작 = (2027 + 2/12 − 2020) ÷ 12 × 100 = **59.72**
- 끝은 **끝나는 달의 다음 달 1일**로 계산합니다 → 2031년 1월
  = (2031 − 2020) ÷ 12 × 100 = **91.67**
- 길이 = 91.67 − 59.72 = **31.95**

이렇게 넣습니다.

```
<div class="prow">
  <div class="plabel">
    <span class="t">과제 이름</span>
    <span class="f">연구재단 · 2027.03 – 2030.12</span>
  </div>
  <div class="track"><span class="bar b-therm" style="--s:59.72%;--w:31.95%"></span></div>
</div>
```

`b-therm` / `b-elec` / `b-mech` / `b-none` 중에 연구 분야에 맞는 걸 고르세요.
끝난 과제는 `<div class="prow past">` 로 바꾸면 흐리게 표시됩니다.
맨 위 `7 active · 4 completed` 와 소제목 옆 숫자도 같이 고쳐주세요.

**해가 바뀌면 "Today" 선도 옮겨야 합니다.** 파일 위쪽 `<style>` 에서
`left: calc(324px + (100% - 324px) * 0.5556)` 의 `0.5556` 이 오늘 위치입니다.
위 공식으로 계산한 값을 100으로 나눠서 넣으세요.
(2027년 1월이면 58.33 ÷ 100 = `0.5833`)

2032년이 가까워지면 타임라인 범위 자체를 늘려야 하는데, 그때는 저에게 물어보세요.

---

## 5. 연구 그림 넣기  → `research.html`

각 연구 분야 아래에 그림 자리가 세 칸씩 있습니다.

```
<div class="frame"><span>Figure</span></div>
```

이 부분을 이렇게 바꾸면 됩니다.

```
<div class="frame"><img src="images/thermal-switch.jpg" alt="설명"></div>
```

논문의 TOC 이미지나 graphical abstract가 잘 어울립니다. 가로로 긴 비율(16:10)로
잘려서 표시되니, 세로로 긴 그림은 미리 잘라 두시는 게 좋습니다.
그림이 세 개보다 많으면 `<figure>` 묶음을 복사해서 늘리면 됩니다.

---

## 2. 고친 내용을 사이트에 반영하기

GitHub에서 Commit 하면 자동으로 올라갑니다. 1분 정도 걸립니다.
반영이 안 되면 저장소의 **Actions** 탭에서 배포가 실패했는지 확인하세요 —
대개 JSON 문법 오류입니다.

---

## 막히면

고치려는 파일을 Claude 대화창에 첨부하고 무엇을 바꾸고 싶은지 말하면
고쳐서 돌려줍니다.

**주의:** 사이트를 올린 뒤에는 **GitHub에 있는 파일이 원본**입니다.
예전에 받아둔 zip을 고쳐서 덮어쓰면 그 사이에 추가한 내용이 사라집니다.
