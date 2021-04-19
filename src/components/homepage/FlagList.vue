<template>
  <div class="flag-list">
    <li :key="index" v-for="(country, index) in countries">
      <CountryCard :country="country" />
    </li>
  </div>
</template>

<script>
import CountryCard from "./countryCard";
export default {
  name: "FlagList",
  components: {
    CountryCard,
  },
  data() {
    return {};
  },
  props: {
    countries: Array,
  },
};
</script>

<style></style>
