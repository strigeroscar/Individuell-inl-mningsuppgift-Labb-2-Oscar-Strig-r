<script setup>
import Cocktail from '../components/CocktailApp.vue'
</script>

<template>
    <h1>This is an Cocktail Page</h1>
  <div id="app">
      <div>
        <img :src="cocktail.strDrinkThumb" alt="Cocktail Image" class="cocktailimg"><!--v-bind img. bild från api-->
        <h2>Drink namn: {{ cocktail.strDrink }}</h2>
        <p>Kategori: {{ cocktail.strCategory }}</p>
        <p>Glas: {{ cocktail.strGlass }}</p>
        <p>Instruktioner: {{ cocktail.strInstructions }}</p>
        <p>Ingredienser:</p>
        <ul>
          <li v-for="i in ingredientCount">{{ cocktail['strIngredient' + i] }}</li><!--gör så att ingredienslistan är lika lång som ingredienser-->
        </ul>
      </div>
    </div>
<div>
  <button @click="generateCocktail">Generera cocktail</button><!--Knapp som kör fetchen igen-->
</div>
</template>

<script>
export default {
  created() {
    this.generateCocktail();
  },
  data() {
    return { cocktail: null }
  },
  computed: {
    ingredientCount() {
      let count = 0;
      while (this.cocktail && this.cocktail['strIngredient' + (count + 1)]) {
        count++;
      }
      return count;
    }
  },
  methods: {
    generateCocktail() {
      fetch('https://www.thecocktaildb.com/api/json/v1/1/random.php')
        .then(response => response.json())
        .then(result => {
          this.cocktail = result.drinks[0];
        });
    }
  }
}
</script>

<style>
.cocktailimg{
  width: 250px;
  height: 250px;
}
</style>
