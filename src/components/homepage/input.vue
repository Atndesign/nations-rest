<template>
  <div class="searchbar">
    <form class="searchbar__container" @submit="searchForCountry">
      <img src="../../assets/img/search.svg" alt="" srcset="" />
      <input
        type="text"
        class="searchbar-container__input"
        placeholder="Search for a country"
        v-model="countrySearchName"
      />
    </form>
  </div>
</template>

<script>
export default {
  name: "Input",
  data() {
    return {
      countrySearchName: "",
    };
  },
  methods: {
    searchForCountry(e) {
      e.preventDefault();
      if (this.countrySearchName !== "") {
        this.$emit("search-country", this.countrySearchName);
        return;
      } else {
        this.$emit("fetch-countries", this.countrySearchName);
        return;
      }
    },
  },
};
</script>

<style></style>
