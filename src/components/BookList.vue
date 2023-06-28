<template>
  <div class="book-filter">
    <div class="body-regular">{{ filteredBooks.length }} results</div>
    <div class="book-list">
      <div :key="book.id" v-for="book in filteredBooks">
        <BookItem :book="book" :filter="filter" />
      </div>
    </div>
  </div>
</template>

<script>
import BookItem from "../components/BookItem.vue"

export default {
  name: "BookList",
  props: {
    filter: String,
  },
  components: {
    BookItem,
  },
  data() {
    return {
      books: [],
    }
  },
  methods: {
    async fetchBooks() {
      const res = await fetch("api/books");
      const data = await res.json();
      return data;
    },
  },
  computed: {
    filteredBooks() {
      return this.books.filter(book => {
        return (book.title.toLowerCase().includes(this.filter.toLowerCase())
          || book.author.toLowerCase().includes(this.filter.toLowerCase())
          || book.isbn.toLowerCase().includes(this.filter.toLowerCase()));
      });
    }
  },
  async created() {
    this.books = await this.fetchBooks();
  },
}
</script>

<style scoped>
.book-list {
  display: flex;
  width: 100%;
  flex-wrap: wrap;
  justify-content: start;
  align-items: center;
  margin-right: auto;
  margin-left: auto;
  gap: 32px;
}

.book-filter {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: flex-start;
  gap: 16px;
}
</style>