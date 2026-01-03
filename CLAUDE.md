# CLAUDE.md - 프로젝트 개발 가이드

## 프로젝트 개요

STUDIO JBBJ 신입사원 온보딩 페이지입니다. 순수 HTML/CSS/JavaScript로 구현되어 있으며, 신입사원이 입사 첫날 회사와 팀원을 소개받고 필수 정보를 습득하는 인터랙티브 웹 경험을 제공합니다.

## 프로젝트 구조

```
JBBJ_onboarding/
├── index.html              # 시작 페이지 (이름/이메일 입력)
├── pages/
│   ├── 2_overview.html     # 회사 소개 및 비전
│   ├── 3_mento.html        # 멘토 소개
│   ├── 4_memberlist.html   # 팀원 소개 및 자리 배치도
│   ├── 5_process.html      # 제작 과정
│   ├── 7_communication-page.html  # 필수 정보 (근무, 휴가 등)
│   ├── 8_last-page.html    # 최종 퀴즈
│   └── member-*.html       # 개별 팀원 상세 페이지
├── images/
│   ├── CH/                 # 팀원 사진
│   └── ...                 # 기타 이미지
└── CLAUDE.md
```

## 커밋 & PR 규칙

- 모든 커밋 메시지는 **한글**로 작성
- 커밋 메시지 형식:
  - 타입: 기능추가 / 버그수정 / 리팩토링 / 문서수정
  - 예시: "기능추가: 로그인 페이지 구현"

- PR 제목도 한글로, 변경사항 요약
- PR 본문에는:
  - 작업한 항목 목록
  - 변경된 파일과 이유
  - 테스트 방법 (있다면)

## 코드 스타일

- 주석은 한글로
- 변수명은 영어 camelCase
- 함수 위에 한글 설명 주석 달기

### 예시

```javascript
// 사용자 이름을 로컬스토리지에서 가져오는 함수
function getNewbieName() {
    const newbieName = localStorage.getItem('newbieName') || '신입사원';
    return newbieName;
}
```

## 주요 기술 스택

- HTML5
- CSS3 (CSS 변수 활용, 다크/라이트 테마 지원)
- Vanilla JavaScript (ES6+)
- Font Awesome (아이콘)
- Google Fonts (Noto Sans KR)
- canvas-confetti (빵빠레 효과)

## 테마 시스템

다크 모드가 기본이며, CSS 변수를 통해 테마를 관리합니다:

```css
:root {
    --page-bg: #1A1A1A;
    --text-primary: #F0E68C;
    --accent-yellow: #FFD700;
    /* ... */
}

[data-theme="light"] {
    --page-bg: #F8F9FA;
    --text-primary: #212529;
    --accent-yellow: #EAA600;
    /* ... */
}
```

## 개인화 시스템

첫 페이지에서 입력받은 이름과 이메일은 localStorage에 저장되어 전체 온보딩 과정에서 사용됩니다:

```javascript
localStorage.setItem('newbieName', nameValue);
localStorage.setItem('newbieEmail', emailValue + '@studiojbbj.com');
```

## 빌드/배포

별도의 빌드 과정 없이 정적 파일로 제공됩니다. 웹 서버에 파일을 배포하면 바로 사용 가능합니다.
