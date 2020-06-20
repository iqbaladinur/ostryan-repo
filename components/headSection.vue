<template>
  <div class="my-10">
    <h1 class="text-3xl text-center capitalize text-gray-700">
      {{ sectionTitle }}
    </h1>
    <h2 class="text-lg text-center text-gray-600">
      {{ sectionSubTitle }}
    </h2>
  </div>
</template>

<script>
export default {
  name: 'HeadSection',
  props: {
    sectionTitle: {
      type: String,
      default: 'Title',
      required: true
    },
    sectionSubTitle: {
      type: String,
      default: 'Title',
      required: true
    },
  }
}
</script>
