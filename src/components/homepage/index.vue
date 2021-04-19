<template>
  <div class="homepage">
    <Header />
    <Input />
    <DropDown />
  </div>
</template>

<script>
import Header from "../header";
import Input from "../homepage/input";
import DropDown from "../homepage/dropdown";

export default {
  name: "HomePage",
  components: {
    Header,
    Input,
    DropDown,
  },
};
</script>

<style>
.homepage {
  font-size: 14px;
}
</style>
