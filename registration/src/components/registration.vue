<template>
<div class="container">
    <div>
      <img v-if="width > 600" src="../assets/big_logo.jpg" alt="#" class="biglogo-img">
      <img v-else src="../assets/logo.jpg" alt="#" class="logo-img">
    </div>
    <div class="login-text">
      <h1>Авторизация</h1>
      <div v-if="width > 600">
        <div>
          <p>Логин</p>
          <input type="text">
        </div>
        <div>
          <p>Пароль</p>
          <div class="password">
            <input type="password" id="pass-desktop">
            <button v-on:click="changePassVis" id="password-desktop"
                    class="password-control"></button>
          </div>
        </div>
      </div>
      <div v-else class="mobile-login">
        <input type="text" placeholder="Логин">
        <div class="password">
          <input type="password" id="pass-mobile" placeholder="Пароль">
          <button v-on:click="changePassVis" id="password-mobile"
                  class="password-control"></button>
        </div>
      </div>
      <div>
        <input type="button" value="Войти" class="login-btn">
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

export default ({
  name: 'Login',
  data() {
    return {
      width: 0,
      hide: false,
    };
  },
  methods: {
    updateWidth() {
      this.width = window.innerWidth;
      this.changePassVis();
    },
    changePassVis() {
      this.hide = !this.hide;
      let pass: HTMLInputElement;
      let btn: HTMLButtonElement;
      if (this.width > 600) {
        pass = document.getElementById('pass-desktop') as HTMLInputElement;
        btn = document.getElementById('password-desktop') as HTMLButtonElement;
      } else {
        pass = document.getElementById('pass-mobile') as HTMLInputElement;
        btn = document.getElementById('password-mobile') as HTMLButtonElement;
      }
      if (this.hide) {
        pass.type = 'password';
        btn.style.background = 'url(https://snipp.ru/demo/495/view.svg) 0 0 no-repeat';
      } else {
        pass.type = 'text';
        btn.style.background = 'url(https://snipp.ru/demo/495/no-view.svg) 0 0 no-repeat';
      }
    },
  },
  created() {
    this.width = window.innerWidth;
    window.addEventListener('resize', this.updateWidth);
  },
  unmounted() {
    window.removeEventListener('resize', this.updateWidth);
  },
});
</script>

<style>
.logo-img {
  height: 150px;
  margin: 0 auto;
  display: block;
}
.biglogo-img {
  height: 300px;
  margin-right: 30px;
}
.container {
  width: 100%;
  margin: 0 auto;
  display: flex;
  justify-content: center;
}
@media (max-width: 600px) {
  .container {
    display: block;
  }
}
.login-btn {
  margin-top: 5px;
  padding: 7px 23px;
  border-radius: 15px;
  border-width: thin;
  font-size: 16px;
  color: white;
  cursor: pointer;
  background-color: rgb(14, 10, 243);
}
.login-text {
  display: flex;
  align-items: center;
  flex-direction: column;
}
.login-text p {
  font-family: SansSerif, sans-serif;
  margin-top: 5px;
  margin-bottom: 5px;
}
.login-text input[type="text"], input[type="password"] {
  border-radius: 5px;
  border-width: thin;
  font-size: medium;
  padding: 3px 7px;
}
.mobile-login input {
  margin-top: 5px;
  margin-bottom: 5px;
}
.password {
  text-align: center;
  position: relative;
}
.password-control {
  position: absolute;
  top: 3px;
  right: 6px;
  display: inline-block;
  width: 20px;
  height: 20px;
  background: url(https://snipp.ru/demo/495/view.svg) 0 0 no-repeat;
  border: 0;
}
@media (max-width: 600px) {
  .password-control {
    top: 8px;
  }
}
</style>
<!--<style scoped>
  .container{
    width: 100%;
    margin: 0 auto;
    display: flex;
    justify-content: center;
  }
  .logo{
    margin-right: 10px;
  }
  .biglogo-img{
    height: 280px;
  }
  .logo-img{
    display: none;
  }
  .registration_block{
    display: flex;
    align-items: center;
    flex-direction: column;
  }
  .title{
    margin-top: 0;
    margin-bottom: 10px;
  }
  .Enter-btn{
    background-color: green;
  }
  .save{
    display: flex;
    margin: 20px 0px 10px 0px;
  }
  .save-text{
    margin: 0 auto;
    margin-left: -1px;
  }
  .save input{
    cursor: pointer;
  }
  .Enter-btn{
    padding: 14px 26px;
    border-radius: 5px;
    font-size: 16px;
    color: white;
    cursor: pointer;
  }
  .input-mobil{
    display: none;
    flex-direction: column;
  }
  .input-block p{
      margin-bottom: 0px;
  }
  .input-block input{
    font-size: 20px;
    text-decoration: none;
    padding: 2px 1px;
    }
  @media (max-width:600px){
    .container{
      display: block;
    }
    .biglogo-img{
      display: none;
    }
    .logo-img{
      display: block;
      margin: 0 auto;
      height: 100px;
    }
    .input_desctop{
      display: none;
    }
    .input-mobil{
      display: flex;
    }
    .input-mobil input{
      margin-top: 10px;
    }
    .input-mobil input{
    font-size: 20px;
    text-decoration: none;
    padding: 2px 1px;
    }
  }
    @media (max-width:260px){
      .input-mobil input{
        width: 180px;
    }
    }
</style>-->
