<script lang="ts">
import router from '@/router';
import { Form } from '@primevue/forms';
import { Button, InputText } from 'primevue';
import { defineComponent } from 'vue';

export default defineComponent({
    components: {
        Form,
        Button,
        InputText,
    },
    methods: {
        async onFormSubmit() {
            const formData = {
                email: (this.$refs.email as HTMLInputElement).value,
                password: (this.$refs.password as HTMLInputElement).value
            }

            try {
                console.log(import.meta.env.VUE_APP_BACKEND)
                const response = await fetch('https://6788e7492c874e66b7d6ca18.mockapi.io/api/signup', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify(formData),
                });

                if (!response.ok) {
                    throw new Error('Error en la red');
                }

                const data = await response.json();
                console.log("Respuesta del servidor:", data);
                alert("Registrado")
                await router.push('/home');
                window.location.reload()
            } catch (error) {
                console.error("Error al enviar el formulario:", error);
            }
        }
    }
});
</script>

<template>
    <div class="form-container">
        <Form @submit="onFormSubmit">
            <div class="form-field">
                <InputText name="email" type="email" placeholder="Email" ref="email" />
            </div>
            <div class="form-field">
                <InputText name="password" type="password" placeholder="Password" ref="password" />
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