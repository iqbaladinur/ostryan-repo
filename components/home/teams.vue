<template>
  <div class="flex flex-wrap">
    <div
      v-for="(person, key) in teams"
      :key="key"
      class="lg:w-1/3 w-full card"
    >
      <div class="p-4 text-gray-400">
        <div class="h-full bg-gray-700 shadow rounded-lg hover:shadow-lg cursor-pointer">
          <div class="h-40 rounded-t-lg flex">
            <img :src="person.img" class="object-cover h-24 w-24 m-auto rounded-full shadow" :alt="person.name" loading="lazy">
          </div>
          <div class="p-2 rounded-b-lg">
            <h1 class="text-lg text-center">
              {{ person.name }}
            </h1>
            <p class="text-center text-sm">
              {{ person.position }}
            </p>
            <div class="flex py-4">
              <a :href="person.twitter" class="text-sm m-auto bg-blue-500 py-2 px-4 rounded-full shadow-lg text-white">
                <i class="fa fa-twitter">
                  twitter
                </i>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import iqbal from '@/assets/teams/iqbal.gif';
import adi from '@/assets/teams/adi.png';
import nurmansyah from '@/assets/teams/nurmansyah.gif';
export default {
  name: 'Services',
  data() {
    return {
      teams: [
        {
          name: 'Iqbal',
          img: iqbal,
          position: 'Frontend Engineer',
          twitter: 'https://twitter.com/Iqbaladinur'
        },
        {
          name: 'Adi',
          img: adi,
          position: 'UI/UX',
          twitter: 'https://twitter.com/Iqbaladinur'
        },
        {
          name: 'Nurmansyah',
          img: nurmansyah,
          position: 'Backend Engineer',
          twitter: 'https://twitter.com/Iqbaladinur'
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
