<template>
  <div class="flag-list">
    <li :key="index" v-for="(country, index) in countries">
      <CountryCard @view-details="viewDetails" :country="country" />
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
  methods: {
    viewDetails(name) {
      this.$emit("view-details", name);
    },
  },
  props: {
    countries: Array,
  },
};
</script>

<style></style>
