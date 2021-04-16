<template>
  <div class="page-company">
    <VSkeletonLoader v-if="$fetchState.pending" type="card" />
    <VCard v-else>
      <VImg
        v-for="photo in company.photos"
        :key="photo"
        :src="company.photos[0]"
        height="250"
        class="white--text"
        gradient="to top, rgba(0,0,0,.1), rgba(0,0,0,.5)"
      >
        <VCardTitle class="text-h3">{{ company.name }}</VCardTitle>
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
      </VImg>
      <VCardText>
        <div class="page-company__contact-info">
          <VaCompanyLocation :location="company.location" />
          <div>
            <PhPhone size="24" />
            <p class="text-body-1">
              {{ company.display_phone }}
            </p>
          </div>
        </div>
      </VCardText>
    </VCard>
    <aside>
      <ul class="pa-0">
        <VSkeletonLoader
          v-if="$fetchState.pending"
          type="article"
          elevation="2"
        />
        <VaCompanyReview v-else
          v-for="review in company.reviews"
          :key="review.id"
          :review="review"
        />
      </ul>
    </aside>
  </div>
</template>

<script>
import { PhPhone } from 'phosphor-vue'

import VaCompanyLocation from '~/components/company-location.vue'
import VaCompanyReview from '~/components/company-review.vue'

export default {
  name: `page-company`,
  components: { VaCompanyLocation, PhPhone, VaCompanyReview },
  data() {
    return {
      company: {},
      currentSlide: 0,
    }
  },
  async fetch() {
    try {
      const { params } = this.$route
      const company = await this.$axios.$get(`/companies/${params.id}`)
      this.company = company
    } catch (error) {
      this.$nuxt.error(error)
    }
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

<style lang="scss" scoped>

.page-company__contact-info {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  grid-gap: var(--gutter);
}

.va-company-review{
  margin-top: 10px;
  margin-bottom: 10px;
}

</style>
