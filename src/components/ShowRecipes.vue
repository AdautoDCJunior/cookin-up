<script lang="ts">
import CButton from './CButton.vue';
import { getRecipes } from '@/http/index';
import CardRecipe from './CardRecipe.vue';
import type IRecipe from '@/interfaces/IRecipe';
import type { PropType } from 'vue/dist/vue.js';
import { list1InList2 } from '@/operations/list';

export default {
  props: {
    ingredients: { type: Array as PropType<string[]>, required: true }
  },
  data() {
    return {
      findedRecipes: [] as IRecipe[]
    };
  },
  async created() {
    const recipes = await getRecipes();

    this.findedRecipes = recipes.filter((recipe) =>
      list1InList2(recipe.ingredientes, this.ingredients)
    );
  },
  emits: ['editRecipes'],
  components: { CardRecipe, CButton }
};
</script>

<template>
  <section class="show-recipes">
    <h1 class="header recipes-title">Receitas</h1>

    <p class="paragraph-lg results-found">
      Resultados encontrados: {{ findedRecipes.length }}
    </p>

    <div v-if="findedRecipes.length" class="recipes-wrapper">
      <p class="paragraph-lg information">
        Veja as opções de receitas que encontramos com os ingredientes que você
        tem por aí!
      </p>

      <ul class="recipes">
        <li v-for="recipe in findedRecipes" :key="recipe.nome">
          <CardRecipe :recipe="recipe" />
        </li>
      </ul>
    </div>

    <div v-else class="recipes-not-found">
      <p class="paragraph-lg recipes-not-found__info">
        Ops, não encontramos resultados para sua combinação. Vamos tentar de
        novo?
      </p>

      <img
        src="../assets/images/no-recipes.png"
        alt="esenho de um ovo quebrado. A gema tem um rosto com uma expressão triste."
      />
    </div>

    <CButton text="Editar lista" @click="$emit('editRecipes')" />
  </section>
</template>

<style scoped>
.show-recipes {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}
.recipes-title {
  color: var(--verde-medio);
  margin-bottom: 1.5rem;
}
.results-found {
  color: var(--verde-medio);
  margin-bottom: 0.5rem;
}
.recipes-wrapper {
  margin-bottom: 3.5rem;
}
.information {
  margin-bottom: 2rem;
}
.recipes {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  flex-wrap: wrap;
}
.recipes-not-found {
  margin-bottom: 2rem;
}
.recipes-not-found__info {
  margin-bottom: 0.5rem;
}
@media only screen and (max-width: 767px) {
  .recipes-wrapper {
    margin-bottom: 2rem;
  }
}
</style>
