
# ✨ Portfolio Website

    반응형 웹사이트 제작
    기술 : HTML, CSS, JAVASCRIPT, JQUERY, swiper slide, gsap
    프로그램 : 피그마, 비주얼스튜디오코드
    링크 : 


---
## 🔍 Self Review

### 📁 1. 파일 구조 및 구성
- [x] 역할별로 디렉토리 분리 (`/css`, `/js`, `/images`)
- [x] 인라인 스타일, 스크립트 제거 → 외부 파일로 분리 완료
- [x] 파일/폴더 네이밍 일관성 유지

---

### 🧱 2. HTML 리뷰
```html
 <button type="button" class="m_btn">
                            <img src="img/고객문의.png" alt="" class="image before">
                            <img src="img/고객문의_color.png" alt="" class="image after">
                            <p>고객문의</p>
                        </button><!-- m_btn -->

```

- [x] `heading` 태그는 순차적으로 구조화 진행 (`<h1>` `<h2>` `<h3>` ..)
- [ ] 이미지 태그의 alt 속성 중 일부 누락, 접근성 개선을 위해 alt 속성 보완 필요
- [x] `<h1>`태그는 footer 내 한 번만 사용되어 시멘틱 구조 적절함 (중복 사용 없음)
- [x] 시멘틱 태그 `<header>`, `<main>`, `<section>`, `<footer>`를 적절히 활용해 문서 구조가 명확함
- [ ] `<label>` 태그가 드롭다운 `<select>` 요소에 연결되어 있지 않음 사용자와 보조기술의 이해를 돕기 위해 `<label>` 추가 필요

---

### 🎨 3. CSS 리뷰
- [x] 중복 스타일 최소화 및 공통 클래스 추출하여 코드 재사용성 강화
- [x] 미디어 쿼리 활용하여 반응형 웹 구현 완료, 다양한 화면 크기에 적응
- [x] 초기값, 공통된 요소 하나의 페이지에서 모두 작성 → reset.css, common.css분리하여 정리 예정
- [x] flex, grid 레이아웃을 적절히 활용해 레이아웃 구조를 직관적으로 설계함
- [ ] 일부 선택자가 너무 구체적이거나 중복되어 스타일 유지보수 시 어려움 가능성 존재
- [ ] 접근성 관련 스타일 강화 고려

---

### ⚙️ 4. JavaScript 리뷰

```javascript

$(function () {
  const sliders = [];

  $('.menu_slider').each(function (i, el) {
    const swiper = new Swiper($(el).find('.swiper')[0], {
      slidesPerView: 5,
      spaceBetween: 20,
      breakpoints: {
        1024: { slidesPerView: 5 },
        768: { slidesPerView: 4 },
        360: { slidesPerView: 3 },
        0: { slidesPerView: 2 },
      },
      loop: false,
    });
    sliders.push(swiper);
  });

  $('.menu_tabs button').on('click', function () {
    const target = $(this).data('target');

    $('.menu_tabs button').removeClass('active');
    $(this).addClass('active');

    $('.menu_slider').removeClass('active');
    $('.menu_slider.' + target).addClass('active');
  });

  let regionData = {
    seoul: ["강남구", "서초구", "종로구", "마포구", "용산구"],
    busan: ["해운대구", "수영구", "사하구", "중구", "연제구"],
    daegu: ["중구", "동구", "서구", "달서구", "수성구"],
    incheon: ["부평구", "남동구", "연수구", "서구", "중구"],
    gwangju: ["동구", "서구", "남구", "북구", "광산구"]
  };
});

```

- 자바스크립트와 제이쿼리 구분을 위해 변수명 앞에 $ 추가함

- [x] 메뉴 토글, 스크롤 애니메이션 등 기능 구현 완료
- [x] 지역 선택에 따라 하위 지역을 동적으로 업데이트하는 로직으로 사용자 편의성 제고
- [x] slidesPerView를 화면 크기별로 세분화해 반응형 UX 향상
- [ ] 이벤트 핸들러에서 jQuery .on() 방식을 통일해 사용하면 일관성 및 확장성 증가
- [ ] 스크립트 분리(현재 `<script>`가 HTML 내 임베디드 상태) 및 모듈화 고려

```javascript

 $('.menu_slider').each(function (i, el) {
    const swiper = new Swiper($(el).find('.swiper')[0], {
      slidesPerView: 5,
      spaceBetween: 20,
      breakpoints: {
        1024: { slidesPerView: 5 },
        768: { slidesPerView: 4 },
        360: { slidesPerView: 3 },
        0: { slidesPerView: 2 },
      },
      loop: false,
    });
    sliders.push(swiper);
  });

```
- 탭 전환 시 슬라이더가 정상적으로 초기화 및 리프레시되도록 처리 보완 필요

---

### 🎯 5. UX/UI 측면
- [x] 인터랙션 요소에 hover 및 focus 스타일 제공
- [x]  `nav_mobile` 메뉴와 토글 버튼이 존재하며, 미디어 쿼리로 모바일/PC 메뉴 구분 처리되어 있고, JS로 토글 이벤트도 연결된 상태
- [ ] CSS에서 .section별 구분은 있지만 일부 섹션 내 요소들의 여백, 정렬이 조금 더 명확해지면 시각적 계층 구조가 더 개선될 수 있음
      
---

## 🛠️ 개선 계획 (To-Do)
- [ ] `<img>` 태그의 alt 속성이 일부 빈 값 또는 누락됨 접근성 향상을 위해 의미 있는 대체 텍스트 보완 필요
- [ ] 메인 콘텐츠 중 제목 구조가 더 명확할 필요 있음
- [ ] 이벤트 핸들러 등록 시 jQuery .on() 메서드로 통일
- [ ] 불필요한 font파일 제거

---
