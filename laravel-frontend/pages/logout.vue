<template>
  <div>Logging Out...</div>
</template>
<script setup>
import axios from 'axios';
import { useRouter } from 'vue-router'

        await axios.post('/logout'); 
        const router = useRouter();
        router.push('/login');
</script>
