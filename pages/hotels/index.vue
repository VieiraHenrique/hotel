/* ****************** TEMPLATE ********************* */

<template>
  <div>
    <div class="hotels__banner">
      <img src="~/assets/img/hotels/hotel1.jpg" alt="hotel picture" />
      <img src="~/assets/img/hotels/hotel2.jpg" alt="hotel picture" />
      <img src="~/assets/img/hotels/hotel3.jpg" alt="hotel picture" />
    </div>
    <!-- <div class="hotels__title">
      <h2>Where are you gonna spend your next vacations ?</h2>
    </div> -->
    <section class="search-testimonials">
      <Search />
      <Testimonials />
    </section>
  </div>
</template>

/* ****************** SCRIPT ********************* */

<script>
import Search from '../../components/Search.vue'
import Testimonials from '../../components/Testimonials.vue'
export default {
  props: [],
  components: { Search, Testimonials },
  data() {
    return {}
  },
  methods: {},
}
</script>

/* ****************** STYLES ********************* */

<style lang="scss">
.hotels__banner {
  width: 100%;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;

  img {
    width: 100%;
    object-fit: cover;
  }
}

.search-testimonials {
  margin: 3rem;
  display: flex;
  gap: 3rem;
}
</style>
