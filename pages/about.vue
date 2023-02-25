<template>
  <div>
    <Head><Title>About</Title></Head>
    <h1 v-if="pending">Loading Infos...</h1>
    <h1 v-else>About</h1>
    <v-row>
      <v-col
        v-for="repo in repos.repositories"
        :key="repo"
        cols="12"
        sm="6"
        md="4"
        lg="3"
      >
        <v-card
          :title="$toTitleCase(repo.name.split('-').join(' '))"
          :text="repo.description"
          class="mx-auto"
        >
          <v-card-actions>
            <v-btn :href="repo.url" target="_blank">GitHub</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script setup lang="ts">
const { data: repos, pending } = await useAsyncData('repos', () =>
  $fetch(`https://github-repositories.herokuapp.com/search`, {
    params: { user: 'samuk-a' },
  })
)
</script>
