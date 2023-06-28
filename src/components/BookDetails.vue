<template>
  <div class="content" v-if="book">
    <BookInfo :book="book" />
    <div class="description">
      <div class="body-regular">{{ book.description }}</div>
    </div>
  </div>
</template>

<script>
import BookInfo from "../components/BookInfo.vue"

export default {
  name: "BookDetails",
  props: {
    book: Object,
  },
  components: {
    BookInfo,
  },
}
</script>

<style scoped>
.content {
  display: flex;
  align-items: flex-start;
  flex-wrap: wrap;
  gap: 24px;
  align-self: stretch;
}

.description {
  display: flex;
  flex-basis: 200px;
  flex-grow: 1;
}
</style>