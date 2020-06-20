<template>
  <div class="p-4">
    <div class="h-full shadow rounded-lg hover:shadow-lg cursor-pointer">
      <div class="h-48">
        <img :src="this.others.thumbnail" class="object-cover rounded-t-lg w-full h-full" :alt="title">
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
        <p class="text-sm">
          {{ description }}
        </p>
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
