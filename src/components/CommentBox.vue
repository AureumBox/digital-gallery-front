<script lang="ts">
import { Form } from '@primevue/forms';
import { Button, Message } from 'primevue';
import { defineComponent } from 'vue';

export default defineComponent({
    components: {
        Form,
        Text,
        Message,
        Button
    }
})
</script>

<template>
    <Form v-slot="$form" class="commentBox">
        <div class="flex flex-col gap-1">
            <Textarea name="address" rows="5" class="textBox" />
            <Message v-if="$form.address?.invalid" severity="error" size="small" variant="simple">{{
                $form.address.error?.message }}</Message>
        </div>
        <Button type="submit" severity="primary" label="Enviar" class="sendBtn" />
    </Form>
</template>

<style scoped>
.commentBox {
    width: 100%;
}

.textBox {
    resize: none;
    width: 100%;
}

.textBox:focus {
    outline: none;
    box-shadow: 0 0 5px var(--p-primary-600)
}
</style>