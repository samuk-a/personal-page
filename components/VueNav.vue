<template>
  <v-app-bar color="teal" dense>
    <v-toolbar-title style="cursor: pointer" @click="$router.push('/')">
      Samuel Santiago
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <div class="hidden-sm-and-down">
      <v-btn
        v-for="item in items"
        :key="item.title"
        variant="text"
        :icon="item.icon"
        :to="item.value"
        nuxt
      ></v-btn>
    </div>
  </v-app-bar>
  <v-bottom-navigation grow class="hidden-md-and-up">
    <v-btn
      v-for="item in items"
      :key="item.title"
      :value="item.title"
      :to="item.value"
      nuxt
      link
    >
      <v-icon>{{ item.icon }}</v-icon>
      {{ item.title }}
    </v-btn>
  </v-bottom-navigation>
</template>

<script lang="ts">
export default {
  data: () => ({
    drawer: false,
    group: null,
    items: [
      {
        title: 'Início',
        value: '/',
        icon: 'mdi-home',
      },
      {
        title: 'Sobre',
        value: '/about',
        icon: 'mdi-information',
      },
      {
        title: 'Projetos',
        value: '/projects',
        icon: 'mdi-folder',
      },
      {
        title: 'Contato',
        value: '/contact',
        icon: 'mdi-email',
      },
    ],
  }),

  watch: {
    group() {
      this.drawer = false
    },
  },
}
</script>
