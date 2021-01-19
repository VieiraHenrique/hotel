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
import Header from '@/components/Header.vue';
import Sidebar from '@/components/Sidebar.vue';

export default {
  props: [],
  components: { Header, Sidebar },
  data() {
    return {};
  },
  methods: {},
};
</script>

/*
**************************************************************************************************************************************
*/ /* ****************** STYLES ********************* */

<style lang="scss">
@import './default.scss';
</style>
