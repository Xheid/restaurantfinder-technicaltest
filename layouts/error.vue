<template>
  <VApp>
    <h1 class="text-h3">
      {{ errorMessage }}
    </h1>
    <NuxtLink to="/"> Home page </NuxtLink>
  </VApp>
</template>

<script>
export default {
  layout: 'page-error',
  props: {
    error: {
      type: Object,
      default: null,
    },
  },
  data() {
    return {
      pageNotFound: '',
      otherError: '',
    }
  },
  head() {
    const title = this.errorMessage
    return {
      title,
    }
  },
  computed: {
    errorMessage() {
      return this.error.statusCode === 404
        ? `404 Not Found`
        : `An error occurred`
    },
  },
}
</script>
