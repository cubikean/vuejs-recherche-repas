<template>
    <div class="flex gap-2 mt-3">
            <router-link :to="{name: 'byLetter', params: {letter}}" v-for="letter of letters" :key="letter">
                {{ letter }}
            </router-link>
        </div>

        <MealItem v-for="meal in meals" :key="meal.idMeal" :meal="meal"/>
            
</template>

<script setup>
import { computed, onMounted, watch } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import MealItem from '../components/MealItem.vue';

const route = useRoute();
const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split("");
const meals = computed(() => store.state.mealsByLetter)

function searchMealsByLetter(){
    store.dispatch('searchMealsByLetter', route.params.letter)
}

watch(route, ()=>{
    searchMealsByLetter()
})
onMounted(() =>{
    searchMealsByLetter()
})

</script>