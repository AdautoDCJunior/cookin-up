<script lang="ts">
import type { PropType } from 'vue';
import Tag from './Tag.vue';

export default {
  props: {
    ingredients: { type: Array as PropType<string[]>, required: true }
  },
  components: { Tag }
};
</script>

<template>
  <section>
    <span class="subtitle-lg your-text-list"> Sua lista: </span>

    <ul v-if="ingredients.length" class="ingredients-your-list">
      <li v-for="ingredient in ingredients" :key="ingredient">
        <Tag :text="ingredient" :activate="true" />
      </li>
    </ul>

    <p v-else class="paragraph empty-list">
      <img src="../assets/icons/empty-list.svg" alt="Ícone de pesquisa" />
      Sua lista está vazia, selecione ingredientes para iniciar.
    </p>
  </section>
</template>

<style scoped>
.your-text-list {
  color: var(--coral, #f0633c);
  display: block;
  text-align: center;
  margin-bottom: 1.5rem;
}

.ingredients-your-list {
  display: flex;
  justify-content: center;
  gap: 1rem 1.5rem;
  flex-wrap: wrap;
}

.empty-list {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.25rem;

  color: var(--coral, #f0633c);
  text-align: center;
}
</style>
