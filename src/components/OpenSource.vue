<script lang="ts" setup>
import { onMounted, reactive, ref } from "vue";
import VanillaTilt from "vanilla-tilt";

const props = defineProps(["title", "desc", "start", "end"]);

const container = ref<HTMLElement>();

onMounted(() => {
    if (container.value) {
        VanillaTilt.init(container.value, {
            reverse: true,
            max: 8,
            speed: 1000,
        });
    }
});
</script>

<template>
    <div class="container" ref="container">
        <div class="text">
            <h4
                :style="{
                    background:
                        'linear-gradient(90deg, ' +
                        props.start +
                        ' 0%, ' +
                        props.end +
                        ' 100%)',
                }"
            >
                {{ props.title }}
            </h4>
            <p>{{ props.desc }}</p>
        </div>
        <div class="star">
            <i class="bi bi-star"></i>
            <p>1,234</p>
        </div>
    </div>
</template>

<style scoped>
.container {
    border: 3px dashed var(--light);
    padding: 15px 25px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-radius: 15px;
}

.text h4 {
    color: transparent;
    background-clip: text !important;
    margin: 0;
}

.text p {
    margin: 0;
}

.star {
    display: flex;
    align-items: center;
}
</style>
