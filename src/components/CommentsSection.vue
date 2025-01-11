<script lang="ts">
import { Form } from '@primevue/forms';
import { Button, Message } from 'primevue';
import { defineComponent } from 'vue';
import Comment from './Comment.vue';
import CommentBox from './CommentBox.vue';

export default defineComponent({
    components: {
        Comment,
        CommentBox
    }
})
</script>

<template>
    <CommentBox />
    <Comment v-for="a in 4" />
</template>

<style scoped></style>