<template>
  <div>
    <navbar class="mb-8"/>
    <div class="main-body">
      <nuxt />
    </div>
    <footer-bar />
  </div>
</template>
<script>
import navbar from '~/components/navbar.vue';
import footerBar from '~/components/footer.vue';
export default {
  name: 'Default',
  components: {
    navbar,
    footerBar
  },
}
</script>

<style lang="postcss">
.bg-navbar {
  background: #ffb347;  /* fallback for old browsers */
  background: -webkit-linear-gradient(to right, #ffcc33, #ffb347);  /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(to right, #ffcc33, #ffb347); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}
.main-body {
  min-height: calc(100vh - 7.5rem);
}
.dark-mode .nuxt-content {
  & h2,
  & h3,
  & blockquote {
    @apply border-gray-800;
  }
  & > code,
  & li > code,
  & p > code,
  & h3 > code {
    @apply bg-gray-800;
  }
}
.nuxt-content h2 {
  @apply text-3xl font-black mb-4 pb-1 border-b -mt-16 pt-24;
  & > a {
    @apply ml-6;
    &::before {
      content: "#";
      @apply text-green-500 font-normal -ml-6 pr-1 absolute opacity-100;
    }
  }
  &:hover {
    & > a::before {
      @apply opacity-100;
    }
  }
}
.nuxt-content h3 {
  @apply text-2xl font-extrabold mb-2 pb-1 border-b -mt-16 pt-20;
  & > a {
    @apply ml-6;
    &::before {
      content: "#";
      @apply text-green-500 font-normal -ml-5 pr-1 absolute opacity-100;
    }
  }
  &:hover {
    & > a::before {
      @apply opacity-100;
    }
  }
}
@screen lg {
  .nuxt-content h2 a,
  .nuxt-content h3 a {
    @apply ml-0;
    &::before {
      @apply opacity-0;
    }
  }
}
.nuxt-content ul,
.nuxt-content ol {
  @apply list-disc list-inside mb-4;
  & > li {
    @apply leading-7;
    & > ul {
      @apply pl-4;
    }
  }
}
.nuxt-content ol {
  @apply list-decimal;
}
.nuxt-content {
  & a {
    @apply underline;
  }
  & p {
    @apply mb-4 leading-7;
  }
  & > blockquote {
    @apply py-2 pl-4 mb-4 border-l-4;
    & p:last-child {
      @apply mb-0;
    }
  }
  & > code,
  & li > code,
  & p > code {
    @apply bg-gray-100 p-1 text-sm shadow-xs rounded;
  }
  & h3 > code {
    @apply bg-gray-100 p-1 text-lg shadow-xs rounded;
  }
  & pre[class*="language-"] {
    @apply rounded mt-0 mb-4 bg-gray-800 text-sm relative;
    > code {
      @apply bg-gray-800 relative;
      text-shadow: none;
    }
  }
  & video {
    @apply w-full border rounded shadow-md;
  }
}
.nuxt-content-highlight {
  @apply relative;
  & > .filename {
    @apply absolute right-0 text-gray-600 font-light z-10 mr-2 mt-1 text-sm;
  }
}
</style>
