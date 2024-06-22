<template>
    <div class="p-8">
        <input type="text" class="rounded border-2 border-gray-200 w-full" placeholder="Search" v-model="keyword" @keyup.enter="searchMeals" />
    </div>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-3 p-8">
        <MealItem v-for="meal in meals" :key="meal.idMeal" :meal="meal"/>
    </div>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue';
import store from '../store';
import { useRoute } from 'vue-router';
import MealItem from '../components/MealItem.vue';

const route = useRoute();
const keyword = ref('')
const meals = computed(() => store.state.searchedMeals)

function searchMeals() {
    if (keyword.value.trim() === '') {
        console.warn('Le champ de recherche est vide.');
        return;
    }
    console.log(keyword.value);
    store.dispatch('searchMeals', keyword.value);
}


onMounted(() =>{
    keyword.value = route.params.name
    if( keyword.value){
        searchMeals()
    }
})
</script>