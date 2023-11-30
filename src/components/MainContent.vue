<script lang="ts">
import YourListVue from './YourList.vue';
import SelectIngredients from './SelectIngredients.vue';

export default {
  data() {
    return {
      ingredients: [] as string[]
    };
  },
  methods: {
    addIngredient(ingredient: string) {
      this.ingredients.push(ingredient);
    },
    removeIngredient(ingredient: string) {
      this.ingredients = this.ingredients.filter((item) => item !== ingredient);
    }
  },
  components: { SelectIngredients, YourListVue }
};
</script>

<template>
  <main class="main-content">
    <YourListVue :ingredients="ingredients" />
    <SelectIngredients
      @addIngredient="addIngredient"
      @removeIngredient="removeIngredient"
    />
  </main>
</template>

<style scoped>
.main-content {
  padding: 6.5rem 7.5rem;
  border-radius: 3.75rem 3.75rem 0rem 0rem;
  background: var(--creme, #fffaf3);
  color: var(--cinza, #444);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5rem;
}

@media only screen and (max-width: 1300px) {
  .main-content {
    padding: 5rem 3.75rem;
    gap: 3.5rem;
  }
}

@media only screen and (max-width: 767px) {
  .main-content {
    padding: 4rem 1.5rem;
    gap: 4rem;
  }
}
</style>
