<template>
    <main class="flex items-center gap-2 relative">
        <h1>BIGBURGER</h1>
        
        <template v-for="(burger, i) in optionsBurgers">
            <img :src="burger.img" :alt="`hamburger ${i}`" :class="classPositionBurger(i)">
        </template>

        <button class="btn-move left-8" @click="onChangePositionRight()">
            <span class="material-icons pl-2">arrow_back_ios</span>
        </button>
        <button class="btn-move right-8" @click="onChangePositionLeft()">
            <span class="material-icons">arrow_forward_ios</span>
        </button>
    </main>
</template>

<script setup lang="ts">
import { ref } from "vue"

import BgOne from "@/assets/burgers/Bg-1.png"
import BgTwo from "@/assets/burgers/Bg-2.png"
import BgThree from "@/assets/burgers/Bg-3.png"
import BgFour from "@/assets/burgers/Bg-4.png"
import BgFive from "@/assets/burgers/Bg-5.png"

const optionsBurgers = ref([
    {
        text: "BIGBURGER",
        img: BgOne,
        link: "",
    },
    {
        text: "BIGBURGER",
        img: BgTwo,
        link: "",
    },
    {
        text: "BIGBURGER",
        img: BgThree,
        link: "",
    },
    {
        text: "BIGBURGER",
        img: BgFour,
        link: "",
    },
    {
        text: "BIGBURGER",
        img: BgFive,
        link: "",
    },
])

function classPositionBurger(pos: number) {
    pos += 1;

    if (pos === 3) {
        return "bg-selected"
    } else if (pos % 2 === 0) {
        return "bg-second"
    } else {
        return "bg-third"
    }
}

function onChangePositionLeft() {
    const lastOption = optionsBurgers.value.pop()
    optionsBurgers.value.unshift(lastOption!)
}

function onChangePositionRight() {
    const lastOption = optionsBurgers.value.shift()
    optionsBurgers.value.push(lastOption!)
}
</script>

<style scoped>
.btn-move {
    @apply fixed m-auto top-0 bottom-0 flex items-center justify-center text-white rounded-full w-12 h-12 bg-[#fff5]
}

.bg-selected {
    @apply w-[560px] h-[560px] object-contain aspect-[3/2];
}

.bg-second {
    @apply w-[280px] h-[280px] object-contain aspect-[3/2];
}

.bg-third {
    @apply w-[200px] h-[200px] object-contain;
}
</style>