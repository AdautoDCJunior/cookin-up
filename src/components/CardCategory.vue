<script lang="ts">
import type { PropType } from 'vue';
import type ICategory from '@/interfaces/ICategory';
import SelectedIngredient from './SelectedIngredient.vue';

export default {
  props: {
    category: { type: Object as PropType<ICategory>, required: true }
  },
  emits: ['addIngredient', 'removeIngredient'],
  components: { SelectedIngredient }
};
</script>

<template>
  <article class="category">
    <header class="category__header">
      <img
        :src="`/images/icons/ingredient-categories/${category.imagem}`"
        alt=""
        class="category__image"
      />

      <h2 class="paragraph-lg category__name">{{ category.nome }}</h2>
    </header>

    <ul class="category__ingredient">
      <li v-for="ingredient in category.ingredientes" :key="ingredient">
        <SelectedIngredient
          :ingredient="ingredient"
          @addIngredient="$emit('addIngredient', $event)"
          @removeIngredient="$emit('removeIngredient', $event)"
        />
      </li>
    </ul>
  </article>
</template>

<style scoped>
.category {
  width: 19.5rem;
  padding: 1rem;
  border-radius: 1rem;
  background: var(--branco, #fff);
  box-shadow: 4px 4px 10px 0px rgba(68, 68, 68, 0.05);
  height: 100%;

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

.category__header {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

.category__image {
  width: 3.5rem;
}

.category__name {
  text-align: center;
  color: var(--verde-medio, #3d6d4a);
  font-weight: 700;
}

.category__ingredient {
  display: flex;
  justify-content: center;
  gap: 0.5rem;
  flex-wrap: wrap;
}
</style>
