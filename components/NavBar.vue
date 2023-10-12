<script setup>
const user = useSupabaseUser()

const supabase = useSupabaseClient()
const logout = async () => {
  console.log("🚀 ~ file: NavBar.vue:7 ~ logout ~ logout:")
  const { error } = await supabase.auth.signOut()
  if (error) console.log(error)
  navigateTo('/login')
}
</script>
<template>
  <header class="sticky top-0 z-50 flex justify-between items-center space-x-1 border-b bg-white p-4 shadow-md">
    <NuxtLink
      to="/"
      class="text-3xl font-mono"
    >
      cartrader
    </NuxtLink>
    <div
      v-if="user"
      class="flex"
    >
      <NuxtLink
        to="/profile/listings"
        class="mr-5"
      >profile</NuxtLink>
      <p
        class="cursor-pointer"
        @click="logout"
      >Logout</p>
    </div>
    <div v-else>
      <NuxtLink to="/login">Login</NuxtLink>
    </div>
  </header>
</template>

