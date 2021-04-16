<template>
  <VCard class="va-company-card d-flex flex-column">
    <VImg
      height="100"
      :src="company.photos[0]"
      class="flex-shrink-0 flex-grow-0"
    />
    <VCardTitle class="headline">
      {{ company.name }}
    </VCardTitle>
    <VRating
      color="yellow darken-3"
      background-color="grey darken-1"
      empty-icon="$ratingFull"
      half-increments
      length="5"
      :value="averageRating"
      center
      readonly
    />
    <VCardText>
      <VaComponayLocation :location="company.location" />
    </VCardText>
    <VCardActions class="mt-auto">
      <VBtn
        color="primary"
        nuxt
        :to="`/companies/${company.id}`"
        block
        outlined
      >
        see more
      </VBtn>
    </VCardActions>
  </VCard>
</template>

<script>
import VaComponayLocation from '~/components/company-location.vue'


export default {
  name: `va-company-card`,
  components: { VaComponayLocation },
  props: {
    company: { type: Object, default: () => ({}) },
  },
  computed: {
    averageRating: function (){
      var sum = 0
      var num = 0
      this.company.reviews.forEach( review => {
        sum = sum + review.rating
        num++
      });
      return sum/num
    },
  },
}
</script>
