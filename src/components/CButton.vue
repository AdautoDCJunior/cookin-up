<script lang="ts">
export default {
  props: {
    text: { type: String, required: true }
  }
};
</script>

<template>
  <button class="paragraph-lg button">{{ text }}</button>
</template>

<style scoped>
.button {
  color: var(--creme);
  text-align: center;
  background: var(--coral);
  padding: 23px 156px;
  border-radius: 32px;
  box-shadow: 4px 4px 15px 0px rgba(255, 115, 76, 0.25);
  cursor: pointer;
}

.button:hover {
  background: var(--ocre-hover, #d1451e);
}
</style>
