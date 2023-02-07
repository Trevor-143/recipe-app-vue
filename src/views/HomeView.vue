<template>
  <div class="home">
    <main>

      <div class="random">
        <img :src="randomMeal.image" :alt="randomMeal.name">
        <div class="randomInfo">
          <h4>{{ randomMeal.name }}</h4>
          <p>{{ randomMeal.description }}</p>
          <button @click="getRandom()">Get Random</button>
        </div>
      </div>

      <div class="form">
        <form>
          <input type="text" class="search_text" >
          <button class="search_button">Search</button>
        </form>
      </div>

      <div class="meals">
        <div class="mealShowcase" v-for="meal in showMeals" :key="meal.id">
            <img :src="meal.image" :alt="meal.name">
            <div class="mealData">
              <h3>{{ meal.name }}</h3>
              <h4>In {{ meal.cookTime }} mins</h4>
              <router-link to="#">Read More</router-link>
            </div>
        </div>
      </div>

    </main>
  </div>
</template>

<script>
import { ref, onBeforeMount } from "vue";
import env from '@/env'

export default {
  name: 'HomeView',
  setup() {
    // const meals = ref([])
    const randomMeal = ref([])
    // const searchText = ref('')
    const showMeals = ref([])
    const options = {
      method: 'GET',
      headers: {
        'X-RapidAPI-Key': env.apiKey,
        'X-RapidAPI-Host': 'low-carb-recipes.p.rapidapi.com'
      }
    };
    onBeforeMount(() => {
      fetch('https://low-carb-recipes.p.rapidapi.com/random', options)
      .then(response => response.json())
      .then(data => {
        randomMeal.value = data;
        // console.log(randomMeal.value)
      })
      fetch('https://low-carb-recipes.p.rapidapi.com/search?name=cake', options)
      .then(response => response.json())
      .then(data => {
        showMeals.value = data
        console.log(showMeals.value)
      })
    })

    const getRandom = () => {
      fetch('https://low-carb-recipes.p.rapidapi.com/random', options)
      .then(response => response.json())
      .then(data => {
        randomMeal.value = data;
        console.log(randomMeal.value)
      })
    }
    
    return {
      randomMeal,
      getRandom,
      showMeals

    }
      
  }

}

</script>

<style>
  main {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
  .random {
    max-width: 900px;
    width: 100%;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    border-radius: 30px;
    background-color: #262455;
    color: #fff;
  }
  .random img {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    object-fit: cover;
    margin: 20px;
  }
  .randomInfo {
    display: flex;
    flex-direction: column;
  }
  .randomInfo p {
    max-width: 550px;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 4; /* number of lines to show */
            line-clamp: 4; 
    -webkit-box-orient: vertical;
  }
  .randomInfo button {
    margin: 10px 0;
    padding: 10px 14px;
    border-radius: 99px;
    color: #262455;
    background-color: #fff;
    width: fit-content;
    border: none;
  }
  .mealShowcase {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 15px;
  }
  /* .mealShowcase .meals {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
  } */
  .mealShowcase img {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    object-fit: cover;
    margin: 10px;
  }
  .mealData {
    display: flex;
    flex-direction: column;
    text-align: center;

  }
</style>
