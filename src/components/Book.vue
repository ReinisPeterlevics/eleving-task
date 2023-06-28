<template>
  <div class="book-info">
    <div class="return" @click="openHomeView">
      <img src="../assets/arrow.svg" alt="<-" />
      <div class="link">Explore</div>
    </div>
    <BookDetails :book="book[0]" />
    <Review v-show="!isReviewed && book.length != 0" @add-review="addReview" />
    <div v-show="isReviewed" class="reviewed">
      <div class="caption-bold">Thank you! Review received.</div>
    </div>
    <div v-show="hasError" class="error">
      <div class="caption-bold">Something went wrong. Please try again later.</div>
    </div>
  </div>
</template>

<script>
import BookDetails from "./BookDetails.vue"
import Review from "./Review.vue"

export default {
  name: "Book",
  components: {
    BookDetails,
    Review,
  },
  data() {
    return {
      book: [],
      isReviewed: false,
      hasError: false,
    }
  },
  methods: {
    openHomeView() {
      this.$router.push({ name: 'home', query: { filter: this.$route.query.filter } });
    },
    async fetchBook(id) {
      let response;
      try {
        response = await fetch("api/books?id=" + id);
      } catch (error) {
        this.hasError = true;
        return [];
      }
      if (response?.ok) {
        const data = await response.json();
        return data;
      } else {
        this.hasError = true;
        return [];
      }
    },
    async addReview(review) {
      review.bookid = this.book[0].id;
      let response;
      try {
        response = await fetch('api/reviews', {
          method: 'POST',
          headers: {
            'Content-type': 'application/json',
          },
          body: JSON.stringify(review),
        })
      } catch (error) {
        this.hasError = true;
      }
      if (response?.ok) {
        this.isReviewed = true;
      } else {
        this.hasError = true;
      }
    },
  },
  async created() {
    this.book = await this.fetchBook(this.$route.query.id);
  },
}
</script>

<style scoped>
.book-info {
  display: flex;
  width: 70%;
  padding: 0px auto;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  gap: 40px;
}

.return {
  display: flex;
  align-items: flex-start;
  gap: 4px;
  align-self: stretch;
  cursor: pointer;
  width: fit-content;
  -webkit-transition: 0.3s;
  transition: 0.3s;
}

.return:hover {
  color: var(--typography-medium, #000000B2);
}

.reviewed {
  display: flex;
  padding: 10px;
  align-items: flex-start;
  gap: 10px;
  border-radius: 4px;
  background: var(--ui-light-blue, #CFEBFF);
}

.error {
  display: flex;
  padding: 10px;
  align-items: flex-start;
  gap: 10px;
  border-radius: 4px;
  background: var(--ui-error, #C71B1B);
  color: #FFF;
}
</style>