<template>
  <div class="footer">
    <div class="footer-logo">
      <img src="/imgs/logo-footer.png" alt />
      <p>小米商城</p>
    </div>
    <div class="footer-link">
      <a href="javascript:;">小米商城</a>
      <span>|</span>
      <a href="javascript:;">MIUI</a>
      <span>|</span>
      <a href="javascript:;">米家</a>
      <span>|</span>
      <a href="javascript:;">米聊</a>
      <span>|</span>
      <a href="javascript:;">多看</a>
      <span>|</span>
      <a href="javascript:;">游戏</a>
      <span>|</span>
      <a href="javascript:;">政企服务</a>
      <span>|</span>
      <a href="javascript:;">小米天猫店</a>
      <span>|</span>
      <a href="javascript:;">小米集团隐私政策</a>
      <span>|</span>
      <a href="javascript:;">小米公司儿童信息保护规则</a>
      <span>|</span>
      <a href="javascript:;">小米商城隐私政策</a>
      <span>|</span>
      <a href="javascript:;">小米商城用户协议</a>
      <span>|</span>
      <a href="javascript:;">问题反馈</a>
      <span>|</span>
      <a href="javascript:;">廉正举报</a>
      <span>|</span>
      <a href="javascript:;">诚信合规</a>
    </div>
    <div class="copyright">
      Copyright ©2019
      <span class="domain">mi.futurefe.com</span>All Rights Reserved.
    </div>
  </div>
</template>

<script>
export default {
  name: "nav-footer"
};
</script>
<style lang="scss">
.footer {
  height: 234px;
  border-top: 4px solid #ff6600;
  background-color: #333333;
  color: #999999;
  font-size: 14px;
  text-align: center;
  .footer-logo {
    margin-top: 46px;
    margin-bottom: 30px;
    img {
      width: 52px;
      height: 36px;
      margin-bottom: 12px;
    }
  }
  .footer-link {
    margin-bottom: 12px;
    a {
      color: #999999;
      display: inline-block;
    }
    span {
      margin: 0 6px;
    }
  }
  .copyright {
    .domain {
      color: #ff6600;
    }
  }
}
</style>