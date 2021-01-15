/* ****************** TEMPLATE ********************* */

<template>
  <div class="header">
    <div class="header__logo">
      <img src="~/assets/img/smallLogo.png" alt="logo" />
    </div>
    <div class="header__search">
      <form action="#" id="search">
        <input
          id="searchInput"
          type="text"
          class="header__search--input"
          placeholder="Search hotels"
        />
        <button class="header__search--button">
          <img src="~/assets/img/fontawesome/search-solid.png" alt="search" />
        </button>
      </form>
    </div>
    <div class="header__nav">
      <div class="header__nav--bookmark">
        <img src="~/assets/img/fontawesome/bookmark-solid.png" alt="bookmark" />
      </div>
      <div class="header__nav--notifications">
        <img src="~/assets/img/fontawesome/comments-solid.png" alt="search" />
      </div>
      <div class="header__nav--user">
        <img src="~/assets/img/henrique.jpg" alt="user-image" />
        <span>Henrique</span>
      </div>
    </div>
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
.header {
  background: #fff;
  height: 7rem;
  border-bottom: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 3rem;

  &__logo {
    width: 4rem;

    img {
      width: 4rem;
    }
  }

  &__search {
    flex: 0 0 40%;
    form {
      display: flex;
      align-items: center;
      input {
        flex: 1;
        background: #f4f2f2;
        border-radius: 20rem;
        padding: 1rem 4.5rem 1rem 3rem;
        border: 1px solid #ccc;

        &:focus {
          /* border: none; */
          outline: none;
        }
      }
      button {
        border: none;
        background: transparent;
        margin-left: -3.5rem;
        img {
          width: 2rem;
          cursor: pointer;
        }
      }
    }
  }

  &__nav {
    display: flex;
    align-items: center;
    gap: 2rem;

    img {
      width: 2rem;
      color: #174261;
      cursor: pointer;
    }

    &--user {
      cursor: pointer;
      display: flex;
      gap: 0.5rem;
      align-items: center;
      img {
        width: 3rem;
        border-radius: 50%;
      }

      span {
        display: inline-block;
        font-size: 1.2rem;
      }
    }
  }
}
</style>
