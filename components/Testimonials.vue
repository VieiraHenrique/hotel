/* ****************** TEMPLATE ********************* */

<template>
  <div class="testimonials">
    <img src="~/assets/img/fontawesome/quote.png" alt="quote" class="quote" />
    <p>
      {{ msg }}
    </p>

    <p class="author">
      <img :src="img" alt="user" class="userPic" /> <br />
      {{ author }} <br />
      {{ date }}
    </p>
  </div>
</template>

/* ****************** SCRIPT ********************* */

<script>
export default {
  props: ['author', 'img', 'date', 'msg'],
  components: {},
  data() {
    return {};
  },
  methods: {},
};
</script>

/* ****************** STYLES ********************* */

<style lang="scss">
@import './Testimonials.scss';
</style>
