<template>
  <div class="flex flex-wrap">
    <div
      v-for="(service, key) in services"
      :key="key"
      class="lg:w-1/3 w-full card"
    >
      <div class="p-4">
        <div class="h-full shadow rounded-lg hover:shadow-lg cursor-pointer">
          <div class="h-48 rounded-t-lg flex">
            <img :src="service.img" class="object-cover w-2/3 h-auto m-auto" :alt="service.title" loading="lazy">
          </div>
          <div class="p-2 bg-white rounded-b-lg">
            <h1 class="text-lg text-gray-700 text-center">
              {{ service.title }}
            </h1>
            <p class="text-center text-sm text-gray-600">
              {{ service.desc }}
            </p>
            <div class="flex py-4">
              <a :href="`mailto:${email}`" class="text-sm m-auto bg-gray-800 py-2 px-4 rounded-lg shadow-lg text-gray-300">
                {{ service.button }}
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import webImage from '@/assets/services/website.png';
import appImage from '@/assets/services/app.png';
import toolImage from '@/assets/services/tool.png';
export default {
  name: 'Services',
  data() {
    return {
      email: process.env.email,
      services: [
        {
          title: 'Website',
          img: webImage,
          desc: 'Create a personal web, company profile or any web app with the latest cool technology.',
          button: 'Create me a Website'
        },
        {
          title: 'Mobile App',
          img: appImage,
          desc: 'Need high portability solution to solve your problem? we provide mobile app creation.',
          button: 'Create me a Mobile App'
        },
        {
          title: 'Scripting Tool',
          img: toolImage,
          desc: 'Create a content management or library to solve your problem without having to bother.',
          button: 'Create me a Tool'
        },
      ]
    }
  }
}
</script>

<style lang="postcss" scoped>
.card{
  transition: all .2s ease-in-out;
  &:hover {
    @apply z-50;
    transform: scale(1.2);
  }
}
</style>>
