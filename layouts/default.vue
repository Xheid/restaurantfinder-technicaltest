<template>
  <VApp class="layout-default">
    <VAppBar fixed app>
      <NuxtLink to="/" class="text-decoration-none font-weight-black">
        <VToolbarTitle class="text-h5 text-md-h4 font-weight-black">
          Restaurant finder
        </VToolbarTitle>
      </NuxtLink>
      <v-spacer />
    </VAppBar>
    <VMain>
      <VContainer class="pt-4 pt-lg-8">
        <nuxt />
      </VContainer>
    </VMain>
    <VFooter app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </VFooter>
  </VApp>
</template>

<script>
export default {
  name: `layout-default`,
}
</script>

<style lang="scss" scoped>
@import '~vuetify/src/styles/styles.sass';

.layout-default {
  --gutter: #{map-get($grid-gutters, 'lg')};

  @media #{map-get($display-breakpoints, 'lg-and-up')} {
    --gutter: #{$grid-gutter};
  }
}
</style>
