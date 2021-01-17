/* ****************** TEMPLATE ********************* */

<template>
  <nuxt-link :to="'/hotels/' + id" class="hotel-card">
    <div class="hotel-card-rating">
      {{ rate }}
    </div>
    <img :src="img" alt="hotel picture" />
    <div class="hotel-card-text">
      <h3>{{ name }}</h3>
      <h4>{{ city }} - {{ country }}</h4>

      <a href="#" class="btn">Explore</a>
    </div>
  </nuxt-link>
</template>

/* ****************** SCRIPT ********************* */

<script>
export default {
  props: ['name', 'country', 'rate', 'img', 'city', 'id'],
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
  position: relative;
  color: #444;

  box-shadow: 0 1px 2px rgba($color: #000000, $alpha: 0.3);

  img {
    width: 100%;
    height: 20rem;
    object-fit: cover;
    border-top-left-radius: 1rem;
    border-top-right-radius: 1rem;
  }

  .hotel-card-rating {
    position: absolute;
    background: #444;
    color: #fff;
    width: 5rem;
    height: 5rem;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    top: -1.5rem;
    left: -1rem;
  }

  .hotel-card-text {
    padding: 3rem;
    height: 20rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;

    h3 {
      font-size: 2rem;
      font-weight: 800;
    }

    h4 {
      color: #444;
    }
  }

  a {
    margin-top: auto;
    display: inline-block;
    padding: 1rem 2rem;
    background: #349af7;
    background: #c7c0ba;
    color: #fff;
    text-decoration: none;
    box-shadow: 0 1px 2px rgba($color: #000000, $alpha: 0.3);

    &:hover {
      background: #349af7;
    }
  }
}
</style>
