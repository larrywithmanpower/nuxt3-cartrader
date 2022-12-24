<script setup>
const route = useRoute()
const firstText = route.params.make ? toTitleCase(route.params.make) : 'Cars'
const { toTitleCase } = useUtils()

useHead({
  title: `${firstText} in ${toTitleCase(route.params.city)}`
})

definePageMeta({
  layout: 'custom'
})

</script>

<template>
  <div>
    <div class="mt-32 flex">
      <CarSideBar />
      <NuxtPage />
    </div>
  </div>
</template>