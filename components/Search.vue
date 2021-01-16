/* ****************** TEMPLATE ********************* */

<template>
  <div class="hotels__search">
    <h2>Search for hotels</h2>
    <p>
      Our search engine powered by Artificial Intelligence gives you the right
      choice every time !
    </p>
    <form action="#">
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
            <input type="number" name="adults" id="adults" value="1" />
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
    return {}
  },
  methods: {},
}
</script>

/* ****************** STYLES ********************* */

<style lang="scss">
.hotels__search {
  /* margin: 3rem; */
  width: fit-content;
  background: #fff;
  padding: 3rem;
  box-shadow: 0 1px 2px rgba($color: #000000, $alpha: 0.3);
  border-radius: 1rem;

  h2 {
    font-weight: 400;
    letter-spacing: 1px;
  }

  p {
    margin-top: 1rem;
    color: #777;
    max-width: 400px;
  }

  form {
    .form__layout {
      display: flex;
      gap: 3rem;
      input {
        margin-top: 0.5rem;
        border: none;
        outline: none;
        background: #f4f2f2;
        border: 1px solid #ccc;
        padding: 1rem;
        border-radius: 10rem;
        font-family: 'rubik', sans-serif;
        font-size: 1.4rem;
        box-shadow: 0 1px 2px rgba($color: #000000, $alpha: 0.3);

        &[type='date'] {
          padding: 0.8rem 1rem;
        }
      }

      p {
        font-size: 1.4rem;
        margin-top: 3rem;
      }
    }
    button {
      border: none;
      outline: none;
      background: #349af7;
      color: #fff;
      padding: 1rem 2rem;
      box-shadow: 0 1px 2px rgba($color: #000000, $alpha: 0.3);
      margin-top: 2rem;
      cursor: pointer;
    }
  }
}
</style>
