<script setup lang="ts">
import { ref } from "vue"
import axios from "axios"
import { useRouter } from 'vue-router'

definePageMeta({
  layout: "centered",
});
interface loginForm {
  email: string,
  password: string,
}
const datos = ref({
  email: "",
  password: "",
})
const router = useRouter();

async function login(datos: loginForm) {
  let responseRegister
  try {
    responseRegister = await axios.post("http://localhost/api/login", datos)
    router.push('/me');
  } 
  catch (e) {
    console.log(`Ha ocurrido un error: ${e}`)
  }
}
</script>
<template>
  <div class="login">
    <h1>Login</h1>
    <form @submit.prevent="() => login(datos)">
      <label>
        <div>Email</div>
        <input v-model="datos.email" type="text" />
      </label>

      <label>
        <div>Password</div>
        <input v-model="datos.password" type="password" />
      </label>
      <button class="btn">Login</button>
    </form>

    <p>
      Don't have an account?
      <NuxtLink class="underline text-lime-600" to="/register">Register now!</NuxtLink>
    </p>
  </div>
</template>
