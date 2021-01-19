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
                <input
                  type="number"
                  name="adults"
                  id="adults"
                  value="1"
                  min="1"
                  max="2"
                  v-model="adults"
                />
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
    <p class="error">{{ error2 }}</p>
    <p class="error">{{ error }}</p>

    <section class="hotels__grid">
      <Hotel-card
        v-for="hotel in hotels"
        :hotel="hotel"
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
import axios from 'axios';
import HotelCard from '../../components/HotelCard.vue';
import Search from '../../components/Search.vue';
import Testimonials from '../../components/Testimonials.vue';

/* Function to fetch a list of hotels from a provided place id */
const getHotels = async (placeID) => {
  const options = {
    method: 'GET',
    url: 'https://hotels4.p.rapidapi.com/properties/list',
    params: {
      destinationId: placeID,
      pageNumber: '1',
      checkIn: localStorage.checkIn,
      checkOut: localStorage.checkOut,
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
  };

  try {
    const res = await axios.request(options);
    return res.data.data.body.searchResults.results;
  } catch (err) {}
};

/* Default export from the component */
export default {
  components: { Search, Testimonials, HotelCard },
  data() {
    return {
      hotels: '',
      inpPlace: '',
      checkIn: '',
      checkOut: '',
      adults: 1,
      searchResults: '',
      error: '',
      error2: '',
    };
  },
  /* Sync inputs with local storage variables */
  watch: {
    inpPlace(inpPlace) {
      localStorage.city = inpPlace;
    },
    checkIn(checkIn) {
      localStorage.checkIn = checkIn;
    },
    checkOut(checkOut) {
      localStorage.checkOut = checkOut;
    },
    adults(adults) {
      localStorage.adults = adults;
    },
  },
  /* Sync inputs with local storage variables when the page is loaded */
  mounted() {
    if (localStorage.city) {
      this.inpPlace = localStorage.city;
    }
    if (localStorage.checkIn) {
      this.checkIn = localStorage.checkIn;
    }
    if (localStorage.checkOut) {
      this.checkOut = localStorage.checkOut;
    }
    if (localStorage.adults) {
      this.adults = localStorage.adults;
    }
  },
  methods: {
    /* Method to fetch de placeID from the city the user provided  */
    getPlace: async function (myQuery) {
      const options = {
        method: 'GET',
        url: 'https://hotels4.p.rapidapi.com/locations/search',
        params: { query: myQuery, locale: 'en_US' },
        headers: {
          'x-rapidapi-key':
            '30f40ac386msh71348525a4a982ap195beajsnb3c226b235e2',
          'x-rapidapi-host': 'hotels4.p.rapidapi.com',
        },
      };
      try {
        const res = await axios.request(options);
        return res.data.suggestions[0].entities[0].destinationId;
      } catch (err) {
        this.error =
          'Error retrieving information. Make sure the city exists and is written in English';
      }
    },
    /* Function that handles the form submit. It checks to see if the values are there - send a message if they are not - and invoke the functions getPlace and getHotels*/
    searchHotels: async function (e) {
      e.preventDefault();

      this.hotels = '';
      this.error = '';
      this.error2 = '';
      if (!localStorage.city) {
        this.error2 = 'Please insert a city';
        return;
      }
      if (!localStorage.checkIn || !localStorage.checkOut) {
        this.error = 'Please insert a date for your query';
        return;
      }
      this.searchResults = 'Searching... Please wait';
      const place = await this.getPlace(localStorage.city);
      const hotels = await getHotels(place);
      this.searchResults = `Results for "${localStorage.city}":`;
      this.hotels = hotels;
    },
  },
};
</script>

/* ****************** STYLES ********************* */

<style lang="scss">
@import './hotels.scss';
</style>
