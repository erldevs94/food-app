<script>
import { BIconYoutube, BIconArrowClockwise } from "bootstrap-icons-vue";

export default {
  props: [
    "apiUrl",
    "mealItem",
    "strMeal",
    "strMealThumb",
    "strYoutube",
    "strSource",
    "mealIngredients",
  ],
  components: {
    BIconYoutube,
    BIconArrowClockwise,
  },
  methods: {
    reloadBtn() {
      fetch(this.apiUrl)
        .then((response) => response.json())
        .then((data) => {
          this.mealItem = data.meals[0]
        })
        .catch(console.error);
    },
  },
};
</script>

<template>
  <div class="row">
    <p :apiUrl="apiUrl">{{apiUrl}}test</p>
    <div class="col-md-4">
      <figure>
        <img class="mw-100 rounded" :src="strMealThumb" alt="" />
        <figcaption v-if="strSource">
          <a target="_blank" :href="strSource">Read the full source</a>
        </figcaption>
      </figure>
    </div>
    <div class="col-md-8">
      <h2>{{ strMeal }}</h2>
      <div class="d-flex justify-content-between">
        <a target="_blank" class="btn btn-light btn-sm" :href="strYoutube">
          <b-icon-youtube class="text-danger" /> Watch on YouTube</a
        >
      </div>
      <div class="table-responsive">
        <table class="table">
          <thead>
            <tr>
              <th>Ingredients</th>
              <th>Measurements</th>
            </tr>
          </thead>
          <tbody>
            <template v-for="(value, key) in mealIngredients" :key="key">
              <tr v-if="mealItem[value]">
                <td>{{ mealItem[key] }}</td>
                <td>{{ mealItem[value] }}</td>
              </tr>
            </template>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<style scoped>
div.table-responsive {
  max-height: 20rem;
}
</style>
