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
      <Testimonials
        author="Billy James"
        date="dec 2020"
        img="https://randomuser.me/api/portraits/men/97.jpg"
        msg="Lorem ipsum dolor sit amet consectetur adipisicing elit. Labore ratione soluta porro consectetur excepturi."
      />
      <Testimonials
        author="Pamela Scott"
        date="jan 2021"
        img="https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-0.3.5&q=80&fm=jpg&crop=faces&fit=crop&h=200&w=200&s=046c29138c1335ef8edee7daf521ba50"
        msg="Lorem ipsum dolor sit amet consectetur, adipisicing elit. Distinctio temporibus eligendi veritatis vitae, repellendus eos."
      />
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
  align-items: flex-start;
  gap: 3rem;
}
</style>
