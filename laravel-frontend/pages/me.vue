<template>
  <div>
    <p><strong>User Name:</strong> {{ user.name }}</p>
    <p><strong>User Email:</strong> {{ user.email }}</p>
  </div>
</template>

<script setup>
import axios from 'axios';

const user = ref({
  name: '',
  email: ''
});

const response = await axios.get('/user');
user.value = response.data;
</script>

