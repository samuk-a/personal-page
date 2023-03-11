<template>
  <div>
    <Head><Title>Projetos</Title></Head>
    <h1 v-if="pending" align="center" class="text-h2">Loading Infos...</h1>
    <h1 v-else align="center" class="mb-5 text-h2">Projetos</h1>
    <v-row v-if="!pending" class="text-body-2">
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
const { data: repos, pending } = useFetch(
  'https://github-repositories.herokuapp.com/search?user=samuk-a'
)
</script>
