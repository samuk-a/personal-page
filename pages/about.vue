<template>
  <div>
    <Head><Title>Sobre</Title></Head>
    <h1 align="center" class="text-h2 mb-5">Sobre</h1>
    <h2 align="center" class="text-h4">Samuel Candido Santiago</h2>
    <p align="center" class="text-subtitle-1 mb-5 text-uppercase">
      Back-end | Python | Node | MongoDB | MySQL | Docker | Cloud
    </p>
    <v-row justify="start">
      <v-col cols="12" md="8" offset-md="2">
        <h4 class="text-h6">Sobre mim</h4>
        <p>
          Formando em Tecnologia da Informação pela UNIVESP, atuando como
          Engenheiro de Software Backend, utilizando tecnologias em Python e JS,
          atuando na criação de APIs REST, MongoDB, MySQL, Docker, AWS e Google
          Cloud.<br />
          Adepto a metodologias ágeis e boas práticas como Kanban, Scrum,
          Review, Code Review, Conventional Commits e GitFlow.<br />
          Atuo também na realização de webscrappers em páginas públicas federais
          e estaduais, na automatização de consultas.<br />
        </p>
        <p>
          Me formei em 2016 no curso técnico em informática pelo Centro Paula
          Souza, e desde então venho me aprimorando na área de desenvolvimento
          de software.
        </p>
      </v-col>
    </v-row>
    <v-row class="mt-5" justify="start">
      <v-col cols="12" sm="6" md="4" offset-md="2">
        <h4 class="text-h6">Experiências</h4>
        <v-list lines="two">
          <v-list-item
            v-for="item in experiences"
            :key="item.title"
            :title="item.title"
            :subtitle="item.company"
            :prepend-avatar="item.companyAvatar"
          ></v-list-item>
        </v-list>
      </v-col>
      <v-col cols="12" sm="6" md="4">
        <h4 class="text-h6">Certificações</h4>
        <v-list :items="certs" item-props lines="three">
          <template #subtitle="{ subtitle }">
            <div v-html="subtitle"></div>
          </template>
        </v-list>
      </v-col>
    </v-row>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      experiences: [
        {
          title: 'Engenheiro de Software',
          company: 'NAGRO',
          companyAvatar: '/companies/nagro.jpg',
        },
        {
          title: 'Desenvolvedor Web (Freelancer)',
          company: 'VintePila',
          companyAvatar: '/companies/vintepila.jpg',
        },
      ],
      certs: [
        {
          prependAvatar: '/certs/udemy.jpg',
          title: 'Curso NoSQL e MongoDB',
          subtitle: `Curso ministrado por Júlio Alcântara<br><a href="https://www.udemy.com/certificate/UC-ad307164-22ad-4dff-8669-857fe8d738c0/" target="_blank">Udemy</a>`,
        },
        {
          prependAvatar: '/certs/alura.jpg',
          title: 'Formação Python',
          subtitle: `Formação python completa na Alura<br><a href="https://cursos.alura.com.br/degree/certificate/2cfd3012-5c14-454f-9b05-32628b4a04ff" target="_blank">Alura</a>`,
        },
      ],
    }
  },
}
</script>
