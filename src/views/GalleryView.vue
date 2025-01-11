<!-- MainComponent.vue -->
<script setup lang="ts">
import PictureCard from '@/components/PictureCard.vue';
</script>

<template>
    <main class="bento-container">
        <PictureCard />
        <PictureCard />
        <PictureCard />
        <PictureCard />
        <PictureCard />
    </main>
</template>

<style>
.bento-container {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: flex-start;
    gap: 2px;
}
</style>