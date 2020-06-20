<template>
  <div>
    <hero />
    <div class="container mx-auto lg:px-40 px-10">
      <head-section
        section-title="Made For Everyone"
        section-sub-title="We not only make paid products, but also open source for everyone."
      />
      <div v-if="!isLoading">
        <div v-if="posts.length > 0">
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
          <div class="mt-5">
            <button v-if="currentPage > 1" @click="prevArticle" class="px-4 border border-black focus:outline-none">
              prev
            </button>
            <button v-if="currentPage < totalPages" @click="nextArticle" class="px-4 border border-black focus:outline-none">
              next
            </button>
          </div>
        </div>
        <div v-else class="text-center">
          You haven't create post.
        </div>
      </div>
      <div v-else >
        loading...
      </div>
    </div>
  </div>
</template>

<script>
import postItem from '~/components/postItem';
import hero from '~/components/home/hero';
import headSection from '~/components/headSection';
const requiredPostKey = ['title', 'slug', 'description', 'publishedAt', 'category', 'openSource', 'link', 'demo', 'thumbnail'];
const sortKey = 'title';
const sortDirection = 'desc';
export default {
  name: 'Home',
  head() {
    return {
      title: `Home - ${process.env.blogTitle}`
    }
  },
  components: {
    postItem,
    hero,
    headSection
  },
  async fetch({ store, $content, error }) {
    try {
      const listMenu = await $content('page').only(['navTitle', 'slug']).fetch();
      store.commit('menu/storePageMenu', listMenu);
    } catch (error) {
      error({ statusCode: 500, message: error })
    }
  },
  async asyncData ({ $content }) {
    // change the limit for pagination
    const limit = process.env.perPage;
    const skip = 0;
    const allPost = await $content('post').only(['createdAt']).fetch();
    const totalPost = allPost.length;
    const posts = await $content('post').sortBy(sortKey, sortDirection).only(requiredPostKey).limit(limit).fetch();
    const totalPages = Math.ceil(totalPost / limit);
    return {
      posts,
      limit,
      skip,
      totalPost,
      totalPages,
      currentPage: 1
    }
  },
  data() {
    return {
      isLoading: false
    }
  },
  methods: {
    async nextArticle() {
      const nextPage = this.currentPage + 1;
      this.currentPage = nextPage <= this.totalPages ? nextPage : this.currentPage;
      if (nextPage <= this.totalPages) {
        this.skip += this.limit;
        this.isLoading = true;
        this.posts = await this.$content('post').sortBy(sortKey, sortDirection).only(requiredPostKey).skip(this.skip).limit(this.limit).fetch();
        this.isLoading = false;
      }
    },
    async prevArticle() {
      const prevPage = this.currentPage - 1;
      this.currentPage = prevPage < 1 ? 1 : prevPage;
      if (prevPage >= 1) {
        this.skip -= this.limit;
        this.isLoading = true;
        this.posts = await this.$content('post').sortBy(sortKey, sortDirection).only(requiredPostKey).skip(this.skip).limit(this.limit).fetch();
        this.isLoading = false;
      }
    },
  }
}
</script>
