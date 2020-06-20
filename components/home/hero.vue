<template>
  <div class="container mx-auto hero-container mt-5">
    <div class="hero flex">
      <div class="lg:my-auto lg:ml-10 p-10">
        <b class="lg:text-4xl text-2xl text-gray-600">
          Sketch, Build & Grow <br>
          Your Business.
        </b>
        <p class="text-gray-700">
          Digitalize your business with our one stop solution.
        </p>
        <button class="px-4 py-1 rounded text-white bg-blue-500 mt-5 shadow-lg hover:bg-blue-600">
          Get Close
        </button>
      </div>
      <img src="~assets/bg.png" class="img-bg">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Hero'
}
</script>

<style lang="postcss" scoped>
.hero-container{
  --minheight: calc(100vh - 7rem); 
  @apply px-2;
  min-height: var(--minheight);
  & > .hero {
    @apply relative rounded-lg shadow-lg;
    min-height: var(--minheight);
    & > .img-bg {
      width: 35rem;
      @apply absolute bottom-0 right-0 pr-10 pb-10;
    }
  }
}
@screen lg {

}
</style>
