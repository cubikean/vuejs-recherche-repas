<template>
    <div class="flex flex-col items-center p-8 justify-center">
        <input type="text" class="rounded border-2 border-gray-200 w-full" placeholder="Search">

        <div class="flex gap-2 mt-3">
            <router-link :to="{name: 'byLetter', params: {letter}}" v-for="letter of letters.split('')" :key="letter">
                {{ letter }}
            </router-link>
        </div>
        {{ ingredients }}
    </div>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue';
import store from '../store'
import axiosClient from '../axiosClient.js';


const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
const ingredients = ref([]);


onMounted(async () =>{
    const response = await axiosClient.get('/list.php?i=list')
    console.log(response.data)
    ingredients.value = response.data
})

</script>