<template>
<div>
  <nav class="bg-blue-800 dark:bg-black">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        <div class="flex items-center">
          <div class="flex-shrink-0 text-white text-2xl font-semibold">
            LOGO
          </div>
          <div class="hidden md:block">
            <div class="ml-10 flex items-baseline space-x-10">
              <a href="#" class="text-gray-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium">Menu</a>

              <a href="#" class="text-gray-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium">Menu</a>

              <a href="#" class="text-gray-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium">Menu</a>

              <a href="#" class="text-gray-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium">Menu</a>

            </div>
          </div>
        </div>
        <div>
          <div class="ml-4 flex items-center md:ml-6">
            <label for="toggle" class="text-gray-300 px-3 py-2 rounded-md text-sm font-medium">Mode</label>
            <div class="relative inline-block w-10 mr-2 align-middle select-none transition duration-200 ease-in">
                <input type="checkbox" name="toggle" id="toggle" @change="$emit('toggle')" :checked="(mode === 'dark') ? 'checked' : false" class="toggle-checkbox absolute block w-6 h-6 rounded-full bg-white border-4 appearance-none cursor-pointer"/>
                <label for="toggle" class="toggle-label block overflow-hidden h-6 rounded-full bg-gray-700 cursor-pointer"></label>
              </div>
            <!-- Profile dropdown -->
            <div class="ml-3 relative">
              <div>
                <button type="button" class="max-w-xs bg-gray-800 rounded-full flex items-center text-sm focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white" id="user-menu" aria-expanded="false" aria-haspopup="true">
                  <span class="sr-only">Open user menu</span>
                  <img class="h-8 w-8 rounded-full" src="https://randomuser.me/api/portraits/women/65.jpg" alt="">
                </button>
              </div>
              <div class="origin-top-right absolute right-0 mt-2 w-60 rounded-md shadow-lg py-1 bg-white dark:bg-gray-800 ring-1 ring-black ring-opacity-5 focus:outline-none flex" role="menu" aria-orientation="vertical" aria-labelledby="user-menu">
                <div class="mt-3 ml-2">
                  <img src="../../public/profile-user.svg" alt="user icon" width="20px" height="20px"/>
                  <p class="text-sm text-red-600 mt-14 text-left">|➜</p>
                </div>
                <div>
                <a href="#" class="block px-4 py-2 text-sm text-gray-800 dark:text-gray-300 hover:bg-gray-100" role="menuitem">My Profile</a>

                <a href="#" class="block px-4 text-sm text-gray-400 dark:text-white hover:bg-gray-100 divide-gray-300 border-b-2" role="menuitem">Change settings of your account.</a>

                <a href="#" class="block px-4 py-2 text-sm text-red-600 hover:bg-gray-100" role="menuitem">Logout</a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>

  <header class="bg-gray-50 dark:bg-gray-700 mb-10">
    <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8" >
      <p class="text-xl text-gray-500 dark:text-gray-300">
        Home / <span class="underline">Reports & Insights</span>
      </p>
    </div>
  </header>
</div>
</template>

<script>
export default {
    name: 'Header',
    props: ['mode']
}
</script>

<style lang="postcss" scoped>
/* @apply rules for documentation, these do not work as inline style */
.toggle-checkbox:checked {
  @apply: right-0;
  right: 0;
  border-color: #68D391;
}
.toggle-checkbox:checked + .toggle-label {
  @apply: bg-green-400;
  background-color: #68D391;
}
</style>