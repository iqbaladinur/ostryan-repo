<template>
  <article class="container mx-auto lg:px-40 px-10">
    <div v-if="!isLoading">
      <div class="flex flex-wrap">
        <post-item
          v-for="(post, key) in posts"
          :key="key"
          :title="post.title"
          :description="post.description"
          :slug="post.slug"
          :created-at="post.publishedAt"
          :category="post.category"
          :others="{ thumbnail: post.thumbnail, demo: post.thumbnail, link: post.link}"
          class="lg:w-1/3 w-full"
        />
      </div>
    </div>
    <div v-else >
      loading...
    </div>
  </article>
</template>

<script>
import postItem from '~/components/postItem';
const requiredPostKey = ['title', 'slug', 'description', 'publishedAt', 'category', 'openSource', 'link', 'demo', 'thumbnail'];
const sortKey = 'title';
const sortDirection = 'desc';
export default {
  name: 'Category',
  head () {
    const categorySlug = `${process.env.blogTitle} | ${decodeURIComponent(this.$route.params.category)}`; 
    const desc = `all post in ${categorySlug}`;
    return {
      title: categorySlug,
      meta: [
        { hid: 'description', name: 'description', content: desc },
        { hid: 'og:title', property: 'og:title', content: categorySlug },
        { hid: 'og:description', property: 'og:description', content: desc },
        { hid: 'og:url', property: 'og:url', content: `${process.env.baseUrl}/categories/${this.category}` },
        { hid: 'og:image', property: 'og:image', content: `${process.env.baseUrl}/image.png` },
        { hid: 'twitter:title', name: 'twitter:title', content: categorySlug },
        { hid: 'twitter:description', name: 'twitter:description', content: desc }
      ]
    }
  },
  components: {
    postItem
  },
  async fetch({ store, $content, error }) {
    try {
      const listMenu = await $content('page').only(['navTitle', 'slug']).fetch();
      store.commit('menu/storePageMenu', listMenu);
    } catch (error) {
      error({ statusCode: 500, message: error })
    }
  },
  async asyncData ({ $content, params }) {
    // change the limit for pagination
    const categorySlug = decodeURIComponent(params.category);
    const posts = await $content('post').sortBy(sortKey, sortDirection).only(requiredPostKey).where({ category : categorySlug }).fetch();
    return {
      posts,
      categorySlug,
      category: params.category
    }
  },
  data() {
    return {
      isLoading: false
    }
  },
}
</script>
