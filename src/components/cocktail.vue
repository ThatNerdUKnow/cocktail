<template>
  <div class="p-3 bg-secondary rounded">
    <header></header>
    <div class="row">
        <div class="col-6">
      <img class="img-fluid rounded shadow-lg" :src="drink.strDrinkThumb" />
      <div class="btn btn-light my-3" @click="getData()">Try another drink 🍸</div>
      </div>
      <div class="col-6 text-white">
        <h1>{{ drink.strDrink }}</h1>
        <ul>
      <div :key="drinkComponent.id" v-for="drinkComponent in drinkComponents">
        <li v-if="drinkComponent.ingredient">
          {{ drinkComponent.ingredient }}
          {{ drinkComponent.measure }}
        </li>
      </div>
    </ul>
    <p class="container">{{ drink.strInstructions }}</p>
    
      </div>
    </div>

    

    
  </div>
</template>

<script>
import axios from "axios";
export default {
  methods:
  {
    getData()
    {
      
      axios
      .get("https://www.thecocktaildb.com/api/json/v1/1/random.php")
      .then((res) => {
        this.drinkComponents = [];
        console.log(res.data);
        this.drink = res.data.drinks[0];
        let i = 0;
        for (i = 1; i < 16; i++) {
          let drinkComponent = {
            ingredient: this.drink[`strIngredient${i}`],
            measure: this.drink[`strMeasure${i}`],
            id: i,
          };
          this.drinkComponents.push(drinkComponent);

        }
      });
    }
  },
  mounted() {
    this.getData();
  },
  data() {
    let drink = {};
    let drinkComponents = [];

    return { drink, drinkComponents };
  },
};
</script>

<style>
</style>