<script setup lang="ts">
import LoginForm from '@/components/LoginForm.vue'
import router from '@/router';
import { Button } from 'primevue';
</script>

<template>
    <main>
        <LoginForm />
    </main>
    <Button type="button" variant="link" label="Registro" @click="router.push('/signup')" />
</template>
