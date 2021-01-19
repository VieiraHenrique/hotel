/* TEMPLATE */ /*
******************************************************************* */ /*
******************************************************************* */ /*
******************************************************************* */ /*
******************************************************************* */ /*
******************************************************************* */ /*
******************************************************************* */
<template>
  <div>
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
        </div>
        <div class="specific-price">
          <h2>
            <span>
              {{
                hotel.propertyDescription.featuredPrice.currentPrice.formatted
              }}
            </span>
            per night
          </h2>
          <p>
            From: <span> {{ checkIn }} </span> to: <span> {{ checkOut }} </span>
          </p>
          <p>
            Total nights : <span>{{ totalDays }}</span>
          </p>
          <p>
            Total price : <span>{{ totalPrice }} € </span
            ><span class="vat">VAT included</span>
          </p>
          <p class="book" @click="toggleModal = !toggleModal">Book now</p>
        </div>
      </div>

      <!-- ************** IMAGE GALLERY ***************** -->

      <div class="specific-pictures">
        <a
          v-for="(n, i) in 8"
          :href="correctPics[i]"
          :key="correctPics[i]"
          target="blank"
        >
          <img :src="correctPics[i]" alt="picture" />
        </a>
      </div>
    </div>

    <!-- ****************MODAL******************** -->

    <div v-if="toggleModal" class="modalBG">
      <div class="modal">
        <div class="modal-first" v-if="modalFirst">
          <div class="modal-title">
            <h2>Great, Henrique ! Let's wrap it up !</h2>
            <p>
              Confirm the below information. <br />
              If you are booking for someone else, insert his/her name and
              email.
            </p>
          </div>

          <div class="modal-row">
            <div class="modal-payment">
              <label for="name">Name of the guest</label>
              <input
                v-model="guestName"
                type="text"
                id="name"
                value="Henrique Vieira"
              />
              <label for="name">Email of the guest</label>
              <input
                v-model="guestMail"
                type="text"
                id="name"
                value="me@henriquevieira.com"
              />
              <label for="name">Special request</label>
              <input v-model="comments" type="text" id="name" />
            </div>

            <div class="modal-recap">
              <p>
                From: <br />
                <span> {{ checkIn }} </span> <br />
                to: <br />
                <span> {{ checkOut }} </span>
              </p>
              <p>
                Total nights : <span>{{ totalDays }}</span>
              </p>
              <p class="totalPrice">
                Total price : <span class="totalPrice">{{ totalPrice }} € </span
                ><span class="vat">VAT included</span>
              </p>
            </div>
          </div>

          <a href="#" class="btn" @click="toggleModal = !toggleModal">Cancel</a>
          <a href="#" class="btn red" @click="handleProceed">Proceed</a>
        </div>
        <div class="modal-second" v-if="modalSecond">
          <h2>Your order has been completed</h2>
          <p>An email has been sent to {{ guestMail }} with all the details</p>
          <nuxt-link class="btn red" to="/hotels"
            >Get back to main page</nuxt-link
          >
        </div>
      </div>
    </div>
  </div>
</template>

/* SCRIPT */ /*
******************************************************************* */ /*
******************************************************************* */ /*
******************************************************************* */ /*
******************************************************************* */ /*
******************************************************************* */ /*
******************************************************************* */

<script>
import axios from 'axios';

/* Function to fetch the details of one hot. Must provide the hotel ID as argument. Returns data.body from the api */
const getOneHotel = async (myID) => {
  const options = {
    method: 'GET',
    url: 'https://hotels4.p.rapidapi.com/properties/get-details',
    params: {
      id: myID,
      locale: 'en_US',
      currency: 'EUR',
      checkOut: localStorage.checkOut,
      adults1: localStorage.adults,
      checkIn: localStorage.checkIn,
    },
    headers: {
      'x-rapidapi-key': '30f40ac386msh71348525a4a982ap195beajsnb3c226b235e2',
      'x-rapidapi-host': 'hotels4.p.rapidapi.com',
    },
  };
  const res = await axios.request(options);
  return res.data.data.body;
};

/* Function to get the pictures from a specific hotel. Must provide the hotel ID as argument. Returns data.hotelImages from the api (the main array of urls) */
const getPics = async (myID) => {
  const options = {
    method: 'GET',
    url: 'https://hotels4.p.rapidapi.com/properties/get-hotel-photos',
    params: { id: myID },
    headers: {
      'x-rapidapi-key': '30f40ac386msh71348525a4a982ap195beajsnb3c226b235e2',
      'x-rapidapi-host': 'hotels4.p.rapidapi.com',
    },
  };
  const res = await axios.request(options);
  return res.data.hotelImages;
};

/* Function to get how many days there are between the two inputs. 'first' and 'second' are dates in a string with the format YYYY-MM-DD */

function datediff(first, second) {
  /* Transform the strings in an actual Date object */
  let a = new Date(first);
  let b = new Date(second);

  /* Converts dates to milliseconds */
  a = a.getTime();
  b = b.getTime();

  /* Calcultates de differente in milliseconds and divide by the quantity of millisenconds in a day */
  let days = Math.round((b - a) / (1000 * 60 * 60 * 24));

  return days;
}

export default {
  props: [],
  components: {},
  data() {
    return {
      /* Message from */
      loadingPic: 'Loading pictures...',
      checkIn: localStorage.checkIn,
      checkOut: localStorage.checkOut,
      totalDays: datediff(localStorage.checkIn, localStorage.checkOut),
      adults: localStorage.adults,
      totalPrice: localStorage.totalPrice,
      toggleModal: false,
      modalFirst: true,
      modalSecond: false,
      guestName: 'Henrique Vieira',
      guestMail: 'me@henriquevieira.com',
      comments: '',
    };
  },
  async asyncData(context) {
    const hotel = await getOneHotel(context.params.id);
    localStorage.hotelID = context.params.id;
    console.log(hotel);
    localStorage.days = datediff(localStorage.checkIn, localStorage.checkOut);
    localStorage.price =
      hotel.propertyDescription.featuredPrice.currentPrice.plain;
    localStorage.totalPrice = localStorage.days * localStorage.price;
    const pics = await getPics(context.params.id);
    const correctPics = pics.map((elem) => {
      let str = elem.baseUrl;
      str = str.slice(0, str.length - 11) + '.jpg';
      return str;
    });
    return { hotel, correctPics };
  },
  methods: {
    handleProceed() {
      const options = {
        method: 'post',
        url:
          'https://7ti5e2qscg.execute-api.us-east-1.amazonaws.com/production/',
        data: {
          hotel_name: this.hotel.propertyDescription.name,
          hotel_id: localStorage.hotelID,
          room_type: 'Standard Room',
          persons: localStorage.adults,
          booking_date_from: localStorage.checkIn,
          booking_date_until: localStorage.checkOut,
          comments: this.comments,
          customer_name: this.guestName,
          customer_email: this.guestMail,
        },
      };

      axios(options);

      this.modalFirst = false;
      this.modalSecond = true;
    },
  },
};
</script>

/* STYLE */ /*
******************************************************************* */ /*
******************************************************************* */ /*
******************************************************************* */ /*
******************************************************************* */ /*
******************************************************************* */ /*
******************************************************************* */

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
        margin-left: 0;
      }
    }

    ul {
      list-style-type: bullet;

      li {
        margin-left: 3rem;
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
    margin-bottom: 10rem;

    img {
      width: 100%;
      height: 25rem;
      object-fit: cover;
      cursor: pointer;
      box-shadow: 0 1px 2px rgba($color: #000000, $alpha: 0.3);
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
      font-size: 1.6rem;

      span {
        background: #349af7;
        color: #fff;
        padding: 1rem 2rem;
        margin-right: 0.5rem;
        display: inline-block;
        font-size: 2rem;
      }
    }

    p {
      margin-top: 1rem;
      color: #666;

      span {
        font-size: 1.8rem;
        color: #000;
      }

      .vat {
        font-size: 1.4rem;
      }
    }
    .book {
      background: rgb(214, 39, 39);
      color: #fff;
      padding: 2rem 2rem;
      cursor: pointer;
      text-align: center;
      margin-top: 2rem;
    }
  }
}

.modalBG {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba($color: #000000, $alpha: 0.7);
  display: flex;
  justify-content: center;
  align-items: center;

  .modal {
    background: #f4f2f2;
    box-shadow: 0 2px 4px rgba($color: #000000, $alpha: 0.7);
    padding: 5rem;
    width: 70rem;
    border-radius: 0.5rem;

    img {
      width: 7rem;
    }

    .btn {
      background: #c7c0ba;
      color: #fff;
      padding: 1rem 2rem;
      text-decoration: none;
      display: inline-block;
      margin-top: 3rem;
    }

    .red {
      background: #349af7;
    }

    p {
      margin: 2rem 0;
    }

    .modal-row {
      display: flex;
      justify-content: space-between;
      align-items: stretch;
    }

    .rounded {
      width: 5rem;
      border-radius: 50%;
    }

    .paypal-pictures {
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: -2rem;
    }

    .totalPrice {
      font-weight: 800;
    }

    .vat {
      font-size: 1.3rem;
    }

    .modal-payment {
      flex: 1 0 50%;
      padding: 3rem;
      background: #fff;
      box-shadow: 0 1px 2px rgba($color: #000000, $alpha: 0.3);

      label {
        display: inline-block;
        margin-top: 1rem;
        font-size: 1.4rem;
        color: #666;
      }

      input {
        margin-top: 0.5rem;
        background: #f4f2f2;
        width: 100%;
        border-radius: 10rem;
        padding: 1rem;
        border: 1px solid #ccc;
        font-size: 1.6rem;

        &:focus {
          outline: none;
        }
      }
    }

    .modal-recap {
      padding: 3rem;
      background: #fff;
      box-shadow: 0 1px 2px rgba($color: #000000, $alpha: 0.3);

      span {
        font-size: 1.4rem;
        font-weight: 800;
      }
    }
  }
}
</style>
