<template>
    <div class="flex flex-col gap-2 mt-3">
        <div v-for="ingredient in ingredients" :key="ingredient.id">
            <router-link :to="{name: 'byIngredient', params: {ingredient: ingredient.strIngredient}}" :key="ingredient.idIngredient">
                <p>{{ ingredient.strIngredient }}</p>
            </router-link>
        </div>    
    </div>

</template>

<script setup>
import { computed, onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import axiosClient from '../axiosClient';

const route = useRoute();
const ingredients = ref([]);

onMounted(() =>{
    axiosClient.get('list.php?i=list')
    .then(({data})=>{
        ingredients.value = data.meals
    })
})

</script>