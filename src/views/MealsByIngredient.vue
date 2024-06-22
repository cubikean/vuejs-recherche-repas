<template>
    <div class="flex flex-col gap-2 mt-3">
        <MealItem v-for="meal in meals" :key="meal.idMeal" :meal="meal"/>
    </div>
    <div v-if="!meals.length">
    No meals</div>

</template>

<script setup>
import { computed, onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import axiosClient from '../axiosClient';
import MealItem from '../components/MealItem.vue';

const route = useRoute()
const meals = computed(() => store.state.mealsByIngredient)

onMounted(() => {
    store.dispatch('searchMealsByIngredient', route.params.ingredient)
})

</script>