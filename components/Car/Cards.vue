<script setup>
const { cars } = useCars()

const favorite = useLocalStorage("favorite", {})

const handleFavorite = (id) => {
  if (id in favorite.value) {
    delete favorite.value[id]
  } else {
    favorite.value = {
      ...favorite.value,
      [id]: true
    }
  }
}


</script>

<template>
  <div class="w-full">
    <CarCard
      @favor="handleFavorite"
      v-for="car in cars"
      :key="car.id"
      :car="car"
      :favored="car.id in favorite"
    ></CarCard>
    <!-- <ClientOnly>
      <CarCard
        @favor="handleFavorite"
        v-for="car in cars"
        :key="car.id"
        :car="car"
        :favored="car.id in favorite"
      ></CarCard>
    </ClientOnly> -->

  </div>
</template>
