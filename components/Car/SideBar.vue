<script setup>
const modal = ref({
  make: false,
  location: false,
  price: false
})

const city = ref('')
const updateModal = (key) => {
  modal.value[key] = !modal.value[key]
}
const route = useRoute()
const { make } = route.params

const onChangeLocation = () => {
  if (!city.value) return
  if (!isNaN(parseInt(city.value))) {
    throw createError({
      statusCode: 400,
      message: 'Invalid city format.'
    })
  }
  updateModal('location')
  navigateTo(`/city/${city.value}/car/${make}`)
}
</script>

<template>
  <div class="shadow border w-64 mr-10 h-[190px]">
    <div class="relative p-5 flex justify-between cursor-pointer border-b">
      <h3>Location</h3>
      <h3 @click="updateModal('location')" class="text-blue-400 capitalize">
        {{ route.params.city }}
      </h3>
      <!-- Modal -->
      <div v-if="modal.location" class="absolute border shadow left-56 p-5 top-1 -m-1 bg-white">
        <input type="text" class="border p-1 rounded" v-model="city">
        <button @click="onChangeLocation" class="bg-blue-400 w-full mt-2 rounded text-white p-1">Apply</button>
      </div>
    </div>
    <div class="relative p-5 flex justify-between cursor-pointer border-b">
      <h3>Make</h3>
      <h3 class="text-blue-400 capitalize">Toyota</h3>
    </div>
    <div class="relative p-5 flex justify-between cursor-pointer border-b">
      <h3>Price</h3>
      <h3 class="text-blue-400 capitalize">Any</h3>
    </div>
  </div>
</template>