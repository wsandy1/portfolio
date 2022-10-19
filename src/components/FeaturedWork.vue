<script setup lang="ts">
import type { PropType } from "vue";

type Featured = {
    title: string;
    date: string;
    thumbnail: string;
}[];

const props = defineProps({
    featured: {
        type: Array as PropType<Featured>,
        required: true,
    },
});
</script>

<template>
    <div class="wrapper">
        <div class="list">
            <h1 v-for="item in props.featured">
                {{ item.title }}
            </h1>
        </div>
        <div class="project-images">
            <div
                class="image"
                v-for="item in props.featured"
                :style="{
                    background: 'url(' + item.thumbnail + ')',
                }"
            ></div>
        </div>
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

.project-images {
    flex-grow: 1;
    position: relative;
    overflow: hidden;
    border-radius: 30px;
}

.image {
    position: absolute;
    inset: 0;
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
