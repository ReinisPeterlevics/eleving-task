<template>
  <div class="book">
    <div class="book-item">
      <div class="book-cover"
        v-bind:style="{ background: 'url(' + book.image + ')', backgroundSize: 'cover', backgroundPosition: 'center' }">
      </div>
      <div class="book-info">
        <div class="title">{{ book.title }}</div>
        <div class="body-regular">{{ book.author }}</div>
        <div class="body-regular">2023</div>
        <div class="body-bold">{{ book.price }}</div>
        <div class="body-regular">{{ book.publisher }}</div>
      </div>
    </div>
    <div class="book-rating">
      <div class="body-regular">{{ book.rating }}</div>
      <StarRating :rating="book.rating" :selectable="selectable" />
    </div>
  </div>
</template>

<script>
import StarRating from "./UI/StarRating.vue"

export default {
  name: "BookItem",
  props: {
    book: Object,
    filter: String,
  },
  components: {
    StarRating,
  },
  data() {
    return {
      selectable: false,
    }
  },
}
</script>

<style scoped>
.book {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 24px;
}

.book-item {
  display: flex;
  align-items: flex-start;
  gap: 14px;
  flex: 1 0 0;
  flex-wrap: wrap;
}

.book-cover {
  width: 120px;
  height: 160px;
  border-radius: 4px;
  background: lightgray 50% / cover no-repeat;
}

.book-info {
  width: 180px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 3px;
  flex: 1 0 0;
  text-align: left;
}

.book-rating {
  display: flex;
  flex-direction: row;
  gap: 8px;
}
</style>