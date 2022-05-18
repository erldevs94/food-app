<script>
import CardMain from "./components/CardMain.vue";
export default {
  data() {
    return {
      mealItem: "",
      apiUrl: "https://www.themealdb.com/api/json/v1/1/random.php",
      mealIngredients: {},
    };
  },
  components: {
    CardMain,
  },
  mounted() {
    fetch(this.apiUrl)
      .then((response) => response.json())
      .then((data) => {
        this.mealItem = data.meals[0];
      })
      .catch(console.error);
  },
  computed: {
    getIngredients() {
      let strIngredient = "strIngredient";
      let strMeasure = "strMeasure";

      for (let i = 1; i <= 20; i++) {
        this.mealIngredients[strIngredient + i] = strMeasure + i;
      }
      return this.mealIngredients;
    },
  },
  methods: {
    callback() {
      fetch(this.apiUrl)
        .then((response) => response.json())
        .then((data) => {
          this.mealItem = data.meals[0];
        })
        .catch(console.error);
    },
  },
};
</script>

<template>
  <div>
    <CardMain
      :mealItem="mealItem"
      :apiUrl="apiUrl"
      :strMeal="mealItem.strMeal"
      :strMealThumb="mealItem.strMealThumb"
      :strInstructions="mealItem.strInstructions"
      :strYoutube="mealItem.strYoutube"
      :strSource="mealItem.strSource"
      :mealIngredients="getIngredients"
      @some-event="callback"
    />
  </div>
</template>
