<template>
  <div class="va-company-location">
    <PhMapPinLine size="24" />
    <pre class="text-body-1" v-text="location.formatted_address" />
  </div>
</template>

<script>
import { PhMapPinLine } from 'phosphor-vue'

export default {
  name: `va-company-location`,
  components: { PhMapPinLine },
  props: {
    location: { type: Object, default: () => ({}) },
  },
}
</script>
