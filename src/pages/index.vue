<template>
  <div class="index">
    <div class="container">
      <div class="swiper-box">
        <div class="nav-menu">
          <ul class="menu-wrap">
            <li class="menu-item">
              <a href="javascript:;">手机 电话卡</a>
              <div class="children">
                <ul v-for="(item, i) in productList" v-bind:key="i">
                  <li v-for="(sub, j) in item" v-bind:key="j">
                    <a v-bind:href="sub ? '/#/product/' + sub.id: ''">
                      <img v-lazy="sub.img" />
                      <span>{{sub ? sub.name : "小米9"}}</span>
                    </a>
                  </li>
                </ul>
              </div>
            </li>
            <li class="menu-item">
              <a href="javascript:;">电视 盒子</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">笔记本 平板</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">家电 插线板</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">出行 穿戴</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">智能 路由器</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">电源 配件</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">生活 箱包</a>
            </li>
          </ul>
        </div>
        <swiper v-bind:options="swiperOption">
          <swiper-slide v-for="(item, index) in slideList" v-bind:key="index">
            <a v-bind:href="'/#/product/' + item.id">
              <img v-bind:src="item.img" />
            </a>
          </swiper-slide>
          <div class="swiper-pagination" slot="pagination" />
          <div class="swiper-button-prev" slot="button-prev" />
          <div class="swiper-button-next" slot="button-next" />
        </swiper>
      </div>
      <div class="ads-box">
        <a
          v-bind:href="'/#/product/' + item.id"
          v-for="(item, index) in adsList"
          v-bind:key="index"
        >
          <img v-lazy="item.img" />
        </a>
      </div>
    </div>
    <div class="product-box">
      <div class="container">
        <div class="flashsale">
          <div>
            <h2 class="flashsale-title">小米闪购</h2>
            <div class="swiper-flashsale-controls">
              <span class="swiper-flashsale-prev" />
              <span class="swiper-flashsale-next" />
            </div>
          </div>
          <div class="flashsale-body clearfix">
            <div class="countdown">
              <p class="time">14:20 场</p>
              <img src="/imgs/flashsale.png" alt />
              <p class="tip">距离结束还有</p>
              <p>
                <span class="hour">00</span>
                <i>:</i>
                <span class="minute">54</span>
                <i>:</i>
                <span class="second">46</span>
              </p>
            </div>
            <div class="flashsale-list clearfix">
              <swiper v-bind:options="flashsaleSwiperOption">
                <swiper-slide>
                  <div class="flashsale-item">
                    <img src="/imgs/product/gallery-2.png" alt />
                  </div>
                </swiper-slide>
                <swiper-slide>
                  <div class="flashsale-item">
                    <img src="/imgs/product/gallery-3.png" alt />
                  </div>
                </swiper-slide>
                <swiper-slide>
                  <div class="flashsale-item">
                    <img src="/imgs/product/gallery-4.png" alt />
                  </div>
                </swiper-slide>
                <swiper-slide>
                  <div class="flashsale-item">
                    <img src="/imgs/product/gallery-5.jpg" alt />
                  </div>
                </swiper-slide>
                <swiper-slide>
                  <div class="flashsale-item">
                    <img src="/imgs/product/gallery-6.jpg" alt />
                  </div>
                </swiper-slide>
                <swiper-slide>
                  <div class="flashsale-item">
                    <img src="/imgs/product/gallery-2.png" alt />
                  </div>
                </swiper-slide>
                <swiper-slide>
                  <div class="flashsale-item">
                    <img src="/imgs/product/gallery-3.png" alt />
                  </div>
                </swiper-slide>
                <swiper-slide>
                  <div class="flashsale-item">
                    <img src="/imgs/product/gallery-4.png" alt />
                  </div>
                </swiper-slide>
                <swiper-slide>
                  <div class="flashsale-item">
                    <img src="/imgs/product/gallery-5.jpg" alt />
                  </div>
                </swiper-slide>
                <swiper-slide>
                  <div class="flashsale-item">
                    <img src="/imgs/product/gallery-6.jpg" alt />
                  </div>
                </swiper-slide>
                <div class="swiper-pagination" slot="pagination"></div>
              </swiper>
            </div>
          </div>
        </div>
        <div class="banner">
          <a href="/#/product/30">
            <img v-lazy="'/imgs/banner-1.png'" />
          </a>
        </div>
        <h2>手机</h2>
        <div class="wrapper">
          <div class="banner-left">
            <a href="/#/product/35">
              <img v-lazy="'/imgs/mix-alpha.jpg'" />
            </a>
          </div>
          <div class="list-box">
            <div class="list" v-for="(item, i) in phoneList" v-bind:key="i">
              <div class="item" v-for="(sub, j) in item" v-bind:key="j">
                <div class="item-img">
                  <img v-lazy="sub.mainImage" alt />
                  <div class="item-info">
                    <h3>{{sub.name}}</h3>
                    <p>{{sub.subtitle}}</p>
                    <p class="price">{{sub.price | currency}}</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <service-bar />
    <modal
      title="提示"
      sureText="查看购物车"
      btnType="3"
      modalType="middle"
      v-bind:showModal="showModal"
      v-on:submit="showModal=false"
      v-on:cancel="showModal=false"
    >
      <template v-slot:body>
        <p>商品添加成功</p>
      </template>
    </modal>
  </div>
</template>
<script>
import { swiper, swiperSlide } from "vue-awesome-swiper";
import "swiper/dist/css/swiper.css";
import ServiceBar from "./../components/ServiceBar";
import Modal from "./../components/Modal";
export default {
  name: "index",
  components: {
    swiper,
    swiperSlide,
    ServiceBar,
    Modal
  },
  data() {
    return {
      swiperOption: {
        autoplay: {
          delay: 8000
        },
        loop: true,
        speed: 1500,
        effect: "fade",
        fadeEffect: {
          crossFade: true
        },
        pagination: {
          el: ".swiper-pagination",
          clickable: true
        },
        navigation: {
          prevEl: ".swiper-button-prev",
          nextEl: ".swiper-button-next"
        }
      },
      flashsaleSwiperOption: {
        autoplay: {
          delay: 5000
        },
        loop: true,
        slidesPerView: 4,
        spaceBetween: 14,
        pagination: {
          el: ".swiper-pagination",
          clickable: true
        }
      },
      slideList: [
        {
          id: "42",
          img: "/imgs/slider/slide-1.jpg"
        },
        {
          id: "45",
          img: "/imgs/slider/slide-2.jpg"
        },
        {
          id: "46",
          img: "/imgs/slider/slide-3.jpg"
        },
        {
          id: "",
          img: "/imgs/slider/slide-4.jpg"
        },
        {
          id: "",
          img: "/imgs/slider/slide-5.jpg"
        }
      ],
      productList: [
        [
          {
            id: 30,
            img: "/imgs/item-box-1.png",
            name: "小米CC9"
          },
          {
            id: 31,
            img: "/imgs/item-box-2.png",
            name: "小米8青春版"
          },
          {
            id: 32,
            img: "/imgs/item-box-3.jpg",
            name: "Redmi K20 Pro"
          },
          {
            id: 33,
            img: "/imgs/item-box-4.jpg",
            name: "移动4G专区"
          }
        ]
      ],
      adsList: [
        {
          id: 33,
          img: "/imgs/ads/ads-1.png"
        },
        {
          id: 48,
          img: "/imgs/ads/ads-2.jpg"
        },
        {
          id: 45,
          img: "/imgs/ads/ads-3.png"
        },
        {
          id: 47,
          img: "/imgs/ads/ads-4.jpg"
        }
      ],
      phoneList: [],
      showModal: false
    };
  },
  mounted() {
    this.init();
  },
  methods: {
    init() {
      this.axios
        .get("/products", {
          params: {
            categoryId: 100012,
            pageSize: 14
          }
        })
        .then(res => {
          this.phoneList = [res.list.slice(6, 10), res.list.slice(10, 14)];
        });
    }
  },
  filters: {
    currency(val) {
      if (!val) return "未知";
      return val.toFixed(2) + "元起";
    }
  }
};
</script>

<style lang="scss">
@import "./../assets/scss/config.scss";
@import "./../assets/scss/mixin.scss";
.index {
  .swiper-box {
    .nav-menu {
      position: absolute;
      width: 264px;
      height: 450px;
      z-index: 9;
      padding: 26px 0;
      background-color: #55585a7a;
      box-sizing: border-box;
      .menu-item {
        height: 50px;
        line-height: 50px;
        a {
          position: relative;
          display: block;
          font-size: 15px;
          color: #ffffff;
          padding-left: 30px;
          &:after {
            position: absolute;
            right: 30px;
            top: 17.5px;
            content: " ";
            @include bgImg(10px, 15px, "/imgs/icon-arrow.png");
          }
        }
        &:hover {
          background-color: $colorA;
          .children {
            width: 962px;
            border: 1px solid $colorH;
            span {
              opacity: 1;
              transition: opacity 2s;
            }
          }
        }
        .children {
          width: 0;
          height: 450px;
          box-sizing: border-box;
          background-color: $colorG;
          position: absolute;
          overflow: hidden;
          top: 0;
          left: 264px;
          transition: width 0.5s;
          ul {
            display: flex;
            justify-content: space-between;
            height: 75px;
            li {
              height: 75px;
              line-height: 75px;
              flex: 1;
              padding-left: 22px;
            }
            a {
              color: $colorB;
              font-size: 14px;
              span {
                opacity: 0;
                transition: opacity 0.2s;
              }
            }
            img {
              width: 42px;
              height: 35px;
              vertical-align: middle;
              margin-right: 15px;
            }
          }
        }
      }
    }
    .swiper-container {
      height: 450px;
      .swiper-button-prev {
        left: 274px;
      }
      img {
        width: 100%;
        height: 100%;
      }
    }
  }
  .ads-box {
    @include flex();
    margin-top: 14px;
    margin-bottom: 30px;
    a {
      width: 296px;
      height: 168px;
    }
  }
  .product-box {
    background-color: $colorJ;
    padding: 30px 0 50px;
    .flashsale {
      position: relative;
      .swiper-flashsale-controls {
        position: absolute;
        top: 0;
        right: 0;
        .swiper-flashsale-prev,
        .swiper-flashsale-next {
          width: 35px;
          height: 25px;
          border: 1px solid #e0e0e0;
          display: inline-block;
        }
      }
      .flashsale-body {
        .countdown {
          width: 234px;
          height: 340px;
          border-top: 1px solid #e53935;
          text-align: center;
          background: #f1eded;
          float: left;
          .time {
            font-size: 20px;
            color: #ef3a3b;
            margin-top: 55px;
            font-weight: normal;
          }
          img {
            margin: 25px;
            overflow: hidden;
          }
          .tip {
            font-size: 15px;
            color: rgb(0, 0, 54);
            margin-bottom: 28px;
          }
          span {
            width: 46px;
            height: 46px;
            line-height: 46px;
            font-size: 24px;
            background: #605751;
            color: #ffffff;
            text-align: center;
            display: inline-block;
          }
          i {
            width: 15px;
            height: 46px;
            line-height: 46px;
            color: #605751;
            font-size: 28px;
            font-style: normal;
            margin: 0 2px;
          }
        }
        .flashsale-list {
          width: 978px;
          float: left;
          margin-left: 14px;
          .flashsale-item {
            width: 234px;
            height: 340px;
          }
          img {
            width: 100%;
            height: 100%;
            object-fit: cover;
          }
        }
      }
    }
    .banner {
      margin-top: 25px;
      margin-bottom: 50px;
    }
    h2 {
      font-size: $fontF;
      height: 20px;
      line-height: 20px;
      color: $colorB;
      margin-bottom: 20px;
    }
    .wrapper {
      display: flex;
      .banner-left {
        margin-right: 14px;
        img {
          width: 234px;
          height: 620px;
        }
      }
      .list-box {
        .list {
          @include flex();
          width: 978px;
          margin-bottom: 16px;
          &:last-child {
            margin-bottom: 0;
          }
          .item {
            width: 234px;
            height: 302px;
            background-color: $colorG;
            text-align: center;
            padding: 20px 10px 15px;
            box-sizing: border-box;
            .item-img {
              img {
                height: 160px;
                width: 160px;
              }
            }
            .item-info {
              h3 {
                font-size: $fontJ;
                color: $colorB;
                line-height: $fontJ;
                margin-top: 10px;
              }
              p {
                color: #b0b0b0;
                line-height: 12px;
                margin: 6px auto 12px;
                margin-top: 10px;
              }
              .price {
                color: $colorA;
                font-size: $fontJ;
                font-weight: normal;
                cursor: pointer;
                margin-top: 18px;
              }
            }
          }
        }
      }
    }
  }
}
</style>