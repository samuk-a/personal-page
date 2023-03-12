<template>
  <div>
    <Head><Title>Início</Title></Head>
    <v-row align="center">
      <v-col cols="12" sm="8" md="5" offset-md="2" :order="order">
        <v-row>
          <v-col cols="12">
            <h1 style="text-align: center" class="text-h2">Samuel Santiago</h1>
            <h2 style="text-align: center" class="text-h4">Dev Back-end</h2>
            <v-divider></v-divider>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12" class="text-body-1">
            <p style="text-align: center">
              Desenvolvedor back-end com experiência profissional em Python,
              Node.js, MongoDB, MySQL, Docker, AWS e GCP.
            </p>
            <p>
              Tenho {{ new Date().getFullYear() - 1999 }} anos, e conto com
              {{ new Date().getFullYear() - 2020 }} anos de experiência
              profissional backend, e com estruturas de dados, como realização
              de web-scraping e desenvolvimento de bots.
            </p>
          </v-col>
        </v-row>
        <v-row no-gutters>
          <v-col cols="12" align="center">
            <v-btn
              variant="text"
              icon="mdi-linkedin"
              size="x-large"
              href="https://www.linkedin.com/in/samuel-santiago/"
              target="_blank"
            ></v-btn>
            <v-btn
              variant="text"
              icon="mdi-github"
              size="x-large"
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
