<template>
  <div class="order-header">
    <div class="container clearfix">
      <div class="header-logo">
        <a href="/#/index"></a>
      </div>
      <div class="title">
        <h2>
          {{title}}
          <slot name="tip" />
        </h2>
      </div>
      <div class="username">
        <a href="javascript:;" v-if="username">{{username}}</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "order-header",
  props: {
    title: String
  },
  computed: {
    username() {
      return this.$store.state.username;
    }
  }
};
</script>

<style lang="scss">
@import "./../assets/scss/mixin.scss";
.order-header {
  padding: 30px 0;
  border-bottom: 2px solid #ff6600;
  .header-logo {
    float: left;
    width: 55px;
    height: 55px;
    background-color: #ff6600;
    a {
      display: inline-block;
      width: 110px;
      height: 55px;
      &::before {
        content: "";
        @include bgImg(55px, 55px, "/imgs/mi-logo.png", 55px);
        transition: margin 0.2s;
      }
      &:after {
        content: "";
        @include bgImg(55px, 55px, "/imgs/mi-home.png", 55px);
      }
      &:hover:before {
        margin-left: -55px;
        transition: margin 0.2s;
      }
    }
  }
  .title,
  .username {
    display: inline-block;
    height: 55px;
    line-height: 55px;
  }
  .title {
    font-size: 28px;
    float: left;
    color: #333333;
    margin-left: 55px;
    span {
      font-size: 14px;
      margin-left: 16px;
      color: #999999;
      font-weight: bold;
    }
  }
  .username {
    float: right;
    a {
      color: #666666;
      font-size: 16px;
    }
  }
}
</style>