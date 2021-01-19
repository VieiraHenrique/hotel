/* ****************** TEMPLATE ********************* */

<template>
  <div class="header">
    <div class="header__logo">
      <nuxt-link to="/"
        ><img src="~/assets/img/logo.png" alt="logo"
      /></nuxt-link>
    </div>
    <div class="header__title">
      <h1>Easy booking</h1>
    </div>
    <div class="header__nav">
      <div class="header__nav--bookmark">
        <img src="~/assets/img/fontawesome/bookmark-gray.png" alt="bookmark" />
      </div>
      <div class="header__nav--notifications">
        <img src="~/assets/img/fontawesome/comments-gray.png" alt="comments" />
      </div>
      <div class="header__nav--user">
        <img src="~/assets/img/henrique.jpg" alt="user-image" />
        <span>Henrique</span>
      </div>
    </div>
  </div>
</template>

/* ****************** SCRIPT ********************* */

<script>
export default {
  props: [],
  components: {},
  data() {
    return {};
  },
  methods: {},
};
</script>

/* ****************** STYLES ********************* */

<style lang="scss">
@import './Header.scss';
</style>
