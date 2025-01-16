<script setup lang="ts">
import { ref, onMounted } from 'vue';
import PictureCard from '@/components/PictureCard.vue';

export interface Picture {
    createdAt: string;
    name: string;
    picture: string;
    likes: number;
    comments: Array<{ username: string, comment: string }>;
    id: string;
}

const pictures = ref<Picture[]>([]); // Define the type of the pictures array

// Function to fetch pictures from the API
const fetchPictures = async () => {
    try {
        const response = await fetch('https://6788e7492c874e66b7d6ca18.mockapi.io/api/posts'); // Replace with your actual API URL
        if (!response.ok) {
            throw new Error('Failed to fetch pictures');
        }
        pictures.value = await response.json(); // Assuming the response is an array of picture objects
    } catch (error) {
        console.error(error);
    }
};

// Fetch pictures when the component is mounted
onMounted(fetchPictures);
</script>

<template>
    <main class="bento-container">
        <PictureCard v-for="picture in pictures" :key="picture.id" :picture="picture" />
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