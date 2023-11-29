<script lang="ts">
export default {
  props: {
    text: { type: String, required: true },
    activate: Boolean
  }
};
</script>

<template>
  <spa :class="['tag', { activate }]">
    {{ text }}
  </spa>
</template>

<style scoped>
.tag {
  display: inline-block;
  border-radius: 0.5rem;
  min-width: 4.25rem;
  padding: 0.5rem;
  text-align: center;
  transition: 0.2s;
  color: var(--cinza);
  background: var(--cinza-claro);
  font-weight: 400;
}

.tag.activate {
  color: var(--creme, #fffaf3);
  background: var(--coral, #f0633c);
  font-weight: 700;
}
</style>
