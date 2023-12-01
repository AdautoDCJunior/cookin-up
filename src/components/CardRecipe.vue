<script lang="ts">
import type { PropType } from 'vue';
import type IRecipe from '@/interfaces/IRecipe';

export default {
  props: {
    recipe: { type: Object as PropType<IRecipe>, required: true }
  }
};
</script>

<template>
  <article class="recipe">
    <header>
      <img
        class="recipe__image"
        :src="`/images/recipes/${recipe.imagem}`"
        alt="`Foto de ${receita.nome}`"
      />
    </header>

    <section class="recipe__body">
      <h2 class="paragraph-bold">
        {{ recipe.nome }}
      </h2>
    </section>
  </article>
</template>

<style scoped>
.recipe {
  display: flex;
  width: 17.625rem;
  max-width: 19.5rem;
  flex-direction: column;
  align-items: center;
  border-radius: 1rem;
  background: var(--Branco, #fff);
  box-shadow: 4px 4px 12px 0px rgba(68, 68, 68, 0.08);
}

.recipe__image {
  width: 100%;
  border-radius: 1rem 1rem 0rem 0rem;
  display: block;
}

.card-recipe__p_i {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
.recipe__body {
  padding: 2rem 1rem;
}
</style>
