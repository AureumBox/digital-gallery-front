<script lang="ts">
import { Form } from '@primevue/forms';
import { Button, InputText, Message } from 'primevue';
import { defineComponent } from 'vue';

export default defineComponent({
    components: {
        Form,
        Button,
        InputText,
    },
})
</script>

<template>
    <p>sdfg</p>
    <Form>
        <div>
            <InputText name="username" type="text" placeholder="Username" />
        </div>
        <div>
            <InputText name="email" type="text" placeholder="Email" />
        </div>
        <Button type="submit" label="Submit" />
    </Form>

</template>