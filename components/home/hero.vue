<template>
  <div class="container mx-auto hero-container">
    <div class="hero flex">
      <div class="lg:my-auto lg:ml-10 px-10 lg:py-10 pt-16 z-10">
        <b class="lg:text-4xl md:text:4xl sm:text-xl text-3xl text-gray-700">
          Sketch, Build & Grow <br>
          Your Ideas.
        </b>
        <p class="text-gray-800">
          Digitalize your ideas with our one stop solution.
        </p>
        <a :href="`mailto:${email}`" class="px-4 py-2 inline-block rounded text-white bg-blue-500 mt-5 shadow-lg hover:bg-blue-600">
          Get Close
        </a>
      </div>
      <img src="~assets/bg.png" class="img-bg" loading="lazy" alt="ostryan hero image">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Hero',
  data() {
    return {
      email: process.env.email
    }
  }
}
</script>

<style lang="postcss" scoped>
.hero-container{
  --minheight: calc(100vh - 7rem); 
  @apply px-2;
  min-height: var(--minheight);
  & > .hero {
    @apply relative;
    min-height: var(--minheight);
    & > .img-bg {
      width: 100%;
      @apply absolute bottom-0 p-5;
    }
  }
}
@screen md {
  .hero-container{
    --minheight: 600px;
    min-height: var(--minheight);
    & > .hero {
      min-height: var(--minheight);
      & > .img-bg {
        width: 35rem;
        @apply absolute bottom-0 right-0 pr-10 pb-10;
      }
    }
  }
}
@screen lg {
  .hero-container{
    --minheight: 600px;
    min-height: var(--minheight);
    & > .hero {
      min-height: var(--minheight);
      & > .img-bg {
        width: 35rem;
        @apply absolute bottom-0 right-0 pr-10 pb-10;
      }
    }
  }
}
</style>
