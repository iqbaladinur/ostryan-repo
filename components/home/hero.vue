<template>
  <div class="container mx-auto hero-container">
    <div class="hero flex">
      <div class="lg:my-auto lg:ml-10 p-10">
        <b class="lg:text-4xl md:text:3xl sm:text-2xl text-gray-700">
          Sketch, Build & Grow <br>
          Your Business.
        </b>
        <p class="text-gray-800">
          Digitalize your business with our one stop solution.
        </p>
        <a href="" class="px-4 py-2 inline-block rounded text-white bg-blue-500 mt-5 shadow-lg hover:bg-blue-600">
          Get Close
        </a>
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
    background: #ffb347;  /* fallback for old browsers */
    background: -webkit-linear-gradient(to right, #ffcc33, #ffb347);  /* Chrome 10-25, Safari 5.1-6 */
    background: linear-gradient(to right, #ffcc33, #ffb347); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
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
