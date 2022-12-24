<script setup>
const route = useRoute()
const { toTitleCase } = useUtils()
useHead({
  title: toTitleCase(route.params.name)
})


definePageMeta({
  layout: 'custom'
})
</script>

<template>
  <div>
    <CarDetailHero />
    <CarDetailAttributes />
    <CarDetailDescription />
    <CarDetailContent />
  </div>
</template>