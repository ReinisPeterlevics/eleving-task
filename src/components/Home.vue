<template>
  <div class="book-explorer">
    <h3>Explore books</h3>
    <SearchBar @search-text="searchBooks" />
    <BookList v-if="filter" :filter="filter" />
    <div v-else class="book-image"><img src="../assets/Book.png" alt="Books"></div>
  </div>
</template>

<script>
import BookList from "./BookList.vue"
import SearchBar from "./UI/SearchBar.vue"

export default {
  name: "Home",
  components: {
    BookList,
    SearchBar,
  },
  data() {
    return {
      filter: this.$route.query.filter,
    }
  },
  methods: {
    searchBooks(text) {
      this.filter = text.replace(/[|&;$%@"<>()+,]/g, "");
    }
  }
}
</script>

<style scoped>
.book-explorer {
  display: flex;
  width: 70%;
  padding: 0px auto;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 35px;
  flex-shrink: 0;
}

.book-image {
  display: flex;
  padding: 10px;
  justify-content: center;
  align-items: center;
  gap: 10px;
  align-self: stretch;
}
</style>