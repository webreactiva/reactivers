<template>
    <header class="flex justify-between bg-blue-900">
        <nuxt-link to="/" class="m-4">
            <div class="flex flex-col">
                <h1 class="text-3xl text-white font-bold">Reactivers</h1>
                <h1 class="text-mc text-white font-bold">Directorio developers</h1>
            </div>
        </nuxt-link>
        <div class="min-h-full flex">
            <nuxt-link to="/about" class="mx-3 my-1 px-2 md:px-6 py-8 bg-blue-600 font-bold text-gray-200">¿Qué es esto?</nuxt-link>
            <nuxt-link to="/proceso-alta" class="mx-3 my-1 px-2 md:px-6 py-8 bg-blue-600 font-bold text-gray-200">Añadir mi ficha</nuxt-link>
        </div>
    </header> 
</template>