<template>
  <nav class="bg-white border-b dark:border-gray-700 lg:fixe lg:w-full lg:top-0 lg:left-0 lg:z-40 dark:bg-gray-900">
    <div class="container px-4 py-5 mx-auto space-y-4 lg:space-y-0 lg:flex lg:items-center lg:justify-between lg:space-x-10">
      <div class="flex justify-between">
        <nuxt-link to="/">
          <div class="flex items-center">
            <p class="text-xl ml-2 dark:text-white hover:text-green-300 dark:hover:text-green-300 duration-300"><strong>AA</strong></p>
          </div>
        </nuxt-link>
        <div class="flex items-center space-x-2 lg:hidden"><button @click="MobileMenu()" class="p-1 rounded-md hover:bg-gray-100 dark:hover:bg-gray-800 focus:bg-gray-100 dark:focus:bg-gray-800 focus:outline-none"><svg viewBox="0 0 20 20" fill="currentColor" class="w-6 h-6 text-gray-700 dark:text-gray-300"><path fill-rule="evenodd" d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z" clip-rule="evenodd"></path></svg></button></div>
      </div>
      <div class="hidden lg:hidden flex flex-col space-y-4" style="display:none;" id="mobilenav">
        <div class="flex flex-col space-y-3 lg:space-y-0 lg:flex-row lg:space-x-6 xl:space-x-8 lg:items-center">
          <nuxt-link to="/" class="py-2 px-4 text-gray-500 dark:text-gray-200 hover:text-gray-800 rounded" exact-active-class="bg-gray-300 dark:bg-gray-700">Home</nuxt-link>
          <nuxt-link to="/about" class="py-2 px-4 text-gray-500 dark:text-gray-200 hover:text-gray-800 rounded" exact-active-class="bg-gray-300 dark:bg-gray-700">About</nuxt-link>
        </div>
      </div>
      <div class="hidden lg:flex lg:flex-row lg:items-center lg:justify-between lg:flex-1 lg:space-x-2">
        <div class="flex flex-col space-y-3 lg:space-y-0 lg:flex-row lg:space-x-6 xl:space-x-8 lg:items-center">
          <nuxt-link to="/" class="dark:text-white hover:text-green-400 dark:hover:text-green-400 duration-300" exact-active-class="font-bold text-green-400 dark:text-green-400 border-b-2 border-green-500 duration-300">Home</nuxt-link>
          <nuxt-link to="/about" class="dark:text-white hover:text-green-400 dark:hover:text-green-400 duration-300" exact-active-class="font-bold text-green-400 dark:text-green-400 border-b-2 border-green-500 duration-300">About</nuxt-link>
          <select v-model="$colorMode.preference">
            <option value="system">System</option>
            <option value="light">Light</option>
            <option value="dark">Dark</option>
            <option value="sepia">Sepia</option>
          </select>
        </div>
      </div>
    </div>
  </nav>
</template>

<style lang="postcss">
  select{
    @apply text-gray-900
  }
</style>

<script>
export default {
  name:'navbar',
  methods: {
  MobileMenu: function(e) {
    if(document.getElementById('mobilenav').style.display === "block"){
      document.getElementById('mobilenav').style.display = "none";
    }else{
      document.getElementById('mobilenav').style.display = "block";
    }
  }
}
}
</script>