/* ****************** TEMPLATE ********************* */

<template>
  <div class="specific-wrapper">
    <nuxt-link to="/hotels" class="btn">Get back to main page</nuxt-link>

    <div class="specific-row">
      <div class="specific-hotel">
        <h2>{{ hotel.propertyDescription.name }}</h2>
        <h4>
          {{ hotel.propertyDescription.address.cityName }} -
          {{ hotel.propertyDescription.address.countryName }}
        </h4>

        <img
          src="~/assets/img/fontawesome/star.png"
          alt="star"
          class="stars"
          v-for="(n, i) in hotel.propertyDescription.starRating"
        />

        <ul class="nobullet">
          <li>{{ hotel.propertyDescription.freebies[0] }}</li>
        </ul>
        <br />
        <ul v-for="amen in hotel.amenities[0].listItems[0].listItems">
          <li>{{ amen }}</li>
        </ul>
        <ul v-for="amen in hotel.amenities[0].listItems[1].listItems">
          <li>{{ amen }}</li>
        </ul>
        <!-- <ul v-for="amen in hotel.amenities[0].listItems[2].listItems">
          <li>{{ amen }}</li>
        </ul> -->
      </div>
      <div class="specific-price">
        <h2>
          <span>
            {{ hotel.propertyDescription.featuredPrice.currentPrice.formatted }}
          </span>
          per night
        </h2>
      </div>
    </div>

    <div class="specific-pictures">
      <!-- <h2>{{ loadingPic }}</h2> -->
      <!-- <img v-for="pic in correctPics" :src="pic" alt="picture" /> -->
      <a v-for="(n, i) in 8" :href="correctPics[i]" target="blank">
        <img :src="correctPics[i]" alt="picture" />
      </a>
    </div>
  </div>
</template>

/* ****************** SCRIPT ********************* */

<script>
import axios from 'axios'

const getOneHotel = async (myID) => {
  const options = {
    method: 'GET',
    url: 'https://hotels4.p.rapidapi.com/properties/get-details',
    params: {
      id: myID,
      locale: 'en_US',
      currency: 'EUR',
      checkOut: '2020-01-15',
      adults1: '1',
      checkIn: '2020-01-08',
    },
    headers: {
      'x-rapidapi-key': '30f40ac386msh71348525a4a982ap195beajsnb3c226b235e2',
      'x-rapidapi-host': 'hotels4.p.rapidapi.com',
    },
  }
  const res = await axios.request(options)
  return res.data.data.body
}

const getPics = async (myID) => {
  const options = {
    method: 'GET',
    url: 'https://hotels4.p.rapidapi.com/properties/get-hotel-photos',
    params: { id: myID },
    headers: {
      'x-rapidapi-key': '30f40ac386msh71348525a4a982ap195beajsnb3c226b235e2',
      'x-rapidapi-host': 'hotels4.p.rapidapi.com',
    },
  }
  const res = await axios.request(options)
  return res.data.hotelImages
}

export default {
  props: [],
  components: {},
  data() {
    return {
      loadingPic: 'Loading pictures...',
    }
  },
  async asyncData(context) {
    const hotel = await getOneHotel(context.params.id)
    const pics = await getPics(context.params.id)
    const correctPics = pics.map((elem) => {
      let str = elem.baseUrl
      str = str.slice(0, str.length - 11) + '.jpg'
      return str
    })
    return { hotel, correctPics }
  },
  methods: {},
}
</script>

/* ****************** STYLES ********************* */

<style lang="scss">
.specific-wrapper {
  margin: 3rem;

  .btn {
    background: #349af7;
    color: #fff;
    padding: 1rem 2rem;
    text-decoration: none;
    display: inline-block;
    cursor: pointer;

    &:hover {
      background: #5bb0ff;
    }
  }

  .specific-hotel {
    background: #fff;
    margin: 3rem 0;
    padding: 3rem;
    width: 50rem;
    box-shadow: 0 1px 2px rgba($color: #000000, $alpha: 0.3);

    h2 {
      margin-bottom: 0.5rem;
      font-weight: 800;
    }
    h4 {
      margin-bottom: 1rem;
    }

    .stars {
      width: 3rem;
      margin-bottom: 2rem;
    }

    .nobullet {
      list-style: none;
      li {
        color: #000;
      }
    }

    ul {
      list-style-type: bullet;

      li {
        margin-bottom: 0.5rem;
        color: #aaa;
      }
    }
  }

  .specific-pictures {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 3rem;
    margin-bottom: 6rem;

    img {
      width: 100%;
      height: 25rem;
      object-fit: cover;
      cursor: pointer;
    }
  }

  .specific-row {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    gap: 3rem;
  }

  .specific-price {
    background: #fff;
    margin: 3rem 0;
    padding: 3rem;
    width: 50%;
    box-shadow: 0 1px 2px rgba($color: #000000, $alpha: 0.3);

    h2 {
      font-size: 2rem;

      span {
        background: red;
        color: #fff;
        padding: 1rem 2rem;
        margin-right: 1rem;
      }
    }
  }
}
</style>
