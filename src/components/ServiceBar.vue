<template>
  <div class="service">
    <div class="container">
      <ul>
        <li>
          <span class="icon icon-setting" />
          <span>预约维修服务</span>
        </li>
        <li>
          <span class="icon icon-7day" />
          <span>7天无理由退货</span>
        </li>
        <li>
          <span class="icon icon-15day" />
          <span>15天无理由换货</span>
        </li>
        <li>
          <span class="icon icon-post" />
          <span>满150元包邮</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "service-bar"
};
</script>

<style lang="scss">
@import "./../assets/scss/mixin.scss";
.service {
  padding: 32px 0;
  color: #666666;
  font-size: 16px;
  li {
    display: inline-block;
    width: 24.9%;
    height: 20px;
    line-height: 20px;
    text-align: center;
    border-right: 1px solid #e5e5e5;
    span {
      display: inline-block;
      vertical-align: middle;
    }
    .icon {
      width: 20px;
      height: 20px;
      margin-right: 8px;
    }
    .icon-setting {
      @include bgImg(20px, 20px, "/imgs/icon-setting.png");
    }
    .icon-7day {
      @include bgImg(20px, 20px, "/imgs/icon-7day.png");
    }
    .icon-15day {
      @include bgImg(20px, 20px, "/imgs/icon-15day.png");
    }
    .icon-post {
      @include bgImg(20px, 20px, "/imgs/icon-post.png");
    }
  }
}
</style>