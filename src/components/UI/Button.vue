<template>
  <button @click="onClick()" class="button body-bold">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    text: String,
  },
  methods: {
    onClick() {
      this.$emit('button-click');
    },
  },
}
</script>

<style scoped>
.button {
  display: flex;
  padding: 10px;
  justify-content: center;
  align-items: center;
  gap: 10px;

  border-radius: 24px;
  border: 2px solid var(--ui-primary, #3980B2);
  color: var(--ui-primary, #3980B2);
  background: #FFF;
  cursor: pointer;

  -webkit-transition: 0.3s;
  transition: 0.3s;
}
.button:hover,
.button:active {
  background: var(--ui-lightblue, #CFEBFF);
}
</style>
