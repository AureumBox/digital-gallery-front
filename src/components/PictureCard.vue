<script lang="ts">
import { defineComponent } from 'vue';
import type { PropType } from 'vue';
import { Button, Card, Divider, Image } from 'primevue';
import CommentsSection from './CommentsSection.vue';
import type { Picture } from '@/views/GalleryView.vue';

export default defineComponent({
    components: {
        Card,
        Button,
        CommentsSection,
        Image
    },
    props: {
        picture: {
            type: Object as PropType<Picture>, // Use the Picture type defined earlier
            required: true
        }
    },
    data() {
        return {
            liked: false,
            showComments: false
        }
    },
    methods: {
        async toggleLike() {
            this.liked = !this.liked;
            const likeCount = this.liked ? this.picture.likes + 1 : this.picture.likes - 1;

            // Send like to the API
            try {
                await fetch(`https://your-api-url/likes`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({ pictureId: this.picture.id, liked: this.liked }),
                });
                this.picture.likes = likeCount; // Update local state
            } catch (error) {
                console.error("Error liking the picture:", error);
            }
        },
        toggleComments() {
            this.showComments = !this.showComments;
        }
    },
})

</script>

<template>
    <Card class="pictureCard">
        <template #content>
            <div>
                <Image class="picture" :src="picture.picture" width="100%" preview />
            </div>
            <div class="interactions">
                <Button icon="pi pi-comments" rounded variant="text" @click="toggleComments" />
                <Button :label="picture.likes.toString()" :icon="liked ? 'pi pi-heart-fill' : 'pi pi-heart'" rounded
                    variant="text" @click="toggleLike" />
            </div>
            <Divider />
            <div v-if="showComments">
                <CommentsSection :comments="picture.comments" :pictureId="picture.id" />
            </div>
        </template>
    </Card>
</template>

<style scoped>
.pictureCard {
    display: flex;
    justify-content: center;
    margin: 10px;
    width: 30%;
}


.interactions {
    text-align: right;
}

.picture {
    text-align: center;
    max-width: 100%;
    height: auto;
}
</style>