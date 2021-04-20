<template>
  <main>
    <HomePage v-if="!isInDetailMode" />
    <Details @close-detail="closeDetailView" v-if="isInDetailMode" />
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
    };
  },
  methods: {
    closeDetailView() {
      console.log("Hello");
      this.isInDetailMode = !this.isInDetailMode;
    },
  },
};
</script>
