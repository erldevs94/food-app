<script>
export default {
  props: ["strMealThumb", "strInstructions"],
};
</script>
<template>
  <div class="card-body">
    <figure>
      <img class="w-100" :src="strMealThumb" />
    </figure>
    <h3>Instructions</h3>
    <small>{{ strInstructions }}</small>
    <slot class="font-weight-bold" />
  </div>
</template>

<style scoped>
  figure img{
    max-width: 30rem;
    margin:auto;
  }
</style>
