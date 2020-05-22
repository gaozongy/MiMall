<template>
  <div class="login">
    <div class="container">
      <a href="/#/index">
        <img
          src="https://account.xiaomi.com/static/res/7f6f2f5/account-static/respassport/acc-2014/img/mistore_logo.png"
          alt
        />
      </a>
    </div>
    <div class="wrapper">
      <div class="container">
        <div class="login-form">
          <h3>
            <span class="checked">账号登录</span>
            <span class="sep-line">|</span>
            <span>扫码登录</span>
          </h3>
          <div class="input">
            <input type="text" placeholder="请输入账号" v-model="username" />
          </div>
          <div class="input">
            <input type="password" placeholder="请输入密码" v-model="password" />
          </div>
          <div class="btn-box">
            <a href="javascript:;" class="btn" @click="login">登录</a>
          </div>
          <div class="tips">
            <div class="sms" @click="register">手机短信登录/注册</div>
            <div class="reg">
              立即注册
              <span>|</span>忘记密码？
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="footer">
      <div class="footer-link">
        <a href>简体</a>
        <span>|</span>
        <a href>繁体</a>
        <span>|</span>
        <a href>English</a>
        <span>|</span>
        <a href>常见问题</a>
        <span>|</span>
        <a href>隐私政策</a>
      </div>
      <p class="copyright">Copyright ©2019 mi.futurefe.com All Rights Reserved.</p>
    </div>
  </div>
</template>

<script>
import { Message } from "element-ui";
import "element-ui/lib/theme-chalk/index.css";
export default {
  name: "login",
  data() {
    return {
      username: "",
      password: "",
      userId: ""
    };
  },
  methods: {
    login() {
      let { username, password } = this;
      this.axios
        .post("/user/login", {
          username,
          password
        })
        .then(res => {
          this.$cookie.set("userId", res.id, { expires: "Session" });
          this.$store.dispatch("saveUserName", res.username);
          this.$router.push({
            name: "index",
            params: {
              from: "login"
            }
          });
        });
    },
    register() {
      this.axios
        .post("/user/register", {
          username: "admin1",
          password: "admin1",
          email: "admin@163.com"
        })
        .then(() => {
          Message.success("注册成功");
        });
    }
  }
};
</script>

<style lang="scss">
.login {
  & > .container {
    height: 98px;
    img {
      width: auto;
      height: 100%;
    }
  }
  .wrapper {
    background: url("https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/7f25f8c94bac0a8bfb3c6a3e30e5b7dd.jpg")
      no-repeat center;
    .container {
      height: 588px;
      position: relative;
      vertical-align: middle;
      .login-form {
        box-sizing: border-box;
        padding-left: 30px;
        padding-right: 30px;
        width: 410px;
        height: 510px;
        background-color: #ffffff;
        position: absolute;
        right: 0;
        top: 50%;
        transform: translate(0, -50%);
        h3 {
          line-height: 22px;
          font-size: 24px;
          text-align: center;
          margin: 40px auto 50px;
          .checked {
            color: #ff6600;
          }
          .sep-line {
            margin: 0 32px;
          }
        }
        .input {
          display: inline-block;
          width: 350px;
          height: 50px;
          border: 1px solid #e5e5e5;
          margin-bottom: 20px;
          input {
            width: 100%;
            height: 100%;
            border: none;
            padding: 18px;
          }
        }
        .btn {
          width: 100%;
          line-height: 50px;
          margin-top: 10px;
          font-size: 16px;
        }
        .tips {
          margin-top: 14px;
          display: flex;
          justify-content: space-between;
          font-size: 14px;
          cursor: pointer;
          .sms {
            color: #ff6600;
          }
          .reg {
            color: #999999;
            span {
              margin: 0 6px;
            }
          }
        }
      }
    }
  }
  .footer {
    height: 100px;
    padding-top: 100px;
    color: #999999;
    font-size: 14px;
    text-align: center;
    .footer-link {
      a {
        color: #999999;
        display: inline-block;
      }
      span {
        margin: 0 12px;
      }
    }
    .copyright {
      margin-top: 12px;
    }
  }
}
</style>