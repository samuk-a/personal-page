<template>
  <v-row align="center">
    <v-col cols="12" sm="8" md="7" :order="order">
      <h1 style="text-align: center">Samuel Santiago</h1>
    </v-col>
    <v-col cols="12" sm="4" md="3">
      <object type="image/svg+xml" data="developer.svg"></object>
    </v-col>
  </v-row>
</template>

<script lang="ts">
export default {
  computed: {
    order() {
      const { smAndUp } = this.$vuetify.display
      return smAndUp ? 'first' : 'last'
    },
  },
}
</script>
