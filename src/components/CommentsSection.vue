<script lang="ts">
import { defineComponent, ref } from 'vue';
import type { PropType } from 'vue';
import Comment from './Comment.vue';
import CommentBox from './CommentBox.vue';

export default defineComponent({
    components: {
        Comment,
        CommentBox
    },
    props: {
        comments: {
            type: Array as PropType<any>, // Adjust the type based on your comment structure
            required: true
        },
        pictureId: {
            type: String,
            required: true
        }
    },
    setup(props) {
        const commentsList = ref(props.comments); // Local state for comments

        // Function to add a new comment
        const addComment = (newComment: string) => {
            // Here you would typically send the new comment to your API
            // For demonstration, we'll just add it to the local state
            commentsList.value.push({
                id: Date.now().toString(), // Generate a simple ID for the comment
                text: newComment,
                // Add other properties as needed (e.g., author, timestamp)
            });

            // Optionally, send the new comment to the API
            // await fetch(`https://your-api-url/comments`, {
            //     method: 'POST',
            //     headers: {
            //         'Content-Type': 'application/json',
            //     },
            //     body: JSON.stringify({ pictureId: props.pictureId, text: newComment }),
            // });
        };

        return {
            commentsList,
            addComment
        };
    }
});
</script>

<template>
    <div>
        <CommentBox @submit="addComment" />
        <div v-for="comment in commentsList" :key="comment.id">
            <Comment :comment="comment" />
        </div>
    </div>
</template>

<style scoped>
/* Add any styles you need for the comments section */
</style>