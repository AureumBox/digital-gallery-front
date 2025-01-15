<script setup lang="ts">
import SignupForm from '@/components/SignupForm.vue'
import router from '@/router';
import { Button } from 'primevue';
</script>

<template>
    <main>
        <SignupForm />
    </main>
    <Button type="button" variant="link" label="Iniciar sesión" @click="router.push('/login')" />
</template>
