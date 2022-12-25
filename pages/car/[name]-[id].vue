<script setup>
const route = useRoute()
const { toTitleCase } = useUtils()
const { cars } = useCars()
const { name, id } = route.params
useHead({
  title: toTitleCase(name)
})

const getCarData = computed(() => {
  return cars.find(it => it.id === parseInt(id))
})

if (!getCarData.value) { s }

definePageMeta({
  layout: 'custom'
})
</script>

<template>
  <div>
    <CarDetailHero :car="getCarData" />
    <CarDetailAttributes :features="getCarData.features" />
    <CarDetailDescription :description="getCarData.description" />
    <CarDetailContent />
  </div>
</template>