---
title: "12.포트폴리오 클론코딩 만들기 CSS 비교(feat.Ellie)(별 100만개)"
excerpt: "javascript 프로젝트 열한번째 CSS"
categories:
  - jsproject
tags:
  - jekyll
last_modified_at: 2018-07-01T13:00:00+09:00
toc: true
toc_sticky: true
---

## 코딩비교

- 1. 적절하게 CSS를 사용했는가?

  - 굳이 안써도 되는 CSS를 사용했는가?

  - 쉽게 사용했어도 될 CSS인데 어렵게 사용한 CSS가 있나?

  * Mobile 까지 생각하고 CSS를 적용했나?

### CSS 비교(1) - global 부분

- Expert Code :

* 1. 자주 사용될 요소들은 무조건 root를 만들어서 사용햇다.

* 2. h1 과 h2 등 자주 사용하는 테그들도 미리 지정해줌 --> 코드의 간략화를 위함인듯

```css
/* Global */

:root {
  /* Color */

  --color-white: #ffffff;

  --color-light-white: #eeeeee;

  --color-dark-white: #bdbdbd;

  --color-pink: #fe918d;

  --color-dark-pink: #ff6863;

  --color-dark-grey: #4d4d4d;

  --color-grey: #616161;

  --color-light-grey: #7c7979;

  --color-blue: #73aace;

  --color-yellow: #fff7d1;

  --color-orange: #feb546;

  --color-black: #000000;

  /* Font size */

  --font-large: 48px;

  --font-medium: 28px;

  --font-regular: 18px;

  --font-small: 16px;

  --font-micro: 14px;

  /* Font weight */

  --weight-bold: 700;

  --weight-semi-bold: 600;

  --weight-regular: 400;

  /* size */

  --size-border-radius: 4px;

  /* animation duration */

  --animation-duration: 300ms;
}

/* Universal tags */
* {
  box-sizing: border-box;
}

/*  */

body {
  margin: 0;
  font-family: "Open Sans", sans-serif;
  cursor: default;
}

a {
  text-decoration: none;
  color: var(--color-white);
}

ul {
  list-style: none;
  padding-left: 0;
}

button {
  background-color: transparent;
  cursor: pointer;
  border: none;
  outline: none;
}

/* Section common */

.section {
  padding: 50px;
  text-align: center;
  margin: auto;
}

.section__container {
  max-width: 1200px;
  margin: auto;
}

/* Typography */

h1 {
  font-size: var(--font-large);

  font-weight: var(--weight-bold);

  color: var(--color-black);

  margin: 16px 0px;
}

h2 {
  font-size: var(--font-medium);

  font-weight: var(--weight-semi-bold);

  color: var(--color-black);

  margin: 8px 0;
}

h3 {
  font-size: var(--font-regular);

  font-weight: var(--weight-regular);

  color: var(--color-black);

  margin: 8px 0;
}

p {
  font-size: var(--font-regular);

  font-weight: var(--weight-regular);

  color: var(--color-black);

  margin: 4px 0;
}
```

### CSS 비교(2) - header , nav 부분

- Expert Code :

* 1. 첫번째로는 **하위요소 선택자 사용을 하지 않았다는점**

- 2. **바뀌지 않을 큰 태그들은 id로 지정했다는점**

* 3. **공통으로 자주 사용될 요소들은 root로 지정해서 사용했다는점**

```css
#navbar {
  display: flex;
  justify-content: space-between;
  background-color: var(--color-pink);
  align-items: center;
  padding: 16px;
  color: var(--color-white);
}

.navbar__menu {
  display: flex;
}

.navbar__logo {
  font-size: var(--font-medium);
  font-weight: var(--weight-semi-bold);
}

.navbar__menu__item {
  padding: 8px 12px;
  margin: 0 4px;
  cursor: pointer;
  border-radius: var(--size-border-radius);
}

.navbar__menu__item.active {
  border: 1px solid var(--color-white);
}

.navbar__menu__item:hover {
  background-color: var(--color-dark-pink);
}
```

- Yosup Code

```css
.container {
  background-image: url(/imgs/background.png);
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  color: rgba(255, 255, 255, 0.8);
}

.nav {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 10px 10px 30px 10px;
}

.nav .nav__logo {
  flex: 1 1 50%;
  font-size: 20px;
}

.nav .nav__menubar {
  flex: 1 1 50%;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}

.nav .nav__menubar a {
  padding: 7px;
  background-color: inherit;
  border-radius: 3px;
}
```

### CSS 비교(3) - 이미지 설명 부분(home, intro)

- Expert Code

* 1. root의 사용으로 좀더 간결해보이는 코딩이 되었다.
* 2. 또한 자주사용되는 테그인 h1,h2,h3 등은 이미 앞에서 padding과 margin이 적용된 상태이므로 여기서 따로 padding과 margin을 줄 필요가 없어서 더 보기 좋은 코드인것 같다.

- 3. **text-align을 통한 자식 태그들의(블록요소는 적용X) 가운데 정렬을 함**

```css
#home {
  background-image: url("/imgs/background.png");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  padding: 40px;
  text-align: center;
}

.home__avatar {
  width: 250px;
  height: 250px;
  border-radius: 50%;
  border: 2px solid var(--color-light-white);
}

.home__title,
.home__description {
  color: var(--color-white);
}

.home__contact {
  font-size: var(--font-regular);
  font-weight: var(--weight-bold);
  margin: 24px;
  border: 2px solid var(--color-dark-white);
  border-radius: var(--size-border-radius);
}
```

- Yosup Code

```css
.intro {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 50px;
}

.intro .intro__img {
  border-radius: 50%;
  max-width: 130px;
  margin-bottom: 15px;
  display: inline-block;
}

.intro .intro__title {
  width: 100%;
  margin-bottom: 15px;
  text-align: center;
  font-size: var(--font-h1);
}

.intro .intro__inform {
  margin-bottom: 15px;
  font-size: var(--font-h3);
}

.intro button {
  border: 2px solid rgba(255, 255, 255, 0.8);
  margin-bottom: 30px;
  color: rgba(255, 255, 255, 0.8);
  padding: 7px;
  background-color: inherit;
  border-radius: 3px;
}
```

### CSS 비교(4) - 첫번째 section 부분

- Expert Code

* 1. 어차피 h1,h2는 위에서 공통으로 지정해줬기때문에, 따로 CSS를 주지 않았다

* 2. 어차피 h1,h2, block 요소이므로 이것을 포함하는 부모한테 flex 와 flex-direction:column을 주지 않으신것 같다.
     ( ellie reply : 만약 가운데 정렬 하는것만 필요하다면 구지 flex를 쓰시는것보다 text-align을 쓰는게 좋을 것 같아요)

```css
.about__majors {
  display: flex;
  justify-content: space-between;
  margin: 80px 0;
}

.major__icon {
  width: 170px;
  height: 170px;
  font-size: 70px;
  line-height: 170px;
  background-color: yellow;
  margin: auto;
  border: 1px solid var(--color-blue);
  border-radius: 50%;
  margin-bottom: 16px;
  color: blue;
}

.major__icon i {
  transition: all var(--animation-duration) ease;
  /* 사용자가 사용하기에 적합한 시간이
  250~350ms */
}

.major__icon:hover i {
  color: var(--color-pink);
  transform: rotate(-30deg) scale(1.1);
}

.major__title,
.major__description {
  color: var(--color-dark-grey);
}

.major__description {
  font-size: var(--font-small);
}
```

- Yosup Code

* 1. **공통적인 요소에도 따로 CSS를 주니까 코드가 길어지는 현상이 발생하였다.**

- 2. **flex를 사용하지 않아도 세로형식으로 diplay가 되는데 굳이 flex-direction : column울 주었다.**

```css
.about {
  margin-bottom: 50px;
}

.about__container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 85%;
  margin: 0 auto;
}

.about__container__title {
  font-size: var(--font-h1);
  margin-bottom: 20px;
  display: block;
}
.about__container__introduce {
  text-align: center;
  margin-bottom: 20px;
}

.about__container__items {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.about__container__items .item {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  flex: 0 1 25%;
}
.about__container__items .item .item__iconbox {
  display: flex;
  width: 150px;
  height: 150px;
  border: 1px solid #5b56f4;
  background-color: inherit;
  border-radius: 50%;
  justify-content: center;
  align-items: center;
  margin-bottom: 10px;
}
.about__container__items .item .item__iconbox i {
  font-size: 50px;
  color: #5b56f4;
}

.about__container__items .item .item__title {
  font-size: var(--font-h2);
  margin-bottom: 10px;
}
.about__container__items .item .item__detail {
  text-align: center;
}
```

### CSS 비교(5) - 두번째 section 부분

- Expert Code

- 1. **value 를 통해 width를 적용하게 되면 모든값이 적용되므로, 따로 CSS를 클래스를 만들어서 적용해주실줄 알았지만, 이런 것들은 나중에 데이터를 받아서 표현되어야 하므로 HTML tag에서 적용되어야한다. 이런것들은 따로 추출해서 json에서 관리해서 동적으로 받아온것들을 HTML 코드로 변환해서 자동적으로 생성해야하므로!!**

* 2. 코드의 양이 현저히 적은것이 보인다. 그 이유는, 기존에 많이 사용할 것들의 태그는 이미 만들어져 재활용된다는것과, 굳이 사용하지 않아도 될 CSS를 사용했다는 점과 HTML에서 div가 너무 남용되었다는것

```css
/* skill */
#skills {
  background-color: var(--color-yellow);
}

.skillset {
  display: flex;
  background-color: var(--color-light-grey);
  color: var(--color-light-white);
  margin: 20px 0;
}

.skillset__title {
  color: var(--color-white);
}

.skillset__left {
  flex-basis: 60%;
  background-color: var(--color-dark-grey);
  padding: 20px 40px;
}

.skill {
  margin-bottom: 32px;
}

.skill_description {
  display: flex;
  justify-content: space-between;
}

.skill__bar {
  width: 100%;
  height: 3px;
  background-color: var(--color-grey);
}
.skill__value {
  height: 3px;
  background-color: var(--color-orange);
}

.skillset__right {
  flex-basis: 40%;
}

.tools {
  background-color: var(--color-grey);
}
```

- Yosup Code

* 1. flex에 미쳤나보다.. 굳이 이걸 flex를 사용해서 bar을 나타내다니..

- 2. 코드의 양이 너무 많다.. 이제는 어떠한 방법으로든 화면을 구현할수 있게되었나. 하지만 코드의 양을 줄이는 방법을 아는것이 중요하겠다.

```css
.skills {
  background-color: #f9f1ca;
  margin-bottom: 50px;
}

.skills__container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 85%;
  margin: 0 auto;
}

.skills__container__title {
  font-size: var(--font-h1);
  margin-top: 50px;
  margin-bottom: 20px;
}
.skills__container__subtitle {
  font-size: var(--font-h2);
  margin-bottom: 10px;
}

.skills__container__introduce {
  text-align: center;
  margin-bottom: 50px;
}
.skills__container__box {
  width: 100%;
  display: flex;
  flex-direction: row;
  margin-bottom: 30px;
}

.box__rightbox {
  display: flex;
  flex-direction: column;
  justify-content: center;
  color: rgba(255, 255, 255, 0.8);
  flex: 1 1 60%;
  background-color: #5b5757;
}

.box__rightbox .rightbox__title {
  font-size: var(--font-h3);
  padding: 20px;
}

.box__rightbox ul {
  padding: 0 40px;
  width: 100%;
}

.box__rightbox ul li {
  margin-bottom: 30px;
}

.rightbox__title {
  text-align: center;
  font-size: var(--font-h3);
}

.rightbox__list {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 5px;
}
.rightbox__list span {
  text-transform: uppercase;
}

.percent {
  display: flex;
  flex-direction: row;
  width: 100%;
}

.percent .percent__right {
  height: 3px;
  background-color: #eac300;
}
.percent .percent__left {
  height: 3px;
  background-color: #7c7979;
}

.box__leftbox {
  color: rgba(255, 255, 255, 0.8);
  flex: 1 1 40%;
  background-color: #7c7979;
  text-align: center;
}

.leftbox__tools {
  height: 60%;
}

.leftbox__tools .tools__title {
  padding: 20px;
  font-size: var(--font-h3);
}

.box__leftbox .leftbox__etc {
  background-color: #ada9a9;
  height: 40%;
}
.leftbox__etc .etc__title {
  padding: 20px;
  font-size: var(--font-h3);
}
```

### CSS 비교(6) - 세번째 section 부분

- Expert Code

* 1. transition과 transform으로도 다양한 animation을 줄수 있다.

* 2. line-height 에 대해서 알아두는것이 좋겠다.

```css
/* work */

.work__categories {
  margin: 40px;
}

.category__btn {
  border: 1px solid var(--color-dark-white);
  border-radius: var(--size-border-radius);
  font-size: var(--font-regular);
  padding: 8px 48px;
}

.category__btn.active,
.category__btn:hover {
  background-color: var(--color-pink);
  color: var(--color-white);
}

.category__btn.active,
.category__btn:hover .category__count {
  opacity: 1;
  top: 0;
}

.category__count {
  background-color: var(--color-orange);
  border-radius: 50%;
  color: var(--color-white);
  width: 24px;
  height: 24px;
  line-height: 24px;
  display: inline-block;
  /* span은 line요소이므로 content를 꽉 잡아주게 생겼다
  따라서 inline-block으로 바꿔야함 */
  position: relative;
  top: -20px;
  left: 4px;
  opacity: 0;
  transition: all var(--animation-duration) ease;
}

.work__projects {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

/* 여기에 고정값을 준 이유는, 사실 디자이너의 맘이긴한데 내가 화면을 줄여도 개수만 바뀌고 그 크기를 유지하고 싶을때는 이렇게 고정값을 준다
 */
.project {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 280px;
  height: 250px;
  margin: 2px;
  background-color: var(--color-light-white);
}

.project__img {
  max-width: 100%;
  max-height: 100%;
}

.project__description {
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: absolute;
  background-color: black;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  opacity: 0;
  transform: translateY(10px);
  transition: all var(--animation-duration) ease;
}

.project:hover .project__description {
  opacity: 0.8;
  transform: translateY(0);
}

.project__description h3 {
  color: var(--color-white);
}

.project__description h3:after {
  content: " ";
  width: 25px;
  height: 2px;
  background-color: var(--color-dark-white);
  position: relative;
  left: 50%;
  margin-left: -12px;
  margin-top: 8px;
}
```

- Yosup Code

```css
.work {
  color: black;
  margin-bottom: 50px;
}

.work__container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.work__container__title {
  font-size: var(--font-h1);
  margin-bottom: 20px;
}

.work__container__subtitle {
  font-size: var(--font-h3);
  margin-bottom: 20px;
}

.work__container__menu {
  display: flex;
  flex-direction: row;
  justify-content: center;
  text-align: center;
  margin-bottom: 20px;
}
.work__container__menu a {
  border: 2px solid rgba(84, 61, 61, 0.39);
  padding: 5px 30px;
  background-color: rgba(255, 255, 255, 0.486);
  border-radius: 3px;
}

.work__container__items {
  width: 100%;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

/* 이렇게 grid를 짜는게 맞을려나..?? */
.work__container__items .item {
  flex: 1 1 25%;
  background-color: white;
  margin-left: -10px;
}

.work__container__items .item img {
  padding: 0 0px 10px 10px;
  max-width: 100%;
  vertical-align: top;
}
```

### CSS 비교(7) - 네번째 section 부분

- Expert Code

```css
#testimonials {
  background-color: var(--color-grey);
}

.testimonials {
  margin: 40px;
}

.testimonial {
  display: flex;
}
.testimonial__avatar {
  width: 150px;
  height: 150px;
  border-radius: 50%;
}

.testimonial__speech-bubble {
  padding: 18px;
  background-color: var(--color-white);
  border-radius: var(--size-border-radius);
}

.testimonial__avatar:nth-child(odd) {
  margin-right: 40px;
}

.testimonial__avatar:nth-child(even) {
  margin-left: 40px;
}

.testimonial__speech-bubble p {
  color: var(--color-dark-white);
}

.testimonial__speech-bubble a {
  color: var(--color-dark-pink);
}
```

- Yosup Code

* 1. 소개하는 부분에 높이를 정해버리니, 안의 content가 늘어나면 그 소개하는 부분의 높이를 content가 초과해버리는 현상이 발생했다. 이 부분을 고치기 위해 높이의 px을 제거해버리니, content의 높이에 따라 같이 소개하는 부분의 높이가 증가하게 되었다.

- 2. 중복되는 코드가 있네, 충분히 고칠수 있었는데..

* 3. 코드가 너무 길다..

```css
.testimonials {
  background-color: #eae5e5;
  margin-bottom: 50px;
}

.testimonials__container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 85%;
  margin: 0 auto;
}

.testimonials__container__title {
  font-size: var(--font-h1);
  margin-top: 50px;
  margin-bottom: 20px;
}
.testimonials__container__subtitle {
  font-size: var(--font-h3);
  margin-bottom: 20px;
}

.container__items {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.container__items .item {
  width: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-bottom: 20px;
}
.container__items .item img {
  border-radius: 50%;
  width: 130px;
  height: 130px;
}

/* 중복되는 코드 고치는법 */
.container__items .item .item__inform:nth-child(even) {
  width: 100%;
  height: 130px;
  text-align: center;
  background-color: aliceblue;
  border-radius: 5px;
  padding: 20px;
  margin-left: 30px;
}
.container__items .item .item__inform:nth-child(odd) {
  width: 100%;
  height: 130px;
  text-align: center;
  background-color: aliceblue;
  border-radius: 5px;
  padding: 20px;
  margin-right: 30px;
}

.item__inform p {
  padding-bottom: 10px;
}
```

### CSS 비교(8) - footer 부분

- Expert Code

```css
/* contact */

#contact {
  background-color: var(--color-pink);
}

.contact__title,
.contact__email,
.contact__right {
  color: var(--color-white);
}

.contact__title {
  margin: 32px 0;
}

.contact__links {
  font-size: var(--font-large);
  margin: 24px 0;
}

.contact__links i {
  transition: all var(--animation-duration) ease;
}
.contact__links i:hover {
  transform: scale(1.1);
  color: var(--color-yellow);
}
```

- Yosup Code

* flex 남발...

```css
.talk {
  color: white;
  background-color: #f9a2a2;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.talk .talk__title {
  margin: 50px 0px;
  font-size: var(--font-h1);
}

.talk .talk__email {
  margin-bottom: 20px;
  font-size: var(--font-h2);
}

.talk .talk__sns {
  margin-bottom: 20px;
  display: flex;
  flex-direction: row;
}
.talk .talk__rights {
  margin-bottom: 20px;
  font-size: var(--font-h3);
}
```

### CSS 비교(9) - 쿼리부분

- Expert

* 1. 미디어 쿼리에서는 최소한의 CSS만 작업해야한다.
  - 에를들어 즉 여기서는 toggle버튼의 보여지고 안보여지는 정도만 작업해야지 여기서 toggle의 색상이나 어떠한 크기는 하면 안되고 미디어가 아닌 CSS에서 작업을 해줘야한다.

```css
@media screen and (max-width: 760px) {
  .navbar__toggle-btn {
    display: block;
  }
  #navbar {
    flex-direction: column;
    align-items: flex-start;
  }

  .navbar__menu {
    flex-direction: column;
    text-align: center;
    width: 100%;
  }

  .about__majors {
    flex-direction: column;
  }

  .major {
    margin-bottom: 38px;
  }

  .skillset {
    flex-direction: column;
  }

  .project {
    flex-grow: 1;
  }
}
```

Yosup :

- 1. **flex를 남용하다보니(display:flex 나 flex) 반응형 웹을 만들때 즉 미디어 쿼리에서 바꿔야하는 코드가 많아짐을 느꼈다. 이말인 즉슨 쓸대없는 CSS의 남용은 , 나중에 고칠게 많음을 알게 된 순간이었다. 또한 미디어쿼리에서 어떻게 동작할지도 미리 생각해놓고 짜야지만 미디어쿼리에서의 코딩양을 줄일수가 있다.**

- **2. 또한 CSS에서 자식요소의 선택자를 자주쓸때 나중에 미디어쿼리에서 우선순위 문제가 발생할수 있기때문에, 최대한 CSS에서 자식선택자를 자주 쓰지는 말자.**

```css
.nav {
  flex-direction: column;
}
.nav__logo {
  flex-direction: row;
  display: flex;
  width: 100%;
  justify-content: space-between;
}
.nav__toggle {
  display: block;
}

.nav .nav__menubar {
  flex-direction: column;
}
```

### CSS Ellie vs Yosup 총평

- 1. 자주 사용되는 CSS는 역시 root로 변수를 만드는것이 코딩이 더 깔금해보이며, h1,h2,h3,h4 , p 와 같은 자주 사용되므로 같은 간격을 유지하는경우 굳이 계속 CSS를 주기보다 다음과 같이 하는것이 보기 더 깔끔하다.

```css
h1 {
  font-size: var(--font-large);

  font-weight: var(--weight-bold);

  color: var(--color-black);

  margin: 16px 0px;
}

h2 {
  font-size: var(--font-medium);

  font-weight: var(--weight-semi-bold);

  color: var(--color-black);

  margin: 8px 0;
}

h3 {
  font-size: var(--font-regular);

  font-weight: var(--weight-regular);

  color: var(--color-black);

  margin: 8px 0;
}

p {
  font-size: var(--font-regular);

  font-weight: var(--weight-regular);

  color: var(--color-black);

  margin: 4px 0;
}
```

- 2. 굳이 flex를 사용하지 않아도 될 부분(가운데정렬)에 flex를 사용해서 코드의 양을 늘려버렸다.

  - **ellie reply : 만약 가운데 정렬 하는것만 필요하다면, 구지 flex를 쓰시는것보다 text-align을 쓰는게 좋을 것 같아요**

* 3. **value 를 통해 width를 적용하게 되면 모든값이 적용되므로, 따로 CSS를 클래스를 만들어서 적용해주실줄 알았지만, 이런 것들은 나중에 데이터를 받아서 표현되어야 하므로 HTML tag에서 적용되어야한다. 이런것들은 따로 추출해서 json에서 관리해서 동적으로 받아온것들을 HTML 코드로 변환해서 자동적으로 생성해야하므로!!**

- 4. 이제는 어떠한 방법으로든 화면을 구현할수 있게되었나. 하지만 **코드의 양을 줄이는 방법을 아는것이 중요하겠다.**

  - 재활용

  - CSS의 클래스명을 길게쓰지말기 !!

  * 굳이 사용하지 않아도 될 CSS 사용 금지 (flex 남용금지..)

  - section 이나 header 같은 테그들을 모습만 갖추는것이 아니라 사용하기(section이나 header는 id로 작성하기)

* 5. **HTML, CSS를 잘 짜놔야지 반응형 만들때 코드가 많이 안들어간다.!!**

- 6. **미디어 쿼리는 최소한의 CSS 작업만 할수 있게~**

* 7. **flex를 남용하다보니(display:flex 나 flex) 반응형 웹을 만들때 즉 미디어 쿼리에서 바꿔야하는 코드가 많아짐을 느꼈다.이말인 즉슨 쓸대없는 CSS의 남용은 , 나중에 고칠게 많음을 알게 된 순간이었다. 또한 미디어쿼리에서 어떻게 동작할지도 미리 생각해놓고 짜야지만 미디어쿼리에서의 코딩양을 줄일수가 있다.**

- 8. **또한 CSS에서 자식요소의 선택자를 자주쓸때 나중에 미디어쿼리에서 우선순위 문제가 발생할수 있기때문에, 최대한 CSS에서 자식선택자를 자주 쓰지는 말자.(ex) .parent .child .childson{} (x) , .childson{} (o)**
