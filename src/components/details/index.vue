<template>
  <div id="detail">
    <Header />
    <div class="top-controls">
      <BackBtn @close-detail="closeDetailView" />
    </div>
    <div class="infos"></div>
  </div>
</template>

<script>
import Header from "../header";
import BackBtn from "../back";
import axios from "axios";

export default {
  name: "Details",
  components: {
    Header,
    BackBtn,
  },
  data() {
    return {
      countryInfos: null,
    };
  },
  mounted() {
    axios.get("https://restcountries.eu/rest/v2/name/belgium").then((data) => {
      this.countryInfos = data.data;
      console.log(data.data[0]);
    });
  },
  methods: {
    closeDetailView() {
      this.$emit("close-detail");
    },
  },
};
</script>

<style></style>
