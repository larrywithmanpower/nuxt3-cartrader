<script setup>
import heartFilled from "~/assets/heartFilled.png"
import heartOutline from "~/assets/heartOutline.png"

const props = defineProps({
  car: {
    type: Object,
    default: () => { }
  },
  favored: Boolean
})

const emit = defineEmits(['favor']) // using emit in nuxt 3
</script>

<template>
  <div>
    <div class="shadow border w-full overflow-hidden mb-5 cursor-pointer h-[200px]">
      <div class="flex h-full relative">
        <img :src="favored ? heartFilled : heartOutline" alt="" class="absolute w-7 right-5 top-2 z-20"
          @click="emit('favor', car.id)">
        <img :src="car.url" alt="" class="w-[300px] h-full" @click="navigateTo(`/car/${car.name}-${car.id}`)" />
        <div class="p-4 flex flex-col">
          <h1 class="text-2xl text-blue-700">{{ car.name }}</h1>
          <p class="text-gray-700">{{ car.description }}</p>
          <h1 class="mt-auto text-xl">${{ car.price }}</h1>
        </div>
      </div>
    </div>
  </div>
</template>