<template>
  <div>
    <Head><Title>About</Title></Head>
    <h1 v-if="pending">Loading Infos...</h1>
    <h1 v-else>Sobre</h1>
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
          class="mx-auto"
        >
          <v-card-text>
            <v-row>
              <v-col cols="12" class="text-center">
                <v-icon
                  :icon="
                    'mdi-language-' +
                    (
                      repo.language
                        ?.replace('#', 'sharp')
                        .replace('HTML', 'html5') || ''
                    ).toLowerCase()
                  "
                  size="88"
                ></v-icon>
              </v-col>
            </v-row>
            <p>{{ repo.description }}</p>
          </v-card-text>
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
