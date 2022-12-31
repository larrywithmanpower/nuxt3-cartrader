<script setup>
const { cars } = useCars()

const favorite = useLocalStorage('favorite', {}) // init localStorage for saving

const handleFavorite = (id) => {
  if (id in favorite.value) {
    delete favorite.value[id]
  } else {
    favorite.value = {
      ...favorite.value, // for keep existing data
      [id]: true // new data
    }
  }
}
</script>

<template>
  <div class="w-full">
    <CarCard v-for="(car) in cars" :key="car.id" :car="car" @favor="handleFavorite" :favored="car.id in favorite" />
  </div>
</template>