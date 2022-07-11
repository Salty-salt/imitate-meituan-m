<template>
  <div class="home">
    <div class="c_header">
      <div class="header_city">
        北京
      </div>
      <div class="header_serach ellipse">
        <img class="search_icon" src="~@/assets/search.png">
        请输入商家名、品类名或者商圈
      </div>
      <div class="operate_wrap">
        <img class="operate_btn" src="~@/assets/people.png">
      </div>
    </div>
    <div class="c-guide-app">
      <div class="guide-content">
        <img class="guide-logo" src="~@/assets/loggo.png">
        <p class="content-wrap">
          <span class="content-title">省钱利器 购物超划算</span>
          <span class="content-desc">吃喝玩乐尽在美团</span>
        </p>
      </div>
      <button class="guide-btn">去APP</button>
    </div>
    <div class="home-body">
      <div class="home-module category-module">
        <div class="category-list-wrap">
         <!-- <div class="category-wrap" v-for="(item, index) in list1" :key="index">
            <img class="category-img" :src="item.img">
            <span class="category-text">{{ item.title }}</span>
          </div>-->
          <div class="category-wrap" v-for="(item, index) in list1" :key="index" >
            <img class="category-img" :src="item.img">
            <span class="category-text">{{ item.title }}</span>
          </div>
        </div>
      </div>
      <div class="home-module recommend-module">
        <h5 class="module-title">猜你喜欢</h5>
        <div class="recommond-list module-list">
          <div class="recommond-card" v-for="(item,index) in list2" :key="index">
            <div class="card-img-wrap">
              <img class="card-img" :src="item.img">
            </div>
            <div class="card-info-wrap">
              <div class="card-title-wrap">
                <div class="card-title ellipse">{{item.title}}</div>
                <div class="card-desc">{{item.subTitle}}</div>
              </div>
              <div class="card-price-wrap">
                <span class="card-price">
                  {{item.price}}
                  <span class="price-unit">元</span>
                </span>
                <span class="market-price">
                  门市价：
                  <!-- -->
                  ￥{{item.priceOrigin}}
                </span>
                <span class="discount-condition"></span>
              </div>
            </div>
          </div>
        </div>
        <div class="recommend-all-text">查看全部团购</div>
      </div>
    </div>
    <footer class="c-footer">
      <div class="footer-info">
        <div class="footer-user"><button class="mt-btn user-btn">登录</button></div>
        <div class="footer-city">
          <span class="city-label">城市：</span>
          <img class="footer-city-icon" src="~@/assets/location.png">
          <span class="city-text">北京</span>
        </div>
      </div>
      <ul class="main-link-wrap">
        <li class="main-link">首页</li>
        <li class="main-link">我的</li>
        <li class="main-link">美团下载</li>
        <li class="main-link">电脑版</li>
        <li class="main-link">帮助</li>
      </ul>
      <ul class="friend-link-wrap">
        <li class="friend-link-label">友情链接：</li>
        <li class="friend-link-label">猫眼电影</li>
        <li class="friend-link-label">大众点评</li>
        <li class="friend-link-label">美团旅馆</li>
        <li class="friend-link-label">榛果民宿</li>
        <li class="friend-link-label">大众点评下载</li>
        <li class="friend-link-label">美团餐饮系统</li>
        <li class="friend-link-label">美团餐饮培训</li>
        <li class="friend-link-label">快驴进货商家合作</li>
        <li class="friend-link-label">商机/招聘</li>
      </ul>
      <div class="footer-certificate">
        <div class="footer-hr"></div>
        <span class="certificate-text">©2021 美团网 京ICP证070791号</span>
      </div>
    </footer>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    // HelloWorld
  },
  data () {
    return {
      list1: [],
      list2: []
    }
  },
  created () {
    this.getlist1()
    this.getlist2()
  },
  methods: {
    getlist1 () {
      fetch('https://www.fastmock.site/mock/98ee8ea5c4480fe466f4d200671417a2/mt_test/category', {
        method: 'post',
        headers: {
          'Content-Type': 'application/json'
        }
      }).then(res => res.json())
        .then(res => {
          console.log(res)
          if (res.status === 0) {
            this.list1 = res.result
          }
        })
    },
    getlist2 () {
      fetch('https://www.fastmock.site/mock/98ee8ea5c4480fe466f4d200671417a2/mt_test/list', {
        method: 'post',
        headers: {
          'Content-Type': 'application.json'
        }
      }).then(res => res.json())
        .then(res => {
          console.log(res)
          if (res.status === 0) {
            this.list2 = res.result
          }
        })
    }
  }
}
</script>
<style>
.c_header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  position: relative;
  width: 100vw;
  height: 13.3vw;
  padding: 0 4vw;
  box-sizing: border-box;
  background: linear-gradient(135deg, #ffd000, #ffbd00);
}

.c_header .header_city {
  display: flex;
  align-items: center;
  margin-right: 4vw;
  flex-shrink: 0;
  font-size: 3.7vw;
  font-family: PingFangSC-Medium
}

.c_header .header_serach {
  flex: 1;
  display: flex;
  align-items: center;
  height: 8.5vw;
  padding: 0 3.5vw;
  border-radius: 2.1vw;
  background-color: #fff;
  font-size: 3.5vw;
  color: #999;
}

.c_header .header_serach .search_icon {
  width: 3.7vw;
  margin-right: 1.6vw;
}

.c_header .operate_wrap {
  margin-left: 4vw;
  flex-shrink: 0;
}

.c_header .operate_wrap .operate_btn {
  width: 6.4vw;
}

body img,
html img {
  border: 0;
  content: normal !important;
  vertical-align: top;
}

.c-guide-app {
  width: 100vw;
  padding: 2.1vw 4vw;
  box-sizing: border-box;
  background-color: #000;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.c-guide-app .guide-content {
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

.c-guide-app .guide-content .content-wrap {
  display: flex;
  flex-direction: column;
  margin: 0;
  padding-left: 2.7vw;
  color: #fff;
}

.c-guide-app .guide-content .guide-logo {
  width: 9.6vw;
}

p {
  margin-block-start: 1em;
  margin-block-end: 1em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
}

.c-guide-app .guide-content .content-wrap .content-title {
  font-size: 3.5vw;
  font-weight: 600;
}

.c-guide-app .guide-content .content-wrap .content-desc {
  font-size: 2.9vw;
  padding-top: .8vw;
}

.c-guide-app .guide-btn {
  border: none;
  height: 8vw;
  padding: 0 2.1vw;
  background-image: linear-gradient(135deg, #ffd000, #ffbd00);
  border-radius: 1.9vw;
  font-size: 3.2vw;
  color: #333;
}

button {
  appearance: button;
  -webkit-writing-mode: horizontal-tb !important;
  text-rendering: auto;
  letter-spacing: normal;
  word-spacing: normal;
  text-transform: none;
  text-indent: 0px;
  text-shadow: none;
  display: inline-block;
  text-align: center;
  align-items: flex-start;
  cursor: default;
  background-color: -internal-light-dark(rgb(239, 239, 239), rgb(74, 74, 74));
  box-sizing: border-box;
  margin: 0em;
  font: 400 13.3333px Arial;
}

.home .home-body .home-module:first-of-type {
  margin-top: 0;
}

.home .home-body .category-module {
  padding: 2.7vw 3.2vw;
}

.home .home-body .home-module {
  width: 100%;
  box-sizing: border-box;
  margin-top: 2.7vw;
  background-color: #fff;
}

div {
  display: block;
}

.category-list-wrap {
  display: grid;
  grid-template-columns: repeat(5, 13.3vw);
  grid-gap: 5.3vw 6.4vw;
}

.category-list-wrap .category-wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.category-list-wrap .category-wrap .category-img {
  width: 11.2vw;
}

.category-list-wrap .category-wrap .category-text {
  margin-top: 1.9vw;
  font-size: 3.2vw;
  color: #333;
}

.home .home-body .recommend-module {
  display: flex;
  flex-direction: column;
  flex: 1;
  min-height: 26.7vw;
  padding: 3.7vw 2.7vw 0;
}

.home .home-body .home-module {
  width: 100%;
  box-sizing: border-box;
  margin-top: 2.7vw;
  background-color: #fff;
}

.home .home-body .recommend-module .module-title {
  flex-shrink: 0;
  margin: 0;
  font-size: 4.5vw;
  color: #333;
}

.home .home-body .recommend-module .module-list {
  flex-grow: 1;
  margin-top: 2.7vw;
}

.recommond-list {
  position: relative;
}

.recommond-card .card-img-wrap {
  display: flex;
  flex-shrink: 0;
  justify-content: center;
  width: 24vw;
  height: 21.9vw;
  overflow: hidden;
  background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAYQAAAEAAQMAAACJUpNeAAAAA3NCSVQICAjb4U/gAAAABlBMVEX///////9VfPVsAAAAAnRSTlMA/1uRIrUAAAAJcEhZcwAACxIAAAsSAdLdfvwAAAAcdEVYdFNvZnR3YXJlAEFkb2JlIEZpcmV3b3JrcyBDUzbovLKMAAAFWUlEQVRoge3aTa7kNBAAYFuWMAtEuIE5yfhiaBxWLLmSb8AVwoolQbMYS4SYqnLs2PmvJ2YEQ1t66rTjLz/lihOnnxBvKirGPi93cX4mhrxs4/RAyBhDXo6PRNWswrDngzJmMa/NHglXhC51dyKuYngibAlv91CYImDJPxR+a69FV4R9LoYixBOhD6J2LdRBX96KkMX0SJRskgwxtfROlMNXj0VOxSoRb0XMYngm7NLV3VuEvxP6sH7+skSJmyi58RKfQGhKvJf45GItpnoOEC/xEp9byIPUDW8Xtq1/iZd4iX9eXF7nn0NU65ijj2ULxxaRKyRbKLbQbGHYwrKFq8UmD3IZGhG5QrKFYgvNFoYtLFs4tohcIdlCsQUG9yNLGPj+G0tgk59YwsF3zRLwdWYJDO7EEhjcwBIwy48jSxj8evjUty1Z4DZ7lsDgHj9ZngkMLktQcI+FPR6vKLgsQcFlCQouS1BwWYKCyxIUXI5IweWIFNxj4Q5FCi5HpOByRAquuL8+fBYpuByRgssQS3AZYgkuQyzBZQrPFj1bCK6Y2WJii8AWI1t4tujZQnDFzBYTWwS2GNnCb0U9MFQvwkUR/amgTQ97kb50eyFPxPJziNmL9BA17sS0eyJrRdiJcCrSM+20E+Op6Kh23gl/Kkyq3on+VNhS3QpxKlzp60Z8ey6g6q+2Q0h8cyqwNrQdQuLrU4HdMbqmQ86eqZeC3THapkO2QrQCg0tz68cCG3vThPdG0IF2TbA2Ym4F5WE6mTMxtYLykNz0UFjarWwyayNCK5aNNHmyEUMj9LIRF9tf+2rhG0GJO+aDOxSzqEXZrakPS7UDRSO6vNsuVod1JVzu0zKBvRG67tO1Ew+EWlbG0kOiZNClSGeRDt9VOzkQmtYtM8p1rpHP5ECY5YE8lh7K+5sXcVBGURbzbvOKW1F+E34sln5jiOUk7XPRl2g8FNX/TDwUOf3kY1H6yt2IIYu+6tZHYh1B9EOxJpC8EX59e9KeyJ2ob7HdtejFAteirkVKpPY/fNyVmJNoLxx9JaYyh6nLlQi02m9EdyFGFEFsizsXcAJH/9gkzwV0XNwDPJUTsT+eV3mV/2b54V8q3n0RQvzPxPdCpo9a9PAn0+JXZe13QkL9Ox2FpReGEN0uTtrjHNBGIUebbo84BuOk26goDFRZmLPj3c3AbSQLD4O7l2N+lJvxkWiglg5aWht/xUHewaaKwEdE+Ue6adP7DwejujVxwCrr4od0lw6rwGdO+SEJAx8Sb4CwbWpp6ZcKT3VF4Psh+THd76AB7nPGbf9JImiYcg1qUjPklRMkzKCDxGoQDr9NMlLLAarsqGDKNehRzJSJSfQS23Qo8EMH4Xo7SmwpLByQ0IMeYPtFWBQzVIOAjxHb9XaglihwFczcbSWEmOREAj4UCuOtJw1WTEmYfisUvjIIQgXjUfQgVBGm34lAQgVAsLYbqCUKkUW3ClGJEfLlUEDn+krISgg8ED1Qy1XYjVCtEAcCn2gqYSY5sgSkyyJ0FuO1iKsYklDXQrFFFwNTwMV5L/ACXfvci/szb4QT4ja6hi/6VRj/vhEyHGUJ5po/FSkT9yLlLl48M2bimLOdro90CVRivaLwsqwEJWS6ojZiaIUqYkrX+U7g9ZvOfITx5r3QScAx0SiA1+pWBBpLLBw0DFROdEXA8Ixro9gINUscr+ykJhjxnHdFwLJXs9qJNIqiiPF3j1n24yJsGnfnrUgjNQhY+QuI2WVh0kxo2gm6G+AdJcafvYmhCHq3jWu3gu44+KrVzng3GIpQOCHAtVnkovK0Ir1t7SnRqLihWvuW8jcg0Wxz1AbH1QAAAABJRU5ErkJggg==);
  background-color: #e0e0e0;
  background-size: 50%;
  background-repeat: no-repeat;
  background-position: 50%;
  max-width: 24vw;
}

.recommond-card:first-of-type {
  border-top: .3vw solid #ddd8ce;
}

.recommond-card {
  display: flex;
  align-items: center;
  padding: 1.9vw 0;
  border-bottom: .3vw solid #ddd8ce;
}

.recommond-card .card-img-wrap .card-img {
  height: 21.9vw;
}

.recommond-card .card-info-wrap {
  display: flex;
  max-width: calc(100% - 26.7vw);
  flex-direction: column;
  justify-content: space-between;
  height: 21.9vw;
  margin-left: 2.7vw;
}

.recommond-card .card-info-wrap .card-title {
  font-size: 4vw;
  color: #333;
}

body .ellipse,
html .ellipse {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.recommond-card .card-info-wrap .card-desc {
  font-size: 3.2vw;
  color: #666;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.recommond-card .card-info-wrap .card-price-wrap .card-price {
  font-size: 4.8vw;
  color: #f60;
}

.recommond-card .card-info-wrap .card-price-wrap .price-unit {
  font-size: 3.2vw;
}

.recommond-card .card-info-wrap .card-price-wrap .market-price {
  margin-left: 1.3vw;
  font-size: 3.2vw;
  color: #666;
}

.home .home-body .recommend-module .recommend-all-text {
  height: 10.7vw;
  line-height: 10.7vw;
  font-size: 4vw;
  color: #fe8c00;
  border-bottom: .3vw solid #ddd8ce;
}

.c-footer {
  width: 100vw;
  padding: 4vw 6.7vw;
  box-sizing: border-box;
  font-size: 3.2vw;
  background-color: #fff;
}

footer {
  display: block;
}

.c-footer .footer-info {
  font-size: 3.5vw;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.c-footer .footer-info .footer-user .user-btn {
  color: #222;
  width: 14.7vw;
  height: 7.2vw;
  font-family: PingFangSC-Medium;
  font-size: 3.5vw;
}

.mt-btn {
  background-image: linear-gradient(135deg, #ffd000, #ffbd00);
  border: none;
  border-radius: 1.9vw;
  color: #222;
}

button {
  appearance: button;
  -webkit-writing-mode: horizontal-tb !important;
  text-rendering: auto;
  color: -internal-light-dark(buttontext, rgb(170, 170, 170));
  letter-spacing: normal;
  word-spacing: normal;
  text-transform: none;
  text-indent: 0px;
  text-shadow: none;
  display: inline-block;
  text-align: center;
  align-items: flex-start;
  cursor: default;
  background-color: -internal-light-dark(rgb(239, 239, 239), rgb(74, 74, 74));
  box-sizing: border-box;
  margin: 0em;
  font: 400 13.3333px Arial;
  padding: 1px 6px;
  border-width: 2px;
  border-style: outset;
  border-color: -internal-light-dark(rgb(118, 118, 118), rgb(195, 195, 195));
  border-image: initial;
}

.c-footer .footer-info .footer-city {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.c-footer .footer-info .footer-city .city-label {
  color: #999;
}

.c-footer .footer-info .footer-city .footer-city-icon {
  width: 3.2vw;
  margin-right: .8vw;
}

body img,
html img {
  border: 0;
  content: normal !important;
  vertical-align: top;
}

.c-footer .footer-info .footer-city .city-text {
  font-family: PingFangSC-Medium;
  color: #222;
}

.c-footer .main-link-wrap {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 6.7vw;
  color: #fe8c00;
}

body li,
body ol,
body ul,
html li,
html ol,
html ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

ul {
  display: block;
  list-style-type: disc;
  margin-block-start: 1em;
  margin-block-end: 1em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  padding-inline-start: 40px;
}

.c-footer .main-link-wrap .main-link:first-of-type {
  padding-left: 0;
}

.c-footer .main-link-wrap .main-link:last-of-type {
  padding-right: 0;
  border-right: none;
}

.c-footer .main-link-wrap .main-link {
  line-height: 3.2vw;
  padding: 0 5.3vw;
  border-right: .3vw solid #666;
}

.c-footer .friend-link-wrap {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  margin-top: 4vw;
  color: #646464;
}

.c-footer .friend-link-wrap .friend-link-label {
  margin-top: 2.7vw;
  font-family: PingFangSC-Medium;
}

.c-footer .friend-link-wrap .friend-link {
  margin: 2.7vw 0 0 5.3vw;
  font-family: PingFangSC-Regular;
}

.c-footer .footer-certificate {
  position: relative;
  margin-top: 4vw;
  color: #999;
  text-align: center;
}

.c-footer .footer-certificate .footer-hr {
  position: absolute;
  width: 100%;
  top: 50%;
  border-top: .1vw solid #999;
}

.c-footer .footer-certificate .certificate-text {
  position: relative;
  z-index: 10;
  padding: 0 4vw;
  background-color: #fff;
}

.c-footer .footer-certificate {
  position: relative;
  margin-top: 4vw;
  color: #999;
  text-align: center;
}

.c-footer .friend-link-wrap .friend-link:nth-of-type(2) {
  margin-left: 0;
}
</style>

<!--<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App hhhhh"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>-->
