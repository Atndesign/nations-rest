<template>
  <div class="homepage">
    <Header />
    <div class="top-controls">
      <Input
        @search-country="searchForCountry"
        @fetch-countries="fetchAllCountries"
      />
      <DropDown @change-filter="searchForRegion" />
    </div>
    <div
      class="loading"
      :style="{ display: isLoading === true ? 'block' : 'none' }"
    >
      <img class="loader" src="../../assets/img/loader.gif" alt="" srcset="" />
    </div>
    <div
      class="flags"
      :style="{ display: isLoading === false ? 'block' : 'none' }"
    >
      <p class="flags__error">
        {{ this.countries.length === 0 ? "No result found for this" : "" }}
      </p>
      <FlagList :countries="countries" />
    </div>
  </div>
</template>

<script>
const axios = require("axios");
import Header from "../header";
import Input from "../homepage/input";
import DropDown from "../homepage/dropdown";
import FlagList from "../homepage/FlagList";
export default {
  name: "HomePage",
  components: {
    Header,
    Input,
    DropDown,
    FlagList,
  },
  data() {
    return {
      countries: [],
      isLoading: false,
    };
  },
  methods: {
    searchForCountry(data) {
      this.isLoading = true;
      axios
        .get(`https://restcountries.eu/rest/v2/name/${data}`)
        .then((data) => {
          this.isLoading = false;
          this.countries = data.data;
        })
        .catch(() => {
          console.log("catch");
          this.isLoading = false;
          this.countries = [];
        });
    },
    searchForRegion(data) {
      this.isLoading = true;
      axios
        .get(`https://restcountries.eu/rest/v2/region/${data}`)
        .then((data) => {
          this.isLoading = false;
          this.countries = data.data;
        });
    },
    fetchAllCountries() {
      this.isLoading = true;
      axios.get("https://restcountries.eu/rest/v2/all").then((data) => {
        this.isLoading = false;
        this.countries = data.data;
      });
    },
  },
  mounted() {
    this.fetchAllCountries();
  },
};
</script>

<style>
.homepage {
  font-size: 14px;
}
</style>
