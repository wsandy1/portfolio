<script setup lang="ts">
import { PropType, ref } from "vue";

type Featured = {
    title: string;
    date: string;
    thumbnail: string;
}[];

const props = defineProps({
    featured: Array as PropType<Featured>,
});

const bg = ref();

function setBg(thumbnail: string | null) {
    bg.value = thumbnail;
}
</script>

<template>
    <div class="wrapper">
        <div class="list" @mouseleave="setBg(null)">
            <h1
                v-for="item in props.featured"
                @mouseover="setBg(item.thumbnail)"
            >
                {{ item.title }}
            </h1>
        </div>
        <div
            class="image"
            :style="[bg !== null ? { backgroundImage: 'url(' + bg + ')' } : {}]"
        ></div>
    </div>
</template>

<style>
h1 {
    transform: skewX(0deg);
    transition: transform 0.3s;
    line-height: 1;
}

h1:hover {
    transform: skewX(-20deg);
}

.wrapper {
    display: flex;
    padding: 0 100px;
}

.list {
    width: 50%;
    text-align: right;
}

.image {
    flex-grow: 1;
    align-self: stretch;
    border-radius: 30px;
    margin-left: 100px;
}

/* we will explain what these classes do next! */
.v-enter-active,
.v-leave-active {
    transition: opacity 0.8s ease;
}

.v-enter-from,
.v-leave-to {
    opacity: 0;
}
</style>
