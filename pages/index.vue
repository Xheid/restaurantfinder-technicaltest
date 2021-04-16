<template>
  <div>
    <VCard class="mb-4">
      <VSystemBar />
      <VBanner single-line>
        Filter the restaurants by ratings
        <template #actions>
          <VSelect
            v-model="minimumRating"
            :items="ratingFilterItems"
            filled
            label="choose your rating"
          />
        </template>
      </VBanner>
    </VCard>
    <div class="companies-cards">
      <VaCompanyCard
        v-for="company of companies"
        :key="company.id"
        :company="company"
      />
    </div>
  </div>
</template>

<script>
import VaCompanyCard from '~/components/company-card.vue'
import companyCardVue from '../components/company-card.vue'

export default {
  name: `page-home`,
  components: {
    VaCompanyCard,
  },
  data() {
    return {
      rawCompanies: [],
      companies: [],
      minimumRating: 0,
    }
  },
  async fetch() {
    try {
      const companies = await this.$axios.$get(`/companies`)
      this.companies = companies
      this.rawCompanies = companies
    } catch (error) {
      this.$nuxt.error(error)
    }
  },
  computed: {
    ratingFilterItems() {
      return [
        { text: `all restaurants`, value: 0 },
        { text: `5 stars`, value: 5 },
        { text: `4 stars or more`, value: 4 },
        { text: `3 stars or more`, value: 3 },
        { text: `2 stars or more`, value: 2 },
        { text: `1 star or more`, value: 1 },
      ]
    },
  },
  watch: {
    minimumRating: function() {
      var data = this.rawCompanies.filter( company => this.getAverage(company) >= this.minimumRating)
      this.companies = data
    }
  },
  methods: {
    getAverage(company){
      var sum = 0
      var num = 0
      if (company.reviews.length != 0){
        company.reviews.forEach( review => {
          sum = sum + review.rating
          num++
        })
        return sum/num
      } else {
        return 0
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~vuetify/src/styles/styles.sass';

@media #{map-get($display-breakpoints, 'md-and-up')} {
  .companies-cards{
    display: grid;
    grid-template-columns: repeat(3, 33.3%);
    row-gap: 40px;

    div {
      max-width: 400px;
      width: 100%;
      margin-left: auto;
      margin-right: auto;
    }
  }
}

@media #{map-get($display-breakpoints, 'sm-and-down')} {
  .companies-cards{
    div {
      margin-top: 10px;
      margin-bottom: 10px;
      max-width: 400px;
      margin-left: auto;
      margin-right: auto;
    }
  }
}

</style>
