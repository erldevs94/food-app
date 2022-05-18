<script>
	import CardHeader from "./CardHeader.vue";
	import CardBody from "./CardBody.vue";

	export default {
		components: {
			CardHeader,
			CardBody,
		},
		props: [
			"apiUrl",
			"mealItem",
			"strMeal",
			"strMealThumb",
			"strInstructions",
			"strYoutube",
			"strSource",
			"mealIngredients",
		],
	};
</script>

<template>
	<div class="p-md-5">
		
		<CardHeader :mealItem="mealItem" :apiUrl="apiUrl" :strMealThumb="strMealThumb" :strMeal="strMeal"
			:strYoutube="strYoutube" :strSource="strSource" :mealIngredients="mealIngredients" />
		<CardBody :strInstructions="strInstructions" />

		<button @click="$emit('someEvent')" class="btn btn-primary btn-sm">
			<b-icon-arrow-clockwise /> Load new Recipe
		</button>
	</div>
</template>

<style scoped>
	.card {}
</style>
