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
        <nuxt-link to="/hotels"> Yes. Take me in! </nuxt-link>
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
}
</script>

/* ****************** STYLES ********************* */

<style lang="scss">
.login {
  background: #fff;
  width: 80rem;
  border-radius: 1rem;

  .login-cover {
    width: 100%;
    height: 20rem;
    object-fit: cover;
    border-top-left-radius: 1rem;
    border-top-right-radius: 1rem;
    box-shadow: 0 5px 10px rgba($color: #000000, $alpha: 0.2);
  }

  .login-text {
    text-align: center;
    min-height: 50rem;
    padding: 3rem;

    img {
      margin-top: 1rem;
      width: 17rem;
    }

    h2 {
      font-family: 'Satisfy', serif;
      font-size: 3.8rem;
    }

    p {
      margin-bottom: 1rem;
      color: #777;
    }

    .login-powered {
      margin: 0;
      margin-top: 1rem;
    }

    hr {
      width: 50%;
      margin: 2rem auto;
    }

    .login-user {
      width: 5rem;
      border-radius: 50%;
    }

    a {
      margin: 0.5rem;
      background: #349af7;
      color: #fff;
      text-decoration: none;
      padding: 1rem 2rem;
      display: inline-block;

      &:hover {
        background: #64aef3;
      }
    }

    .orange {
      background: #1e65a8;

      &:hover {
        background: #1f77ca;
      }
    }

    .normal-link {
      all: unset;
      margin-top: 3rem;
      color: #349af7;
      cursor: pointer;

      &:hover {
        background: transparent;
      }
    }
  }
}
</style>
