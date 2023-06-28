<template>
  <form class="review" @submit="onSubmit">
    <div class="title">Write a review</div>
    <div class="review-rating">
      <div class="body-large-bold">Rate the book</div>
      <StarRating @star-rating="rateBook" :rating="rating" :selectable="selectable" />
    </div>
    <textarea class="review-text caption-regular" type="text" v-model="text" name="text" />
    <Button :text="buttontext" />
  </form>
</template>

<script>
import StarRating from './UI/StarRating.vue';
import Button from "./UI/Button.vue"

export default {
  name: "Review",
  components: {
    StarRating,
    Button,
  },
  data() {
    return {
      buttontext: "Submit review",
      selectable: true,
      rating: 0,
      text: "",
    }
  },
  methods: {
    onSubmit(event) {
      event.preventDefault();
      if (this.rating === 0) {
        alert("Please add a rating");
        return;
      }
      if (!this.text) {
        alert("Please enter review text");
        return;
      }
      const newReview = {
        rating: this.rating,
        text: this.text,
      }
      this.$emit("add-review", newReview);
      this.rating = 0;
      this.text = "";
    },
    rateBook(star) {
      this.rating = star;
    }
  }
}
</script>

<style scoped>
.review {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 24px;
  align-self: stretch;
}

.review-rating {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 8px;
}

.review-text {
  height: 208px;
  align-self: stretch;

  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 8px;
}
</style>