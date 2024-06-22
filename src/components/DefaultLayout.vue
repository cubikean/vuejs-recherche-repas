<template>
    <div class="bg-gray-100 h-full">
    <Narvbar />
    <main>
      <router-view />
    </main>
  </div>
</template>

<script setup>
    import Narvbar from '../components/Narvbar.vue';
</script>