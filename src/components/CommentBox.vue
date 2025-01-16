<script lang="ts">
import { defineComponent, ref } from 'vue';
import { Button, Textarea } from 'primevue';
import { Form } from '@primevue/forms';

export default defineComponent({
    components: {
        Form,
        Button,
        Textarea
    },
    setup(_, { emit }) {
        const commentText = ref('');

        const submitComment = () => {
            if (commentText.value.trim()) {
                emit('submit', commentText.value); // Emit the new comment
                commentText.value = ''; // Clear the input
            }
        };

        return {
            commentText,
            submitComment
        };
    }
});
</script>

<template>
    <Form @submit.prevent="submitComment">
        <div class="flex flex-col gap-1">
            <Textarea v-model="commentText" rows="3" placeholder="Write a comment..." />
            <Button type="submit" label="Send" />
        </div>
    </Form>
</template>

<style scoped>
/* Add any styles you need for the comment box */
</style>