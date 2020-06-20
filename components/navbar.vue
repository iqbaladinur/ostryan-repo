<template>
  <div class="rounded shadow text-gray-700">
    <nav class="container mx-auto flex items-center justify-between flex-wrap p-2">
      <div>
        <nuxt-link to="/" class="flex items-center flex-shrink-0 pr-3 rounded">
          <div class="w-10 h-10 flex">
            <img src="/icon.png" class="w-8 m-auto">
          </div>
          <span class="text-sm font-bold ml-1 uppercase">
            {{ title }}
          </span>
        </nuxt-link>
      </div>
      <div class="block lg:hidden">
        <button class="flex items-center px-3 py-2 focus:outline-none" @click="isHide = !isHide">
          <svg class="fill-current h-5 w-4" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><title>Menu</title><path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"/></svg>
        </button>
      </div>
      <div class="w-full lg:block flex-grow lg:flex lg:items-center lg:w-auto" :class="{ 'hidden' : isHide}">
        <div class="flex lg:flex-grow bg-blue-300 items-center w-auto px-2 lg:px-0"></div>
        <div class="text-sm px-2 lg:px-0">
          <nuxt-link
            :to="`/categories`"
            class="capitalize block mt-3 hover:text-gray-600 lg:inline-block lg:mt-0 mr-4 lg:mb-0 mb-3"
          >
            Repo Category
          </nuxt-link>
          <nuxt-link
            v-for="(item, key) in menu"
            :key="key" 
            :to="`/pages/${item.slug}`"
            class="capitalize block mt-3 hover:text-gray-600 lg:inline-block lg:mt-0 mr-4 lg:mb-0 mb-3"
          >
            {{ item.navTitle }}
          </nuxt-link>
          <a
            href="https://github.com/iqbaladinur"
            class="capitalize block mt-3 text-white lg:inline-block lg:mt-0 lg:mb-0 mb-3 bg-gray-700 flex px-5 lg:py-1 py-2 rounded"
          >
            <i class="fa fa-github m-auto"></i>
          </a>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  computed: {
    menu() {
      return this.$store.getters['menu/getMenu'];
    }
  },
  data() {
    const title = process.env.blogTitle; 
    return {
      title,
      isHide: true
    }
  },
};
</script>
<style scoped>
.bg-navbar {
  background: #ffb347;  /* fallback for old browsers */
  background: -webkit-linear-gradient(to right, #ffcc33, #ffb347);  /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(to right, #ffcc33, #ffb347); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}
</style>