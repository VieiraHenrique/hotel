/* ****************** TEMPLATE ********************* */

<template>
  <div>
    <div class="hotels__banner">
      <img src="~/assets/img/hotels/hotel1.jpg" alt="hotel picture" />
      <img src="~/assets/img/hotels/hotel2.jpg" alt="hotel picture" />
      <img src="~/assets/img/hotels/hotel3.jpg" alt="hotel picture" />
    </div>
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

    <p class="results">Results:</p>

    <section class="hotels__grid">
      <!-- FOR LOOP on the hotels response -->
      <Hotel-card
        v-for="hotel in hotels"
        :name="hotel.name"
        :key="hotel.destinationId"
        :id="hotel.destinationId"
      />
    </section>
  </div>
</template>

/* ****************** SCRIPT ********************* */

<script>
import axios from 'axios'
import HotelCard from '../../components/HotelCard.vue'
import Search from '../../components/Search.vue'
import Testimonials from '../../components/Testimonials.vue'

// Define options for Axios request
const options = {
  method: 'GET',
  url: 'https://hotels4.p.rapidapi.com/locations/search',
  params: { query: 'recife', locale: 'en_US' },
  headers: {
    'x-rapidapi-key': '30f40ac386msh71348525a4a982ap195beajsnb3c226b235e2',
    'x-rapidapi-host': 'hotels4.p.rapidapi.com',
  },
}

export default {
  components: { Search, Testimonials, HotelCard },
  data() {
    return {
      // Declare variable "hotels"
      hotels: '',
    }
  },

  // Call API on load and save hotels array to the variable "hotels"
  mounted() {
    axios.request(options).then((res) => {
      this.hotels = res.data.suggestions[1].entities
    })
  },
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

.results {
  margin-left: 3rem;
}

.hotels__grid {
  margin: 3rem;
  margin-bottom: 10rem;
  display: grid;
  gap: 3rem;
  grid-template-columns: 1fr 1fr 1fr;
}
</style>
