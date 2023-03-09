<template>
  <div>
    <Head><Title>Contato</Title></Head>
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
                <p>Conecte-se comigo no LinkedIn</p>
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
                <p>Dê uma olhada no meu GitHub</p>
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
        <div v-if="success">
          <v-alert type="success" closable>
            Mensagem enviada com sucesso!
          </v-alert>
        </div>
        <div v-else>
          <v-alert type="info" closable>
            Preencha o formulário abaixo para entrar em contato comigo
          </v-alert>
        </div>
        <div>
          <v-form @submit.prevent="sendEmail">
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
                <v-btn v-if="!loading" type="submit" color="teal">Enviar</v-btn>
                <v-btn v-else type="" disabled color="teal">Enviando...</v-btn>
              </v-col>
            </v-row>
          </v-form>
        </div>
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
    loading: false,
    success: false,
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
        if (/^\w+@[a-z.-]+\.[a-z]+$/i.test(value)) return true
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
  methods: {
    async sendEmail() {
      if (this.loading) return
      if (!this.name || !this.email || !this.subject || !this.message) return
      this.loading = true
      const response: any = await $fetch(
        'https://mail-send.herokuapp.com/mail/send',
        {
          method: 'POST',
          body: {
            from: this.name,
            to: 'contato@samuelsantiago.dev.br',
            subject: `[${this.subject}] - ${this.name}`,
            message: `<b>${this.email}</b><br>${this.message}`,
          },
        }
      )
      this.loading = false
      if (response.status === 200) {
        this.name = null
        this.email = null
        this.subject = null
        this.message = null
        this.success = true
      }
    },
  },
}
</script>
