<template>
  <div>
    <Head><Title>Contact</Title></Head>
    <h1>Contato</h1>
    <v-row>
      <v-col cols="12" sm="6" md="4" lg="3">
        <v-row>
          <v-col cols="12">
            <v-card class="mx-auto">
              <v-card-text>
                <v-row>
                  <v-col cols="12" class="text-center">
                    <v-icon icon="mdi-linkedin" size="88"></v-icon>
                  </v-col>
                </v-row>
                <p>Connect with me on LinkedIn</p>
              </v-card-text>
              <v-card-actions>
                <v-btn
                  href="https://www.linkedin.com/in/samuel-santiago/"
                  target="_blank"
                  >LinkedIn</v-btn
                >
              </v-card-actions>
            </v-card>
          </v-col>
          <v-col cols="12">
            <v-card class="mx-auto">
              <v-card-text>
                <v-row>
                  <v-col cols="12" class="text-center">
                    <v-icon icon="mdi-github" size="88"></v-icon>
                  </v-col>
                </v-row>
                <p>Check out my GitHub</p>
              </v-card-text>
              <v-card-actions>
                <v-btn href="https://www.github.com/samuk-a" target="_blank"
                  >GitHub</v-btn
                >
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
      <v-col>
        <v-form @submit.prevent>
          <v-row no-gutters>
            <v-col cols="12">
              <v-text-field
                v-model="name"
                label="Nome"
                :rules="nameRule"
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12">
              <v-text-field
                v-model="email"
                label="Email"
                :rules="emailRule"
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12">
              <v-select
                v-model="subject"
                label="Assunto Principal"
                :items="items"
                item-title="subject"
                item-value="value"
                required
                :rules="subjectRule"
              ></v-select>
            </v-col>
            <v-col cols="12">
              <v-textarea
                v-model="message"
                label="Mensagem"
                :rules="messageRule"
                required
              ></v-textarea>
            </v-col>
            <v-col cols="12">
              <v-btn type="submit" color="teal">Enviar</v-btn>
            </v-col>
          </v-row>
        </v-form>
      </v-col>
    </v-row>
  </div>
</template>
<script lang="ts">
export default {
  data: () => ({
    name: null,
    email: null,
    subject: null,
    message: null,
    items: [
      { subject: 'Proposta', value: 'Proposta' },
      { subject: 'Requisição de Serviços', value: 'Requisição de Serviços' },
      { subject: 'Dúvidas', value: 'Dúvidas' },
      { subject: 'Outros', value: 'Outros' },
    ],
    nameRule: [
      (value: string) => {
        if (value) return true
        return 'Você deve digitar um nome'
      },
    ],
    emailRule: [
      (value: string) => {
        if (/^[a-z.-]+@[a-z.-]+\.[a-z]+$/i.test(value)) return true
        return 'Você deve digitar um email'
      },
    ],
    subjectRule: [
      (value: string) => {
        if (value) return true
        return 'Você deve selecionar um assunto'
      },
    ],
    messageRule: [
      (value: string) => {
        if (value) return true
        return 'Você deve digitar uma mensagem'
      },
    ],
  }),
}
</script>
