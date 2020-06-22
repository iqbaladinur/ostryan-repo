<template>
  <div class="p-4">
    <div class="h-full shadow rounded-lg hover:shadow-lg cursor-pointer">
      <div class="h-48 bg-navbar rounded-t-lg">
        <img :src="others.thumbnail" class="shadow object-cover rounded-t-lg w-full h-full" :alt="title">
      </div>
      <div class="py-2 px-4">
        <nuxt-link :to="`/post/${slug}`" class="text-xl hover:text-blue-700 capitalize">
          {{ title }}
        </nuxt-link>
        <p class="text-xs">
          &#128198; {{ formatLocaleDateString(createdAt) }}
        </p>
        <div class="text-xs">
          <nuxt-link
            :to="`/categories/${encodeURIComponent(category)}`"
            class="hover:text-blue-300"
          >
            &#128194; {{ category }}
          </nuxt-link>
        </div>
        <p class="text-sm capitalize">
          {{ description }}
        </p>
        <div class="flex my-3">
          <a  :href="others.link" class="mr-1 text-center block bg-gray-800 w-full p-1 rounded text-gray-300">
            <i class="fa fa-github"></i>
          </a>
          <a  :href="others.demo" class="ml-1 text-center block bg-navbar w-full p-1 rounded text-gray-700">
            <i class="fas fa-external-link-square-alt"></i>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { formatLocaleDateString } from '~/helper/dateHelper';

export default {
  name: 'PostItem',
  props: {
    title: {
      type: String,
      default: 'title',
      required: true,
    },
    description: {
      type: String,
      default: 'desc',
      required: true,
    },
    slug: {
      type: String,
      default: '404',
      required: true,
    },
    createdAt: {
      type: String,
      default: formatLocaleDateString(),
      required: true,
    },
    category: {
      type: String,
      default: 'uncategorized',
      required: false
    },
    others: {
      type: Object,
      default: null,
      require: true
    }
  },
  methods: {
    formatLocaleDateString
  },
}
</script>
