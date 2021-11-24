<template>
  <div class="bg-white text-gray-900 dark:bg-gray-900 dark:text-white">
    <navbar/>
    <main class="container">
      <Nuxt />
    </main>
  </div>
</template>

<style lang="postcss">
  html,
  body{
    height: 100%;
    width: 100%;
    @apply bg-white text-gray-900 dark:bg-gray-900 dark:text-white;
  }
</style>