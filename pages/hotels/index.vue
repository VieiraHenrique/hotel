/* ****************** TEMPLATE ********************* */

<template>
  <div>
    <div class="hotels__banner">
      <img src="~/assets/img/hotels/hotel1.jpg" alt="hotel picture" />
      <img src="~/assets/img/hotels/hotel2.jpg" alt="hotel picture" />
      <img src="~/assets/img/hotels/hotel3.jpg" alt="hotel picture" />
    </div>
    <section class="search-testimonials">
      <div class="hotels__search">
        <h2>Search for hotels</h2>
        <p>
          Our search engine powered by Artificial Intelligence gives you the
          right choice every time !
        </p>
        <form @submit="searchHotels">
          <div class="form__layout">
            <div class="form__col-left">
              <p>
                <label for="city">City</label>
                <br />
                <input
                  v-model="inpPlace"
                  type="text"
                  name="city"
                  id="city"
                  placeholder="Enter a city"
                />
              </p>
              <p>
                Number of adults
                <br />
                <input type="number" name="adults" id="adults" value="1" />
              </p>
            </div>
            <div class="form__col-right">
              <p>
                From
                <br />
                <input
                  type="date"
                  name="checkIn"
                  id="checkIn"
                  v-model="checkIn"
                />
              </p>
              <p>
                To
                <br />
                <input
                  type="date"
                  name="checkOut"
                  id="checkOut"
                  v-model="checkOut"
                />
              </p>
            </div>
          </div>
          <button>Let's go !</button>
        </form>
      </div>

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

    <p class="results">{{ searchResults }}</p>

    <section class="hotels__grid">
      <Hotel-card
        v-for="hotel in hotels"
        :name="hotel.name"
        :country="hotel.address.countryName"
        :city="hotel.address.locality"
        :rate="hotel.guestReviews.rating"
        :img="hotel.thumbnailUrl"
        :key="hotel.id"
        :id="hotel.id"
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

const getPlace = async (myQuery) => {
  const options = {
    method: 'GET',
    url: 'https://hotels4.p.rapidapi.com/locations/search',
    params: { query: myQuery, locale: 'en_US' },
    headers: {
      'x-rapidapi-key': '30f40ac386msh71348525a4a982ap195beajsnb3c226b235e2',
      'x-rapidapi-host': 'hotels4.p.rapidapi.com',
    },
  }
  const res = await axios.request(options)
  return res.data.suggestions[0].entities[0].destinationId
}

const getHotels = async (placeID) => {
  const options = {
    method: 'GET',
    url: 'https://hotels4.p.rapidapi.com/properties/list',
    params: {
      destinationId: placeID,
      pageNumber: '1',
      checkIn: '2020-01-08',
      checkOut: '2020-01-15',
      pageSize: '9',
      adults1: '1',
      currency: 'EUR',
      locale: 'en_US',
      sortOrder: 'STAR_RATING_HIGHEST_FIRST',
    },
    headers: {
      'x-rapidapi-key': '30f40ac386msh71348525a4a982ap195beajsnb3c226b235e2',
      'x-rapidapi-host': 'hotels4.p.rapidapi.com',
    },
  }
  const res = await axios.request(options)
  return res.data.data.body.searchResults.results
}

export default {
  components: { Search, Testimonials, HotelCard },
  data() {
    return {
      hotels: '',
      inpPlace: '',
      checkIn: '',
      checkOut: '',
      searchResults: '',
    }
  },

  methods: {
    searchHotels: async function (e) {
      e.preventDefault()
      this.hotels = ''
      this.searchResults = 'Searching... Please wait'
      const place = await getPlace(this.inpPlace)
      const hotels = await getHotels(place)
      this.searchResults = 'Results:'
      this.hotels = hotels
    },
  },

  asyncData() {},
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
  font-weight: 400;
  font-size: 1.7rem;
  text-align: center;
}

.hotels__grid {
  margin: 3rem;
  margin-bottom: 10rem;
  display: grid;
  gap: 3rem;
  grid-template-columns: 1fr 1fr 1fr;
}
</style>
