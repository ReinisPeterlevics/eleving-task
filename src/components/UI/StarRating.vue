<template>
  <div>
    <img :src="showStar(rating, 1)" v-bind:class="{ 'selectable': selectable }" @click="getRating(1)" alt="*" />
    <img :src="showStar(rating, 2)" v-bind:class="{ 'selectable': selectable }" @click="getRating(2)" alt="*" />
    <img :src="showStar(rating, 3)" v-bind:class="{ 'selectable': selectable }" @click="getRating(3)" alt="*" />
    <img :src="showStar(rating, 4)" v-bind:class="{ 'selectable': selectable }" @click="getRating(4)" alt="*" />
    <img :src="showStar(rating, 5)" v-bind:class="{ 'selectable': selectable }" @click="getRating(5)" alt="*" />
  </div>
</template>

<script>
export default {
  name: "StarRating",
  props: {
    rating: Number,
    selectable: Boolean,
  },
  methods: {
    showStar(rating, star) {
      if ((rating - star) > -0.5) {
        return require("../../assets/star=stat-filled.svg");
      } else {
        return require("../../assets/star=stat-outline.svg");
      }
    },
    getRating(star) {
      this.$emit("star-rating", star);
    }
  }
}
</script>

<style scoped>
.selectable {
  cursor: pointer;
}
</style>