/* ****************** TEMPLATE ********************* */

<template>
  <div>
    <div class="wrapper">
      <Header />
      <div class="content">
        <Sidebar />
        <nuxt />
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
@import url('https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;600&display=swap');

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
  min-height: 100vh;
  background: radial-gradient(#01c0ff, #174261);
  background-size: cover;
}

.wrapper {
}
</style>
