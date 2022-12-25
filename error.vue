<script setup>
const error = useError()
const handleError = () => {
  // navigateTo('/')
  clearError({
    redirect: '/'
  })
}
</script>

<template>
  <div
    class="flex h-screen justify-center items-center flex-col bg-cover bg-no-repeat bg-[url(https://images.unsplash.com/photo-1570042707390-2e011141ab78?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1332&q=80)]">
    <h1 class="text-9xl text-white">{{ error.statusCode }}</h1>
    <p class="mt-7 text-4xl text-white">
      {{ error.message }}
    </p>
    <button class="rounded mt-7 text-2xl bg-blue-400 px-7 py-4 text-white" @click="handleError">Go Back</button>
  </div>
</template>