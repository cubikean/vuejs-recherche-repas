<template>

    <div class="bg-white shadow rounded p-2">
        <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
            <img :src="meal.strMealThumb" :alt="meal.strMeal">
        </router-link>
        <h3 class="font-bold">{{ meal.strMeal }}</h3>
        <p class="line-clamp-3">{{ meal.strInstructions }}</p>
        <div class="pt-4 flex items-center justify-between">
            <YoutubeButton :href="meal.strYoutube">Youtube</YoutubeButton>

            <router-link to="/">
                View
            </router-link>
        </div>
    </div>

</template>

<script setup>
import YoutubeButton from './YoutubeButton.vue';

const { meal } = defineProps({
    meal: {
        required: true,
        type: Object
    }
})
</script>