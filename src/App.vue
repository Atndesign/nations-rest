<template>
  <main>
    <HomePage @view-details="setCountryDetails" v-if="!isInDetailMode" />
    <Details
      :country="country"
      @close-detail="toggleDetailView"
      v-if="isInDetailMode"
    />
  </main>
</template>

<script>
import HomePage from "./components/homepage/index";
import Details from "./components/details/index";
import "./assets/css/App.css";
export default {
  name: "App",
  components: {
    HomePage,
    Details,
  },
  data() {
    return {
      isInDetailMode: true,
      country: null,
    };
  },
  methods: {
    setCountryDetails(name) {
      this.toggleDetailView();
      this.country = name;
    },
    toggleDetailView() {
      this.isInDetailMode = !this.isInDetailMode;
    },
  },
};
</script>
