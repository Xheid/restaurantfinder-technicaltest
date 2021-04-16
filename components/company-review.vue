<template>
  <VCard class="va-company-review" tag="li">
    <VCardText> {{review.text}} </VCardText>
    <VRating
      color="yellow darken-3"
      background-color="grey darken-1"
      empty-icon="$ratingFull"
      half-increments
      length="5"
      :value="review.rating"
      center
      readonly
    />
  </VCard>
</template>

<script>
export default {
  name: `va-company-review`,
  props: {
    review: { type: Object, default: () => ({}) },
  },
}
</script>
