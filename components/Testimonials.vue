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
    return {}
  },
  methods: {},
}
</script>

/* ****************** STYLES ********************* */

<style lang="scss">
.testimonials {
  background: #fff;
  box-shadow: 0 1px 2px rgba($color: #000000, $alpha: 0.3);
  padding: 3rem;
  border-radius: 1rem;
  width: 100%;
  height: 32rem;
  position: relative;

  .quote {
    position: absolute;
    top: -1rem;
    left: -1rem;
    width: 4rem;
  }

  p {
    color: #777;
    font-style: italic;
  }

  .author {
    margin-top: 2rem;
    text-align: right;
    font-size: 1.3rem;
    color: #000;
  }

  .userPic {
    border-radius: 50%;
    width: 3rem;
  }
}
</style>
