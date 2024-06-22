<template>
    <div>
        <h1 class="text-5xl">{{ meal.strMeal }}</h1>
       <img :src="meal.strMealThumb" :alt="meal.strMeal">
    </div>
    <div>
        <h2 class="text-3xl">ingredients</h2>
        <ul>
            <template v-for="(el,ind) of new Array(20)">
                <li v-if="meal[`strIngredient${ind + 1}`]">
                    {{ ind + 1 }}. {{ meal[`strIngredient${ind + 1}`] }}
                </li>
            </template>
        </ul>
    </div>
    <div>
        <h2>Links</h2>
        <YoutubeButton :href="meal.strYoutube">Youtube</YoutubeButton>
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import axiosClient from '../axiosClient';
import YoutubeButton from '../components/YoutubeButton.vue';

const route = useRoute()
const meal = ref({})

onMounted(() => {
    axiosClient.get(`lookup.php?i=${route.params.id}`)
        .then(({ data }) => {
            meal.value = data.meals[0] || {}
        })
})
</script>