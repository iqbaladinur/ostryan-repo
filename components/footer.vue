<template>
  <footer class="h-10 flex text-gray-700 border-t border-gray-500">
    <p class="text-center m-auto text-xs px-2">
      {{ `Ostryan ${year}, see our location ` }}
      <a :href="location" class="text-blue-300">here. </a>
    </p>
  </footer>
</template>

<script>
export default {
  name: 'FooterBar',
  data() {
    return {
      year: new Date().getFullYear(),
      location: 'https://maps.app.goo.gl/GTfgxVkEshegtuug6'
    }
  }
}
</script>
