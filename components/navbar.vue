<template>
  <div class="absolute top-0 z-10 w-full bg-gray-300">
    <ul
      class="flex space-x-8 justify-center items-center font-bold text-2xl py-4"
    >
      <li class="transform hover:scale-110 duration-500 ease-in-out">
        <nuxt-link to="/">Basics</nuxt-link>
      </li>
      <li class="transform hover:scale-105 duration-300 ease-in-out">
        <nuxt-link to="/intermediate">Intermediate</nuxt-link>
      </li>
      <li class="transform hover:scale-105 duration-300 ease-in-out">
        <nuxt-link to="/vue-cavnas">Vue Canvas</nuxt-link>
      </li>
      <li class="transform hover:scale-105 duration-300 ease-in-out">
        <nuxt-link to="/animation">Animation</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {}
</script>

<style></style>
