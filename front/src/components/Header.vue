<script setup lang="ts">
import { ref } from 'vue'

import IconPage from "../assets/icon.png"

const headerOptions = ref([
    {
        label: "Home",
        link: "/",
    },
    {
        label: "Food",
        link: "/",
    },
    {
        label: "Map",
        link: "/",
    },
    {
        label: "About",
        link: "/",
    },
    {
        label: "Contact",
        link: "/",
    }
])
</script>

<template>
    <header class="flex items-center justify-between w-full h-40">
        <img :src="IconPage" alt="Icon Hambruger page" class="w-40 h-40 ml-16">

        <ul class="flex gap-24">
            <li v-for="(option, i) in headerOptions" :key="i" class="text-header">
                <a :href="option.link"> {{ option.label }} </a>
            </li>
        </ul>

        <hgroup class="flex gap-8 mr-24">
            <button class="text-header">Sign Up</button>
            <button class="bg-red-color rounded-2xl h-8 px-6 text-header text-center">Log In</button>
        </hgroup>
    </header>
</template>

<style scoped>
    .text-header{
        @apply text-white capitalize text-xl font-bold;
    }
</style>
