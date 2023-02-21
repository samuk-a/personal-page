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
    <v-list :items="items"></v-list>
  </v-navigation-drawer>
</template>

<script lang="ts">
export default {
  data: () => ({
    drawer: false,
    group: null,
    items: [
      {
        title: 'Foo',
        value: 'foo',
      },
      {
        title: 'Bar',
        value: 'bar',
      },
      {
        title: 'Fizz',
        value: 'fizz',
      },
      {
        title: 'Buzz',
        value: 'buzz',
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
