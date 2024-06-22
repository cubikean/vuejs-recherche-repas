<template>

    <header class="bg-white shadow h-16 flex justify-between items-center">
        <router-link :to="{ name: 'home' }">
            Home
        </router-link>
        <div class="flex justify-center items-center h-full">
            <router-link :to="{ name: 'byName' }" class="px-2 flex items-center h-full hover:bg-purple-50">
                Search Meals
            </router-link>
            <router-link :to="{ name: 'byLetter' }" class="px-2 flex items-center h-full hover:bg-purple-50">
                Search By letter
            </router-link>
            <router-link :to="{ name: 'ingredients' }" class="px-2 flex items-center h-full hover:bg-purple-50">
                Search By ingredients
            </router-link>
        </div>
    </header>

</template>