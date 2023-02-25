<template>
  <v-app-bar color="teal" dense>
    <v-app-bar-nav-icon
      variant="text"
      class="hidden-md-and-up"
      @click.stop="drawer = !drawer"
    ></v-app-bar-nav-icon>
    <v-toolbar-title>Samuel Santiago</v-toolbar-title>
    <v-spacer></v-spacer>
    <div class="hidden-sm-and-down">
      <v-btn variant="text" icon="mdi-home" to="/" nuxt></v-btn>
      <v-btn variant="text" icon="mdi-information" to="/about" nuxt></v-btn>
    </div>
  </v-app-bar>
  <v-navigation-drawer v-model="drawer" location="bottom" temporary>
    <v-list>
      <v-list-item
        v-for="item in items"
        :key="item.title"
        :to="item.value"
        nuxt
        link
      >
        <v-list-item-icon>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-icon>
        <v-list-item-content>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script lang="ts">
export default {
  data: () => ({
    drawer: false,
    group: null,
    items: [
      {
        title: 'Home',
        value: '/',
        icon: 'mdi-home',
      },
      {
        title: 'About',
        value: '/about',
        icon: 'mdi-information',
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
