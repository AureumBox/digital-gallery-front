<script lang="ts">
import { Form } from '@primevue/forms';
import { Button, Card, Divider, Image, InputText, Message, Panel } from 'primevue';
import { defineComponent } from 'vue';
import Comment from './Comment.vue';

export default defineComponent({
    components: {
        Card,
        Button,
        Comment,
        Image
    },
    data() {
        return {
            liked: false as boolean,
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
            <div>
                <Button :icon="liked ? 'pi pi-heart-fill' : 'pi pi-heart'" rounded variant="text" @click="toggleLike" />
                <Button icon="pi pi-comments" rounded variant="text" @click="toggleComments" />
            </div>
            <Divider />
            <div v-if="showComments">
                <Comment v-for="a in 4" />
            </div>
        </template>
    </Card>
</template>

<style scoped>
.pictureCard {
    display: flex;
    justify-content: center;
    margin: 10px;
    width: 33%;
}

.picture {
    text-align: center;
    max-width: 100%;
    height: auto;
}
</style>
