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

      <div class="hotel-card-price-explore">
        <!-- <p>{{ hotel.ratePlan.price.current }}</p> -->
        <a href="#" class="btn">Explore</a>
      </div>
    </div>
  </nuxt-link>
</template>

/* ****************** SCRIPT ********************* */

<script>
export default {
  props: ['name', 'country', 'rate', 'img', 'city', 'id', 'hotel'],
  data() {
    return {};
  },
  mounted() {},
};
</script>

/* ****************** STYLES ********************* */

<style lang="scss">
@import './HotelCard.scss';
</style>
