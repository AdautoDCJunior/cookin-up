<script lang="ts">
import { getCategories } from '@/http/index';
import CardCategory from './CardCategory.vue';
import type ICategory from '@/interfaces/ICategory';
import CButton from './CButton.vue';

export default {
  data() {
    return {
      categories: [] as ICategory[]
    };
  },
  async created() {
    this.categories = await getCategories();
  },
  emits: ['addIngredient', 'removeIngredient', 'ChangePage'],
  components: { CardCategory, CButton }
};
</script>

<template>
  <section class="select-ingredients">
    <h1 class="header ingredient-title">Ingredientes</h1>

    <p class="paragraph-lg instructions">
      Selecione abaixo os ingredientes que você quer usar nesta receita:
    </p>

    <ul class="categories">
      <li v-for="category in categories" :key="category.nome">
        <CardCategory
          :category="category"
          @addIngredient="$emit('addIngredient', $event)"
          @removeIngredient="$emit('removeIngredient', $event)"
        />
      </li>
    </ul>

    <p class="paragraph tip">
      *Atenção: consideramos que você tem em casa sal, pimenta e água.
    </p>

    <CButton text="Buscar receitas!" @click="$emit('ChangePage')" />
  </section>
</template>

<style scoped>
.select-ingredients {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.ingredient-title {
  color: var(--verde-medio, #3d6d4a);
  display: block;
  margin-bottom: 1.5rem;
}

.instructions {
  margin-bottom: 2rem;
}

.categories {
  margin-bottom: 1rem;
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  flex-wrap: wrap;
}

.tip {
  align-self: flex-start;
  margin-bottom: 3.5rem;
}

@media only screen and (max-width: 767px) {
  .tip {
    margin-bottom: 2.5rem;
  }
}
</style>
