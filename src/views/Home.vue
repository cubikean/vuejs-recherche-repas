<template>
    <div class="flex flex-col items-center p-8 justify-center">
       

        
    </div>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue';
import store from '../store'
import axiosClient from '../axiosClient.js';


const ingredients = ref([]);


onMounted(async () =>{
    const response = await axiosClient.get('/list.php?i=list')
    console.log(response.data)
    ingredients.value = response.data
})

</script>