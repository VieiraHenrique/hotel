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
    return {}
  },
  methods: {},
}
</script>

/* ****************** STYLES ********************* */

<style lang="scss">
.sidebar {
  background: #57636f;
  background: #444;
  min-height: 50rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding-top: 5rem;

  ul {
    display: flex;
    flex-direction: column;
  }

  li {
    flex: 1;
    text-align: left;

    border-top: 1px solid #fff;

    &:last-child {
      border-bottom: 1px solid #fff;
    }

    &:hover {
      background: #349af7;
    }
  }

  a {
    padding: 2rem 0;
    text-decoration: none;
    color: #fff;
    display: flex;
    align-items: left;
    justify-content: flex-start;
    font-weight: 400;
    img {
      margin-left: 30%;
      margin-right: 1rem;
      width: 2rem;
    }
  }

  p {
    padding-bottom: 5rem;
    color: #ccc;
    font-size: 1.2rem;
    margin: 0 1rem;
    line-height: 1.4;
    text-align: center;
  }
}
</style>
