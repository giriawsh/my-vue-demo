<template>
  <div class="container">
    <div class="my-login-box">
      <h2>Login</h2>
      <form>
        <div class="user-box">
          <span v-show="userShow === true"/>
          <input type="text" name="" required="" @focus="userClick()">
          </input>
          <label>
            Username
          </label>
        </div>
        <div class="circle_process" v-if="circleShow === true">
          <div class="wrapper right">
            <div class="circle rightcircle"></div>
          </div>
        </div>
        <div class="pass-box">
          <span v-show="passShow === true" class="passSpan"/>
          <input type="password" name="" required="" @focus="passClick()">
          </input>
          <label>
            Password
          </label>
        </div>
        <a href="#">
          <span></span>
          <span></span>
          <span></span>
          <span></span>
          Submit
        </a>
      </form>
    </div>
  </div>
</template>
<script>
  export default {
    name: 'loginDemo',
    data() {
      return {
        userShow: false,
        passShow: false,
        circleShow: false,
        timer: '',
      }
    },
    methods: {
      userClick() {
        this.userShow = true;
      },
      passClick() {
        this.userShow = false;
        this.circleShow = true;
        this.timer = setInterval(this.showPath, 200);
      },
      showPath(){
        this.circleShow = false;
        this.passShow = true;
      }
    },
    beforeDestroy() {
      clearInterval(this.timer);
    }
  }
</script>
<style scoped>
  .circle_process {
    position: absolute;
    /*width: 199px;*/
    /*height: 200px;*/
    /*left: 250px;*/
    /*top: 50px;*/
  }

  .circle_process .wrapper {
    width: 50px;
    height: 200px;
    position: absolute;
    left: 300px;
    top: -28px;
    overflow: hidden;
  }

  .circle_process .right {
    right: 0;
  }

  .circle_process .circle {
    width: 70px;
    height: 70px;
    border: 20px solid transparent;
    border-radius: 50%;
    position: absolute;
    top: 0;
    transform: rotate(-135deg);
  }

  .circle_process .rightcircle {
    /*border-top:2px solid #03e9f4;*/
    /*border-right:20px solid #03e9f4;*/
    border-right: 20px transparent;
    border-bottom: 2px solid #03e9f4;
    /*background: linear-gradient(90deg, transparent, #03e9f4);*/
    right: 0;
    -webkit-animation: circle_right .5s linear infinite;
    /*animation-delay: 2s;*/
  }

  @-webkit-keyframes circle_right {
    0% {
      -webkit-transform: rotate(-135deg);
    }
    50%, 100% {
      -webkit-transform: rotate(0deg);
    }
  }

  .my-login-box {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 400px;
    padding: 40px;
    transform: translate(-50%, -50%);
    background: rgba(0, 0, 0, .5);
    box-sizing: border-box;
    box-shadow: 0 15px 25px rgba(0, 0, 0, .6);
    border-radius: 10px;
  }

  .my-login-box h2 {
    margin: 0 0 30px;
    padding: 0;
    color: #F5F5F5;
    text-align: center;
  }

  .my-login-box .user-box {
    position: relative;
  }

  .my-login-box .pass-box {
    position: relative;
  }

  .my-login-box .user-box input {
    width: 100%;
    padding: 10px 0;
    font-size: 16px;
    color: #F5F5F5;
    margin-bottom: 30px;
    border: none;
    /*border-bottom: 1px solid #fff;*/
    outline: none;
    background: transparent;
  }

  .my-login-box .pass-box input {
    width: 100%;
    padding: 10px 0;
    font-size: 16px;
    color: #F5F5F5;
    margin-bottom: 30px;
    border: none;
    /*border-bottom: 1px solid #fff;*/
    outline: none;
    background: transparent;
  }

  .my-login-box .user-box span {
    position: absolute;
    /*display: block;*/
  }

  .my-login-box .pass-box span {
    position: absolute;
    /*display: block;*/
  }

  .my-login-box .user-box span{
    top: 40px;
    left: -50%;
    width: 50%;
    height: 2px;
    background: linear-gradient(90deg, transparent, #03e9f4);
    animation: btn-animuser 2s cubic-bezier(0.215, 0.610, 0.355, 1.000) alternate forwards;
  }

  @keyframes btn-animuser {
    0% {
      left: -50%;
    }
    50%,
    100% {
      left: 50%;
    }
  }

  .my-login-box .pass-box span{
    top: 40px;
    left: -50%;
    width: 50%;
    height: 2px;
    background: linear-gradient(270deg, transparent, #03e9f4);
    animation: btn-animpass 2s cubic-bezier(0.215, 0.610, 0.355, 1.000) alternate forwards;
  }

  @keyframes btn-animpass {
    0% {
      left: 95%;
      width: 10%;
    }
    50%,
    100% {
      left: 0%;
    }
  }

  .my-login-box .user-box label {
    position: absolute;
    top: 0;
    left: 0;
    padding: 10px 0;
    font-size: 16px;
    color: #F5F5F5;
    pointer-events: none;
    transition: .5s;
  }

  .my-login-box .user-box input:focus ~ label,
  .my-login-box .user-box input:valid ~ label {
    top: -30px;
    left: 0;
    color: rgba(100, 200, 255, 0.7);
    font-size: 12px;
  }

  .my-login-box .pass-box label {
    position: absolute;
    top: 0;
    left: 0;
    padding: 10px 0;
    font-size: 16px;
    color: #F5F5F5;
    pointer-events: none;
    transition: .5s;
  }

  .my-login-box .pass-box input:focus ~ label,
  .my-login-box .pass-box input:valid ~ label {
    top: -30px;
    left: 0;
    color: rgba(100, 200, 255, 0.7);
    font-size: 12px;
  }


  .my-login-box form a {
    position: relative;
    display: inline-block;
    padding: 10px 20px;
    color: #03e9f4;
    font-size: 16px;
    text-decoration: none; /*取消下划线*/
    text-transform: uppercase;
    overflow: hidden;
    transition: .3s;
    margin-top: 40px;
    letter-spacing: 4px;
  }

  .my-login-box a:hover {
    background: #03e9f4;
    color: #F5F5F5;
    border-radius: 5px;
    box-shadow: 0 0 5px #03e9f4, 0 0 25px #03e9f4, 0 0 30px #03e9f4, 0 0 30px #03e9f4;
  }

  .my-login-box a span {
    position: absolute;
    display: block;
  }

  .my-login-box a span:nth-child(1) {
    top: 0;
    left: -100%;
    width: 100%;
    height: 2px;
    background: linear-gradient(90deg, transparent, #03e9f4);
    animation: btn-anim1 1s linear infinite;
  }

  @keyframes btn-anim1 {
    0% {
      left: -90%;
    }
    50%,
    100% {
      left: 90%;
    }
  }

  .my-login-box a span:nth-child(2) {
    top: -100%;
    right: 0;
    width: 2px;
    height: 100%;
    background: linear-gradient(180deg, transparent, #03e9f4);
    animation: btn-anim2 1s linear infinite;
    animation-delay: .25s
  }

  @keyframes btn-anim2 {
    0% {
      top: -100%;
    }
    50%,
    100% {
      top: 100%;
    }
  }

  .my-login-box a span:nth-child(3) {
    bottom: 0;
    right: -100%;
    width: 100%;
    height: 2px;
    background: linear-gradient(270deg, transparent, #03e9f4);
    animation: btn-anim3 1s linear infinite;
    animation-delay: .5s
  }

  @keyframes btn-anim3 {
    0% {
      right: -100%;
    }
    50%,
    100% {
      right: 100%;
    }
  }

  .my-login-box a span:nth-child(4) {
    bottom: -100%;
    left: 0;
    width: 2px;
    height: 100%;
    background: linear-gradient(360deg, transparent, #03e9f4);
    animation: btn-anim4 1s linear infinite;
    animation-delay: .75s
  }

  @keyframes btn-anim4 {
    0% {
      bottom: -100%;
    }
    50%,
    100% {
      bottom: 100%;
    }
  }

  .container {
    margin: 0;
    padding: 0;
    font-family: sans-serif;
    justify-content: center;
    align-items: center;
    /*background: linear-gradient(#141e30, #243b55);*/
    background: radial-gradient(ellipse at bottom, #1b2735 0%, #141e30 100%);
    color: rgba(100, 200, 255, 0.7);
    height: 100vh;
    overflow: hidden;
    width: 150vm !important;
    max-width: none;
  }

</style>
