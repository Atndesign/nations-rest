<template>
  <div class="homepage">
    <Header />
    <Input
      @search-country="searchForCountry"
      @fetch-countries="fetchAllCountries"
    />
    <DropDown />
    <FlagList :countries="countries" />
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
    };
  },
  methods: {
    searchForCountry(data) {
      axios
        .get(`https://restcountries.eu/rest/v2/name/${data}`)
        .then((data) => {
          this.countries = data.data;
        });
    },
    fetchAllCountries() {
      axios.get("https://restcountries.eu/rest/v2/all").then((data) => {
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
