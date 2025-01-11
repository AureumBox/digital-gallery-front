<script lang="ts">
import { Form } from '@primevue/forms';
import { Button, Card, Divider, Image, InputText, Message, Panel } from 'primevue';
import { defineComponent } from 'vue';
import CommentsSection from './CommentsSection.vue';

export default defineComponent({
    components: {
        Card,
        Button,
        CommentsSection,
        Image
    },
    data() {
        return {
            liked: false as boolean,
            likes: "0" as string,
            showComments: false as boolean
        }
    },
    methods: {
        toggleLike() {
            this.liked = !this.liked;
        },
        toggleComments() {
            this.showComments = !this.showComments;
        }
    },
})

</script>

<template>
    <Card class="pictureCard"><template #content>
            <div>
                <Image class="picture" src="src\assets\pic.png" width="100%" preview />
            </div>
            <div class="interactions">
                <Button icon="pi pi-comments" rounded variant="text" @click="toggleComments" />
                <Button :label="likes" :icon="liked ? 'pi pi-heart-fill' : 'pi pi-heart'" rounded variant="text"
                    @click="toggleLike" />
            </div>
            <Divider />
            <div v-if="showComments">
                <CommentsSection></CommentsSection>
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
