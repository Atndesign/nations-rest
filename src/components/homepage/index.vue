<template>
  <div class="homepage">
    <Header />
    <Input />
  </div>
</template>

<script>
import Header from "../header";
import Input from "../homepage/input";

export default {
  name: "HomePage",
  components: {
    Header,
    Input,
  },
};
</script>

<style>
.homepage {
  font-size: 14px;
}
</style>
