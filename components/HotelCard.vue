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
import axios from 'axios'

export default {
  props: ['name', 'id'],
  data() {
    return {
      img: '',
      title: '',
      location: '',
    }
  },
  mounted() {
    const options = {
      method: 'GET',
      url: 'https://hotels4.p.rapidapi.com/properties/get-hotel-photos',
      params: { id: this.id },
      headers: {
        'x-rapidapi-key': '30f40ac386msh71348525a4a982ap195beajsnb3c226b235e2',
        'x-rapidapi-host': 'hotels4.p.rapidapi.com',
      },
    }
    axios.request(options).then((res) => {
      console.log(res.data.hotelImages[0])
      let str = res.data.hotelImages[0].baseUrl
      str = str.slice(0, str.length - 11) + '.jpg'
      this.img = str
    })
  },
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
