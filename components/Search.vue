/* ****************** TEMPLATE ********************* */

<template>
  <div class="hotels__search">
    <h2>Search for hotels</h2>
    <p>
      Our search engine powered by Artificial Intelligence gives you the right
      choice every time !
    </p>
    <form>
      <div class="form__layout">
        <div class="form__col-left">
          <p>
            <label for="city">City</label>
            <br />
            <input
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
            />
          </p>
        </div>
        <div class="form__col-right">
          <p>
            From
            <br />
            <input type="date" name="from" id="from" />
          </p>
          <p>
            To
            <br />
            <input type="date" name="to" id="to" />
          </p>
        </div>
      </div>
      <button>Let's go !</button>
    </form>
  </div>
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
@import './Search.scss';
</style>
