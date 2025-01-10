<script lang="ts">
import router from '@/router';
import { Form } from '@primevue/forms';
import { Button, InputText, Message } from 'primevue';
import { defineComponent } from 'vue';

export default defineComponent({
    components: {
        Form,
        Button,
        InputText,
    },
    methods: {
        onFormSubmit() {
            console.log("ki")
            router.push('/')
        }
    }
})

</script>

<template>
    <div class="form-container">
        <Form @submit.stop.prevent="onFormSubmit">
            <div class="form-field">
                <InputText name="username" type="text" placeholder="Username" />
            </div>
            <div class="form-field">
                <InputText name="email" type="text" placeholder="Email" />
            </div>
            <Button type="submit" label="Submit" class="submit-button" />
        </Form>
    </div>
</template>

<style scoped>
.form-field {
    margin-bottom: 15px;
}

.submit-button {
    width: 100%;
}

.form-container {
    display: flex;
    align-items: self-start;
    justify-content: center;
}
</style>
