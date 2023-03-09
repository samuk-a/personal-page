<template>
  <div>
    <Head><Title>Início</Title></Head>
    <v-row align="center">
      <v-col cols="12" sm="8" md="7" :order="order">
        <v-row no-gutters>
          <v-col cols="12">
            <h1 style="text-align: center">Samuel Santiago</h1>
          </v-col>
        </v-row>
        <v-row no-gutters>
          <v-col cols="12" align="center">
            <v-btn
              variant="text"
              icon="mdi-linkedin"
              href="https://www.linkedin.com/in/samuel-santiago/"
              target="_blank"
            ></v-btn>
            <v-btn
              variant="text"
              icon="mdi-github"
              href="https://www.github.com/samuk-a"
              target="_blank"
            ></v-btn>
          </v-col>
        </v-row>
      </v-col>
      <v-col cols="12" sm="4" md="3">
        <object type="image/svg+xml" data="developer.svg"></object>
      </v-col>
    </v-row>
  </div>
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
