---
title: "5.HTML과CSS를 이용한 연습 다섯번째"
excerpt: " '생활용품 판매 사이트' 전문가와 코린이의 코딩 비교 "
categories:
  - htmlandcss
tags:
  - jekyll
last_modified_at: 2018-07-01T13:00:00+09:00
toc: true
toc_sticky: true
---

## 1.생활용품 판매 사이트

- 웹페이지

<img src="/assets/images/practice/household/household01.PNG" width="40%"> <img src="/assets/images/practice/household/household02.PNG" width="40%">

- 반응형 웹페이지

<img src="/assets/images/practice/household/household03.PNG" width="80%">

- 모바일

<img src="/assets/images/practice/household/household04.PNG" width="30%">

## 코드 비교

- **HTML 구성(1) : 전체적인 뼈대**

  - Expert code : 전체를 header, cover, contents, footer로 잡고 그 안에를 l_wrapper로 잡았다.

  ```html
  <body>
    <div class="header">
      <div class="l_wrapper">
        Header
      </div>
    </div>
    <div class="cover">
      <div class="l_wrapper">
        Cover
      </div>
    </div>
    <div class="contents">
      <div class="section">
        <div class="l_wrapper">
          Section 1
        </div>
      </div>
    </div>
    <div class="footer">
      <div class="l_wrapper">
        footer
      </div>
    </div>
  </body>
  ```

  ```css
  .l_wrapper {
    width: 980px;
    border: 1px solid red;
    margin: 0 auto;
  }
  ```

  - Yosup code : wrapper을 하나로 잡고 Wrapper 안에 header , main , footer로 구성헀다.

  ```html
  <body>
    <div class="wrapper">
      <header>
        <div class="upper"></div>
      </header>
      <main>
        <div class="sort"></div>
      </main>
      <footer>
        <div class="lower clearfix"></div>
      </footer>
    </div>
  </body>
  ```

  ```css
  .wrapper {
    max-width: 1280px;
    margin: 0 auto;
  }
  ```

* **HTML 구성(2) : Header 와 cover 부분**

  - Expert code : 전문가의 경우 header부분을 따로 잡고 cover부분을 따로 잡은뒤 cover 부분에 negative margin을 주었다.

  ```html
  <body>
    <div class="header">
      <div class="l_wrapper">
        <div class="header-inside clearfix">
          <a class="header-logo" href="#"> </a>
          <ul class="header-menu">
            <li><a href="">Shop</a></li>
            <li><a href="">Blog</a></li>
            <li><a href="">Membership</a></li>
          </ul>
        </div>
      </div>
    </div>

    <div class="cover">
      <div class="l_wrapper">
        <div class="cover-contents">
          <h1>Welcome to a world of inspiration for your home</h1>
          <p>
            Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus
            consectetur explicabo officiis architecto et placeat consequatur
            porro hic aliquam! Neque quos nulla modi dolores accusantium
            perferendis mollitia ratione quod ad?
          </p>
        </div>
      </div>
    </div>
  </body>
  ```

  - Yosup code(1) : 이미지를 주었기 때문에 이미지는 blcok이라 upper-box가 이미지 밑으로 떨어졌고, 그것을 position을 이용해 이미지 위에다가 올렸다. 직접적으로 이미지에다가 position: relative를 줄수 없어 같은 높이에 있기에 upper에다가 relative를 주었다.

  ```html
  <header>
    <div class="upper">
      <img
        src="/assets//images/practice/household/header-cover.png"
        alt="이미지"
        class="upper-img"
      />
      <div class="upper-box">
        <ul class="l_row clearfix border_white">
          <li class="l_col l_col_6_10 ">
            <img
              src="/assets/images/practice/household/logo.png"
              alt="로고"
              class="menu-img"
            />
          </li>
          <li class="l_col l_col_1_10 border_white ">
            <div class="item">
              <strong class="box-title textmiddle ">SHOP</strong>
            </div>
          </li>
          <li class="l_col l_col_1_10 border_white">
            <div class="item">
              <strong class="box-title textmiddle ">BLOG</strong>
            </div>
          </li>
          <li class="l_col l_col_2_10 border_white">
            <div class="item">
              <strong class="box-title textmiddle ">Membership</strong>
            </div>
          </li>
        </ul>

        <div class="box-inform">
          <h1>
            <span>Welcome to a world of</span>
            <br />
            <span>inspiration for your home</span>
          </h1>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing
            elit.Reprehenderit
            <br />
          </p>
        </div>
      </div>
    </div>
  </header>
  ```

  ```css
  .upper {
    position: relative;
    /* background-image: url("/assets//images/practice/household/header-cover.png"); */
    height: 500px;
    /* 이걸 vh로 잡아보니 ipad같은 높이가 긴거에서도 60%가 잡혀버리니까 조금 이상해지는것 같다
    따라서 그냥 고정값을 주자 */
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
  }

  .upper-img {
    width: 100%;
    height: 100%;
  }

  .upper-box {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    padding: 30px 0 0 0;
  }
  ```

  - Yosup code(2) : 배경으로 이미지를 주니, 따로 position을 할 필요가 없었다.

  ```html
  <header>
    <div class="upper">
      <!-- <img
            src="/assets//images/practice/household/header-cover.png"
            alt="이미지"
            class="upper-img"
      /> -->
      <div class="upper-box">
        <ul class="l_row clearfix border_white">
          <li class="l_col l_col_6_10">
            <img
              src="/assets/images/practice/household/logo.png"
              alt="로고"
              class="menu-img"
            />
          </li>
          <li class="l_col l_col_1_10 border_white">
            <div class="item">
              <strong class="box-title textmiddle">SHOP</strong>
            </div>
          </li>
          <li class="l_col l_col_1_10 border_white">
            <div class="item">
              <strong class="box-title textmiddle">BLOG</strong>
            </div>
          </li>
          <li class="l_col l_col_2_10 border_white">
            <div class="item">
              <strong class="box-title textmiddle">Membership</strong>
            </div>
          </li>
        </ul>

        <div class="box-inform">
          <h1>
            <span>Welcome to a world of</span>
            <br />
            <span>inspiration for your home</span>
          </h1>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing
            elit.Reprehenderit
            <br />
            praesentium suscipitvoluptatem amet neque maxime optio hic
            placeat,<br />
          </p>
        </div>
      </div>
    </div>
  </header>
  ```

  ```css
  .upper {
    background-image: url("/assets//images/practice/household/header-cover.png");
    height: 500px;
    /* 이걸 vh로 잡아보니 ipad같은 높이가 긴거에서도 60%가 잡혀버리니까 조금 이상해지는것 같다
  따라서 그냥 고정값을 주자 */
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
  }
  .upper-img {
    height: 100%;
  }
  .upper-box {
    padding: 30px 0 0 0;
  }
  ```

결론 : 어떤 데이터의 목적이 아닌 꾸미는 용도의 이미지는 background로 쓰는게 좋겠다. 또한 굿이 upper 자체가 재활용으로 쓰지 않을것이기 때문에
upper-box라는것을 굳이 만들필요 없고, upper-box에 있는 padding을 upper에다가 줘도 같은 결과값을 얻을수 있었다.

- **HTML 구성(3) : header의 text 위치**

  - Expert code : 너비를 주어 텍스트가 길면 그 너비를 넘어갈시 띄어쓰기가 되게끔 하였다

  ```html
  <div class="cover">
    <div class="l_wrapper">
      <div class="cover-contents">
        <h1>Welcome to a world of inspiration for your home</h1>
        <p>
          Lorem, ipsum dolor sit amet consectetur adipisicing elit. Possimus
          consectetur explicabo officiis architecto et placeat consequatur porro
          hic aliquam! Neque quos nulla modi dolores accusantium perferendis
          mollitia ratione quod ad?
        </p>
      </div>
    </div>
  </div>
  ```

  ```css
  .cover-contents {
    padding: 60px 0;
    max-width: 450px;
  }
  ```

  - Yosup code : text가 오른쪽에 위치해야하는데, 텍스트가 길어서 원하는 모습이 나오지 않아 br 테그를 사용하여 위치를 지정했다. 허나 이런방법은 너무 좋지 못한방법같다. 전문가처럼 너비를 주면 그 텍스트가 길어도 너비 밑으로 떨어지는데...

  ```html
  <div class="box-inform">
    <h1>
      <span>Welcome to a world of</span>
      <br />
      <span>inspiration for your home</span>
    </h1>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit.Reprehenderit
      <br />
      praesentium suscipitvoluptatem amet neque maxime optio hic placeat,<br />
    </p>
  </div>
  ```

* **HTML 구성(4) : Main 첫번쨰 부분**

  - Expert code : 전문가는 이번에는 좀 특별하게 해보기 위해 diplay : table이라는것을 사용했지만 ,자주 사용하지는 않는것 같다. 장점이라면 테이블의 갯수를 조절해도 알아서 비율을 유지한다는것이다. 단점은 너비를 100%를 줬다고 해서 자식들의 너비가 100%안으로 모두 들어가는게 아니다. 이게 너무 큰 단점이기에 잘 사용하지 않음, 특이한 점은, table테그를 사용하는것이 아닌 ul li 테그를 사용하고 display를 줬다는 것이다. 그 이유는 HTML의 목적이 브라우저에게 이런게 있다고 알려주기위함인데 지금의 grid는 Table의 목적으로 사용되는용도가 아니기 때문인것같다.

  **특별한 점이라고 하면 이미지안에 들어가는 텍스트의 가운데 정렬을 하기 위해 position과 transform 을 사용했다.**

  ```html
  <div class="contents">
    <div class="category">
      <div class="l_wrapper">
        <div class="category-wrapper">
          <ul class="category-list">
            <li>
              <a href="#" class="category-anchor">
                <img
                  src="/assets/images/practice/household/cat01.png"
                  alt=""
                  class="category-anchor-bg"
                />
                <strong>Chairs</strong>
              </a>
            </li>
            <!-- css단에서 background로 이미지를 주면 안된다. 예전에 배웠듯이 css를 배경화면으로 주는 이유는 바로 중요하지 않는거에만 그렇게 했고, 이 말은 외부에서 데이터를 받아서 와야하는 부분의 경우 background를 쓰면 안된다. -->
          </ul>
        </div>
      </div>
    </div>
    <div class="section">
      <div class="l_wrapper">
        Section 1
      </div>
    </div>
  </div>
  ```

  ```css
  .category {
    background-color: rgba(0, 0, 0, 0.2);
    padding: 10px 0;
  }
  .category-wrapper {
    margin: 0 -5px;
  }
  /* 위쪽과 카테고리의 좌우를 맞추기 위해 */
  .category-list {
    display: table;
    width: 100%;
  }

  .category-list li {
    display: table-cell;
  }
  /* css단에서 table로 만들기? 
  table로 만든 grid의 장점은 테이블의 갯수를 조절해도
  알아서 그 비율을 유지한다는것이다.*/

  .category-anchor {
    display: block;
    background-color: red;
    height: 50px;
    margin: 0 5px;
    position: relative;
  }

  .category-anchor-bg {
    width: 100%;
  }

  .category-anchor::after {
    content: " ";
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    background-color: #000;
    opacity: 0.5;
  }
  /* 이미지를 조금 어둡게 해서 글자를 더 잘 보이게 하기 위한 CSS */

  .category-anchor strong {
    position: absolute;
    left: 0;
    right: 0;
    top: 50%;
    text-align: center;
    transform: translateY(-50%);
    /*  transform: translateY(-50%); 이게 뭐지? */
    color: white;
    z-index: 10;
  }
  ```

  - Yosup code : float로 grid를 만들어보았다.
    나 역시 가운데 정렬을 위해 position 과 transform을 사용하였다. 하지만 다른점은 나는 이러한 꼴이 더 많이 쓰일것 같아 가운데 정렬을 하는 css를 commoms로 따로 빼서 클래스를 줬다.

  ```html
  <main>
    <div class="sort">
      <ul class="l_row clearfix">
        <li class="l_col l_col_2_12 l_col_4_mb_12">
          <a href="#">
            <div class="item2">
              <img
                src="/assets/images/practice/household/cat01.png"
                alt=""
                class="sort-img"
              />
              <h2 class="sort-title textmiddle">Chairs</h2>
            </div>
          </a>
        </li>
      </ul>
    </div>
  </main>
  ```

  ```css
  .sort {
    padding: 10px;
  }

  .item2 {
    position: relative;
  }
  .item2 .sort-img {
    height: 70px;
  }

  .item2 .sort-title {
    position: absolute;
  }
  .textmiddle {
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    /* 가운데 정렬 완성.. 이게 의미하는게 뭔지 알아보자 */
  }
  ```

* **HTML 구성(5) : Main 첫번쨰 부분의 a테그 버튼**

  - Expert code : a테그 안에 img 와 strong 테그를 넣었고 a테그를 조절하여 누를떄의 범위를 크게하였다.

  ```html
  <li>
    <a href="#" class="category-anchor">
      <img
        src="/assets/images/practice/household/cat01.png"
        alt=""
        class="category-anchor-bg"
      />
      <strong>Chairs</strong>
    </a>
  </li>
  ```

  ```css
  .category-anchor {
    display: block;
    background-color: red;
    height: 50px;
    margin: 0 5px;
    position: relative;
  }

  .category-anchor-bg {
    width: 100%;
  }

  .category-anchor::after {
    content: " ";
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    background-color: #000;
    opacity: 0.5;
  }
  /* 이미지를 조금 어둡게 해서 글자를 더 잘 보이게 하기 위한 CSS */

  .category-anchor strong {
    position: absolute;
    left: 0;
    right: 0;
    top: 50%;
    text-align: center;
    transform: translateY(-50%);
    /*  transform: translateY(-50%); 이게 뭐지? */
    color: white;
    z-index: 10;
  }
  ```

  - Yosup code : a테그안에 또다른 div테그를 만들어서 div테그의 css를 조절하여 누를때의 범위를 크게하였다. 굳이 또 하나의 div테그를 넣을 필요가 있었을까? 테그는 적게쓸수록 좋다했는데~

  ```html
  <li class="l_col l_col_2_12 l_col_4_mb_12">
    <a href="index.html">
      <div class="item2">
        <img
          src="/assets/images/practice/household/cat01.png"
          alt=""
          class="sort-img"
        />
        <h2 class="sort-title textmiddle">Chairs</h2>
      </div>
    </a>
  </li>
  ```

  ```css
  .item2 {
    position: relative;
  }
  .item2 .sort-img {
    height: 70px;
  }

  .item2 .sort-title {
    position: absolute;
  }
  ```

* **HTML 구성(6) : Main 두번째 부분(layout)**

  - Expert code : sidebar에 float 를 주고 main에 overflow로 main과 sidebar의 영역을 나눴다. 그리고 sidebar부분이 float로 떳기때문에 내용이 길어지게 되면 footer 부분을 침범하게 된다. 따라서 이를 방지하고자 clearfix를 주었다.

  또한 l_sidebar 안에 또다른 div를 만들어서 그 안에 h2와 p 테그를 넣었는데, l_sidebar는 꾸미는 용도가 아니므로 꾸밈을 당할 또다른 테그를 선언해줘야한다고 li에 또다른 div를 넣었을때부터 말했다.

  ```html
  <div class="section">
    <div class="l_wrapper clearfix">
      <div class="l_sidebar">
        <div class="section-title">
          <h2>Merry Holiday</h2>
          <p>6 Best</p>
        </div>
      </div>
      <div class="l_main"></div>
    </div>
  </div>
  ```

  ```css
  .l_sidebar {
    float: left;
    width: 200px;
  }

  .l_main {
    border: 1px solid white;
    overflow: hidden;
  }

  .section-title {
    background-color: red;
  }
  .clearfix::after {
    content: " ";
    display: block;
    clear: both;
  }
  ```

  - Yosup code : 두곳에 float 를 주었다. 그리고 부모에게 뜬 자식들을 알려주기 위해 clearfix를 해주었다.솔직히 내가 더 잘한코드처럼 느껴진다. 왜냐 overflow의 목적이 이런용도가 아니기 때문으로 알고 있다.

  나는 l_title 밑에 또다른 div테그를 만들지 않고 바로 h1과 p 테그를 넣었다. 이럴경우 배경색을 바꾸고 싶은 마음이 들때 l_title을 건드려야할수가 있다.따라서 l_title 밑에 새로은 div테그를 선언해주고 그 테그에 꾸미는 요소를 적용시켜야한다

  ```html
  <div class="contents">
    <div class="l_list clearfix">
      <div class="l_title">
        <h1>Lighting</h1>
        <p>merry Chrismas 2019</p>
      </div>

      <div class="l_grid"></div>
    </div>
  </div>
  ```

  ```css
  .l_title {
    width: 20%;
    float: left;
    padding: 20px 10px;
  }
  .l_grid {
    float: left;
    width: 80%;
  }
  ```

- **HTML 구성(6) : Main 두번째 부분(grid)**

  - Expert code : Grid의 class 이름을 정할때, 그 grid가 축구관련된 내용이라고 해도 특정 이름인 즉 l_soccer 이렇게 잡으면 안된다. 왜냐하면 계속 사용할 공통의 이름으로 만들어야지 저렇게 잡아버리면 다른곳에서 grid를 재활용해서 사용하지 못하기 때문이다.

  따라서 grid를 만들때 ul과 li의 class이름을 l_row , l_col 으로 잡는 이유이다.

  CSS에서 전문가는 padding으로 생기는 오른쪽 , 왼쪽 , 그리고 아래의 공간을 없애고 좀더 깔끔한 grid를 만들었다.

  ```html
  <div class="section">
    <div class="l_wrapper clearfix">
      <div class="l_sidebar">
        <div class="section-title">
          <h2>Merry Holiday</h2>
          <p>6 Best</p>
        </div>
      </div>
      <div class="l_main">
        <ul class="l_row">
          <li class="l_col">
            <div class="item">
              Item
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
  ```

  ```css
  .l_row {
    margin: -20px -10px 0 -10px;
  }
  .l_col {
    float: left;
    width: 33.3333333%;
    padding: 0 10px;
    box-sizing: border-box;
    margin-top: 20px;
  }
  ```

  - Yosup code : 전문가와 비슷하게 잡았지만, a테그 안에 div테그가 있는데, 이게 좋은방법일까?? 아니면 div테그 안에 a테그를 만들어서 넣는게 좋을방법일까?? 라는 의문이 든다.

  CSS 부분은 나는 따로 손보지 않았는데..

  ```html
  <div class="l_grid">
    <ul class="l_row clearfix">
      <li class="l_col l_col_4_12 l_col_12_mb_12">
        <a href="#">
          <div class="item3"></div>
        </a>
      </li>
    </ul>
  </div>
  ```

  ```css
  .l_row {
    width: auto;
  }
  .l_col {
    float: left;
    width: 10%;
    padding: 5px;
  }
  ```

- **HTML 구성(7) : footer 부분**

  - Expert code : 위에서 사용했던 l_sidebar와 l_main 클래스를 그대로 재활용해서 사용하돼, float의 위치만 다르게 할 필요가 있어 추가적인 클래스를 넣어주었다

  ```html
  <div class="footer">
    <div class="l_wrapper">
      <div class="footer-content">
        <div class="l_sidebar l_sidebar_right"></div>
        <div class="l_main"></div>
      </div>
    </div>
    <div class="footer-copyright"></div>
  </div>
  ```

  ```css
  .l_sidebar_right {
    float: right;
  }
  ```

* Yosup code : 새로운 footer를 만들었다.. 재활용할수 있는것은 재활용해서 사용하자 !!

  ```html
  <footer>
    <div class="lower clearfix">
      <div class="additional">
        <h2>Helpful Links</h2>
        <ul>
          <li><a href="#">how to shop</a></li>
          <li><a href="#">Product availability</a></li>
          <li><a href="#">IKEB Cards</a></li>
        </ul>
      </div>
      <div class="additional">
        <h2>Customer Relations</h2>
        <ul>
          <li><a href="#">FAQ</a></li>
          <li><a href="#">Contact us</a></li>
          <li><a href="#">Delivery Tracking</a></li>
        </ul>
      </div>
      <div class="additional">
        <h2>News Room</h2>
        <ul>
          <li><a href="#">Corporate PR</a></li>
          <li><a href="#">Commercial PR</a></li>
          <li><a href="#">Product recalls</a></li>
        </ul>
      </div>
    </div>
  </footer>
  ```

  - **CSS 구성 : 전체적인 부분**

  - Expert code : CSS의 선택자가 header, main(cover,section), footer 을 이해하기가 쉽게 표현되어있다. 처음 본 사람이 그냥 봐도 어떤부분인지 이해가 됨

  ```css
  /* Reset */
  body,
  ul,
  p {
    margin: 0;
    padding: 0;
  }

  li {
    list-style-type: none;
  }

  a {
    color: inherit;
    text-decoration: none;
  }
  /* Typography */
  html {
    font-size: 62.5%;
    line-height: 1.4;
  }
  body {
    font-size: 1.4rem;
  }

  /* body가 아닌 html에 한 이유는 html에 typography를 적기로 약속했기 때문이다. */

  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
    font-size: 100%;
    font-weight: normal;
    margin: 0;
  }

  /* h1~6까지의 font를 두껍게 하지 않고 일반적으로 한다음
  나중에 css에서 영향을 준다
  옛날에 말햇듯이 테그들은 브라우저에게 알려주기 위함이지
  어떠한 꾸미는 용도가 아니라고 했으므로 이렇게 해주는것 같다. */

  /* Commons */

  .clearfix::after {
    content: " ";
    display: block;
    clear: both;
  }

  /* Layouts */

  .l_wrapper {
    max-width: 980px;
    border: 1px solid red;
    margin: 0 auto;
    padding: 0 20px;
  }

  .l_sidebar {
    background-color: red;
    float: left;
    width: 200px;
  }

  .l_sidebar_right {
    float: right;
  }

  .l_main {
    border: 1px solid white;
    overflow: hidden;
  }

  .l_row {
    margin: -20px -10px 0 -10px;
  }

  .l_col {
    float: left;
    width: 33.3333333%;
    padding: 0 10px;
    box-sizing: border-box;
    margin-top: 20px;
  }

  /* Components */
  body {
    background-color: #0e0e0e;
    color: #999;
  }

  .header {
    color: white;
    padding: 20px 0;
    position: relative;
    /* 여기서의 position relative의 역할? */
  }
  .header-inside {
    border: 1px solid white;
  }

  .header-logo {
    background-color: orange;
    float: left;
    background-image: url("/assets/images/practice/household/logo.png");
    width: 115px;
    height: 40px;
    background-size: cover;
    /* 이미지들은 준비할때 적용할 CSS보다 큰 것을 준비해야
    CSS적용시에도 깨지지 않는다. */
  }

  .header-menu {
    float: right;
  }

  .header-menu li {
    float: left;
    border-left: 1px solid;
  }
  .header-menu li a {
    height: 40px;
    display: block;
    padding: 0 10px;
    line-height: 40px;
    /* line-height 는 위 아래에 40px을 20px씩 줘서 
    가운데 정렬을 하게끔 만들어준다.; */

    /* menu li vs menu li a 
    이 둘중  어떤곳에 높이를 주는것이 좋을까?
    바로 a 테그한테 주는것이 좋다. 그 이유는 a가 눌려야하는데 a를 크게하면 실질 메뉴처럼 누를수 있기 때문이다. 하지만 a테그는 inline이므로 block으로 처리해줘야한다.*/
  }

  .cover {
    background-color: #666;
    background-image: url("/assets/images/practice/household/header-cover.png");
    color: white;
    background-size: cover;
    background-position: center;
    margin-top: -82px;
    padding-top: 82px;
  }

  .cover-contents {
    padding: 60px 0;
    max-width: 450px;
  }

  .cover-contents h1 {
    font-size: 4rem;
    margin-bottom: 20px;
    line-height: 1.2;
  }

  .cover-contents p {
    color: #666;
    line-height: 1.4;
  }

  .contents {
  }

  .category {
    background-color: rgba(0, 0, 0, 0.2);
    padding: 10px 0;
  }
  .category-wrapper {
    margin: 0 -5px;
  }
  /* 위쪽과 카테고리의 좌우를 맞추기 위해 */

  .category-list {
    display: table;
    width: 100%;
  }

  .category-list li {
    display: table-cell;
  }
  /* css단에서 table로 만들기? 
  table로 만든 grid의 장점은 테이블의 갯수를 조절해도
  알아서 그 비율을 유지한다는것이다.
  그러나 단점은 너비를 100%를 줬다고 해서 
  자식들의 너비가 100%안으로 모두 들어가는게 아니다.
  이게 너무 큰 단점이기에 잘 사용하지 않음*/

  .category-anchor {
    display: block;
    background-color: red;
    height: 50px;
    margin: 0 5px;
    position: relative;
  }

  .category-anchor-bg {
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
    height: 100%;
  }

  .category-anchor::after {
    content: " ";
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    background-color: #000;
    opacity: 0.5;
  }
  /* 이미지를 조금 어둡게 해서 글자를 더 잘 보이게 하기 위한 CSS */

  .category-anchor strong {
    position: absolute;
    left: 0;
    right: 0;
    top: 50%;
    text-align: center;
    transform: translateY(-50%);
    /*  transform: translateY(-50%); 이게 뭐지? */
    color: white;
    z-index: 10;
  }

  .section {
    background-color: red;
  }

  .footer {
    background-color: blue;
  }
  ```

  - Yosup code : 선택자의 이름이 부분별하고 , 나만 봤을때 이해가 가능 CSS 선택자 사용..

  ```css
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  body {
    background-color: black;
    color: white;
    text-transform: capitalize;
    font-size: 80%;
  }

  img {
    display: block;
    max-width: 100%;
  }

  p {
    color: #777;
  }

  a {
    text-decoration: none;
    color: white;
  }

  main img {
    opacity: 0.5;
  }

  main a:hover img {
    opacity: 1;
    transition: all 0.5s ease-in-out;
  }
  /* layout */

  .l_row {
    width: auto;
  }
  .l_col {
    float: left;
    width: 10%;
    padding: 5px;
  }

  .l_title {
    width: 20%;
    float: left;
    padding: 20px 10px;
  }
  .l_grid {
    float: left;
    width: 80%;
  }

  /* components */
  .wrapper {
    max-width: 1280px;
    margin: 0 auto;
  }

  .upper {
    background-image: url("/assets//images/practice/household/header-cover.png");
    height: 500px;
    /* 이걸 vh로 잡아보니 ipad같은 높이가 긴거에서도 60%가 잡혀버리니까 조금 이상해지는것 같다
    따라서 그냥 고정값을 주자 */
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    padding: 30px 0 0 0;
  }

  .upper-img {
    height: 100%;
  }

  .upper-box {
    padding: 30px 0 0 0;
  }

  .item {
    position: relative;
    height: 80px;
  }

  .box-title {
    position: absolute;
  }

  /* 여기서 item에게 padding을 주는게 맞는걸까?? 이거 수정이 필요할것 같은 느낌이 든다.*/

  .box-inform {
    padding: 10px;
  }

  .box-inform h1 {
    padding: 30px 0;
  }

  .sort {
    padding: 10px;
  }

  .item2 {
    position: relative;
  }
  .item2 .sort-img {
    height: 70px;
  }

  .item2 .sort-title {
    position: absolute;
  }

  .contents {
    padding: 50px 10px;
  }

  .item3 {
    position: relative;
  }

  .item3 .grid-title {
    position: absolute;
    padding: 10px;
    bottom: 0;
    left: 0;
    font-family: "Nanum Gothic", sans-serif;
  }

  .lower {
    padding: 0 10px 40px 10px;
  }
  .additional {
    float: left;
    margin-right: 20px;
  }
  .additional h2 {
    margin: 10px 0px;
  }

  .additional a {
    color: #777;
  }

  /* 이미지는 텍스트이기때문에 다른요소가 absolute를 잡았을때 relative 역할을 못하나보다 */

  /* commons */

  .clearfix::after {
    content: " ";
    display: block;
    clear: both;
  }

  .textmiddle {
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    /* 가운데 정렬 완성.. 이게 의미하는게 뭔지 알아보자 */
  }

  .border_white {
    border: 1px solid white;
  }

  /* utility */

  .l_col_10_10 {
    width: 100%;
  }
  .l_col_9_10 {
    width: 90%;
  }
  .l_col_8_10 {
    width: 80%;
  }
  .l_col_7_10 {
    width: 70%;
  }
  .l_col_6_10 {
    width: 60%;
  }
  .l_col_5_10 {
    width: 50%;
  }
  .l_col_4_10 {
    width: 40%;
  }
  .l_col_3_10 {
    width: 30%;
  }
  .l_col_2_10 {
    width: 20%;
  }
  .l_col_1_10 {
    width: 10%;
  }

  .l_col_12_12 {
    width: 100%;
  }
  .l_col_11_12 {
    width: 91.66666667%;
  }
  .l_col_10_12 {
    width: 83.33333333%;
  }
  .l_col_9_12 {
    width: 75%;
  }
  .l_col_8_12 {
    width: 66.66666667%;
  }
  .l_col_7_12 {
    width: 58.33333333%;
  }
  .l_col_6_12 {
    width: 50%;
  }
  .l_col_5_12 {
    width: 41.66666667%;
  }
  .l_col_4_12 {
    width: 33.33333333%;
  }
  .l_col_3_12 {
    width: 25%;
  }
  .l_col_2_12 {
    width: 16.66666667%;
  }
  .l_col_1_12 {
    width: 8.33333333%;
  }

  /* mediaqueries  */

  /* laptop */

  /* tablet */
  @media screen and (max-width: 768px) {
    body {
      font-size: 60%;
    }
    .l_title {
      width: auto;
    }
    .l_grid {
      width: auto;
    }
  }
  /* mobile */
  @media screen and (max-width: 430px) {
    body {
      font-size: 55%;
    }

    .l_col_12_mb_12 {
      width: 100%;
    }
    .l_col_11_mb_12 {
      width: 91.66666667%;
    }
    .l_col_10_mb_12 {
      width: 83.33333333%;
    }
    .l_col_9_mb_12 {
      width: 75%;
    }
    .l_col_8_mb_12 {
      width: 66.66666667%;
    }
    .l_col_7_mb_12 {
      width: 58.33333333%;
    }
    .l_col_6_mb_12 {
      width: 50%;
    }
    .l_col_5_mb_12 {
      width: 41.66666667%;
    }
    .l_col_4_mb_12 {
      width: 33.33333333%;
    }
    .l_col_3_mb_12 {
      width: 25%;
    }
    .l_col_2_mb_12 {
      width: 16.66666667%;
    }
    .l_col_1_mb_12 {
      width: 8.33333333%;
    }
  }
  ```

### 꿀팁~

- 1.외부에서 데이터를 받아서 와야하는 부분의 경우 css단에서 background로 이미지를 주면 안된다. 예전에 배웠듯이 css를 배경화면으로 주는 이유는 바로 중요하지 않는거에만 그렇게 했다. 데이터의 의미를 지닌 이미지의 경우는 img 테그를 써야한다.

* 2.transform 에 대한 내용

## 결론

- **1. float를 이용한 grid는 한계가 있다.**

* **2. 재활용할 layout을 잡는게 중요하며, layout을 잡을때 숲을 먼저 잡는게 중요하다.**

- **3. layout을 잡은 테그는 배경이나, 어떠한 꾸미기 용도가 아니다, 따라서 꾸미는 용도의 테그를 하나 더 잡아줘야 한다.**

* **4. 재활용될수 있는 영역을 판단하고 , 재활용을 하자**

- **5. 클래스의 이름을 다른사람이 봐도 명확하게 이해할수 있도록 작성하자**
