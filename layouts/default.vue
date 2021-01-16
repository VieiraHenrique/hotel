/* ****************** TEMPLATE ********************* */

<template>
  <div>
    <div class="wrapper">
      <Header />
      <div class="content">
        <Sidebar />
        <nuxt />
      </div>
      <div class="powered">
        <span>Powered by</span><br />
        <img src="~/assets/img/logoBlack.png" alt="" />
      </div>
    </div>
  </div>
</template>

/* ****************** SCRIPT ********************* */

<script>
import Header from '@/components/Header.vue'
import Sidebar from '@/components/Sidebar.vue'

export default {
  props: [],
  components: { Header, Sidebar },
  data() {
    return {}
  },
  methods: {},
}
</script>

/*
**************************************************************************************************************************************
*/ /* ****************** STYLES ********************* */

<style lang="scss">
$gray-light: #f4f2f2;

@import url('https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;600&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Satisfy&display=swap');

html {
  font-size: 62.5%;
  scroll-behavior: smooth;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-weight: 400;
}

body {
  font-family: 'Rubik', sans-serif;
  font-size: 1.6rem;
  /* background: radial-gradient(#536369be, #1d2931c5),
    url(https://images.pexels.com/photos/3293148/pexels-photo-3293148.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260); */
  /* background: radial-gradient(#346e97, #174261); */
  background: #3276b6;
  background-size: cover;
  background-position: center;
}

.wrapper {
  position: relative;
  max-width: 120rem;
  margin: 5rem auto;
  background: $gray-light;
  overflow: hidden;
  border-radius: 1rem;
  box-shadow: 0 2rem 6rem rgba($color: #000000, $alpha: 0.3);
}

.powered {
  position: absolute;
  text-align: center;
  right: 2rem;
  bottom: 2rem;
  font-size: 1.3rem;

  img {
    width: 15rem;
  }
}

.content {
  display: flex;
}

.sidebar {
  flex: 0 0 18%;
}

.main {
  flex: 1;
}
</style>
