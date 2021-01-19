/* ****************** TEMPLATE ********************* */

<template>
  <nav class="sidebar">
    <ul>
      <li>
        <nuxt-link to="/hotels">
          <img src="~/assets/img/fontawesome/home-solid.png" alt="search" />
          <span>Hotels</span>
        </nuxt-link>
      </li>
      <li>
        <nuxt-link to="#">
          <img src="~/assets/img/fontawesome/plane-solid.png" alt="search" />
          <span>Flights</span>
        </nuxt-link>
      </li>
      <li>
        <nuxt-link to="#">
          <img src="~/assets/img/fontawesome/car-side-solid.png" alt="search" />
          <span>Cars</span>
        </nuxt-link>
      </li>
      <li>
        <nuxt-link to="#">
          <img
            src="~/assets/img/fontawesome/info-circle-solid.png"
            alt="search"
          />
          <span>About</span>
        </nuxt-link>
      </li>
    </ul>
    <p>
      &copy; 2021 by Hight.io. <br />
      All rights reserved
    </p>
  </nav>
</template>

/* ****************** SCRIPT ********************* */

<script>
export default {
  props: [],
  components: {},
  data() {
    return {};
  },
  methods: {},
};
</script>

/* ****************** STYLES ********************* */

<style lang="scss">
@import './Sidebar.scss';
</style>
