<template>
  <label>
    <input :class="[text ? 'active' : '', 'search-bar body-regular']" type="text" v-model="text" name="text"
      placeholder="Search for a book" v-on:input="onSearch" />
  </label>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      text: "",
    }
  },
  methods: {
    onSearch() {
      this.$emit("search-text", this.text);
    }
  }
}
</script>

<style scoped>
label {
  position: relative;
  cursor: text;
}

label::before {
  content: "";
  position: absolute;
  left: 10px;
  top: 9px;
  bottom: 0;
  width: 24px;
  height: 24px;
  flex-shrink: 1;
  background: url("../../assets/search.svg");
}

.search-bar {
  display: flex;
  width: 70%;
  padding: 8px 42px;
  align-items: flex-start;
  gap: 10px;
  border-radius: 4px;
  border: 1px solid var(--ui-grey, #DDE1E3);
  background: #FFF;
  color: var(--typography-light, rgba(0, 0, 0, 0.55));
}

.search-bar.active {
  color: var(--typography-dark, rgba(0, 0, 0, 0.95));
}
</style>