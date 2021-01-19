/* ****************** TEMPLATE ********************* */

<template>
  <div class="login">
    <img class="login-cover" src="~/assets/img/beach.jpg" alt="login cover" />
    <div class="login-text">
      <h2>- Easy booking -</h2>
      <p class="login-powered">Powered By</p>
      <img src="~/assets/img/logoBlack.png" alt="" />
      <hr />
      <h2>Login</h2>
      <img src="~/assets/img/henrique.jpg" alt="henrique" class="login-user" />
      <p>Continue as Henrique ?</p>

      <div class="login-btns">
        <nuxt-link to="/hotels"> Yes. Take me in ! </nuxt-link>
        <nuxt-link to="#" class="orange"> I am not Henrique</nuxt-link>
      </div>
      <br />
      <p>Not registered yet ? <a href="#" class="normal-link">Register !</a></p>
    </div>
  </div>
</template>

/* ****************** SCRIPT ********************* */

<script>
export default {
  layout: 'login',
};
</script>

/* ****************** STYLES ********************* */

<style lang="scss">
@import './login.scss';
</style>
