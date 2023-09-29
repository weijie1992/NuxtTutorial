<script setup>
const route = useRoute()
useHead({
    title: route.params.name
})
</script>

<template>
    <div>
        <NavBar />
        <div class="mx-auto mt-4 max-w-7xl space-y-4 px-4 xs:px-9 sm:px10 lg:px-16 pb-16 w-3/5">
            <CarDetailHero />
            <CarDetailAttributes />
            <CarDetailDescription />
            <CarDetailContact />
        </div>

    </div>
</template>
