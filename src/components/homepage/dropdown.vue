<template>
  <div class="dropdown">
    <div class="dropdown__select" @click="openDropDown">
      {{ filter === null ? "Filter by region" : filter }}
    </div>
    <ul
      class="dropdown__list"
      :style="{ display: isOpen === true ? 'block' : 'none' }"
    >
      <li class="list__item" @click="changeFilter">Africa</li>
      <li class="list__item" @click="changeFilter">Americas</li>
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
      this.isOpen = !this.isOpen;
      this.$emit("change-filter", this.filter);
    },
  },
};
</script>

<style></style>
