<template>
  <div class="dropdown">
    <div class="dropdown__select" @click="openDropDown">
      Filter by region
    </div>
    <ul
      class="dropdown__list"
      :style="{ display: isOpen === true ? 'block' : 'none' }"
    >
      <li class="list__item" @click="changeFilter">Africa</li>
      <li class="list__item" @click="changeFilter">America</li>
      <li class="list__item" @click="changeFilter">Asia</li>
      <li class="list__item" @click="changeFilter">Europe</li>
      <li class="list__item" @click="changeFilter">Oceania</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "DropDown",
  data() {
    return {
      isOpen: false,
      filter: null,
    };
  },
  methods: {
    openDropDown() {
      this.isOpen = !this.isOpen;
    },
    changeFilter(e) {
      this.filter = e.target.innerText;
      this.$emit("change-filter", this.filter);
    },
  },
};
</script>

<style></style>
