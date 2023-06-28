<template>
  <div class="book-list-item" @click="openBookView">
    <div class="book-cover"
      v-bind:style="{ background: 'url(' + book.image + ')', backgroundSize: 'cover', backgroundPosition: 'center' }">
    </div>
    <div class="book-info">
      <div class="body-bold">{{ book.title }}</div>
      <div class="caption-regular">{{ book.author }}</div>
      <div class="caption-regular">2023</div>
      <div class="caption-bold">{{ book.price }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "BookItem",
  props: {
    book: Object,
    filter: String,
  },
  methods: {
    openBookView() {
      this.$router.push({ name: 'book', query: { id: this.book.id, filter: this.filter } });
    }
  }
}
</script>

<style scoped>
.book-list-item {
  display: flex;
  align-items: flex-start;
  gap: 14px;
  flex: 1 0 0;
  cursor: pointer;
  border-radius: 4px;
  -webkit-transition: 0.3s;
  transition: 0.3s;
  flex-wrap: wrap;
}

.book-list-item:hover {
  background-color: var(--ui-lightgrey, #F3F3F3);
}

.book-cover {
  width: 88px;
  height: 110px;
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
</style>