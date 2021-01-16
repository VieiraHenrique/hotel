/* ****************** TEMPLATE ********************* */

<template>
  <div class="hotel-card">
    <img :src="img" alt="hotel picture" />
    <div class="hotel-card-text">
      <h3>{{ name }}</h3>
      <h4>{{ location }}</h4>
      <a href="#" class="btn">Explore</a>
    </div>
  </div>
</template>

/* ****************** SCRIPT ********************* */

<script>
export default {
  props: ['name', 'location', 'rate', 'img'],
  data() {
    return {}
  },
  mounted() {},
}
</script>

/* ****************** STYLES ********************* */

<style lang="scss">
.hotel-card {
  border-radius: 1rem;
  background: #fff;

  color: #444;

  box-shadow: 0 1px 2px rgba($color: #000000, $alpha: 0.3);

  img {
    width: 100%;
    height: 20rem;
    object-fit: cover;
    border-top-left-radius: 1rem;
    border-top-right-radius: 1rem;
  }

  .hotel-card-text {
    padding: 3rem;
  }

  a {
    margin-top: 2rem;
    display: inline-block;
    padding: 1rem 2rem;
    background: #349af7;
    color: #fff;
    text-decoration: none;

    &:hover {
      background: #6eb1f0;
    }
  }
}
</style>
