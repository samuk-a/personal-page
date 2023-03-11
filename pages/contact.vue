<template>
  <div>
    <Head><Title>Contato</Title></Head>
    <h1 align="center" class="text-h2 mb-5">Contato</h1>
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
        <div>
          <v-form v-model="isFormValid" @submit.prevent="sendEmail">
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
                <div class="hidden-md-and-up">
                  <v-btn
                    v-if="!loading"
                    type="submit"
                    color="teal"
                    block
                    prepend-icon="mdi-send"
                    >Enviar</v-btn
                  >
                  <v-btn
                    v-else
                    type=""
                    disabled
                    color="teal"
                    block
                    prepend-icon="mdi-send"
                    >Enviando...</v-btn
                  >
                </div>
                <div class="hidden-sm-and-down" align="right">
                  <v-btn
                    v-if="!loading"
                    type="submit"
                    color="teal"
                    prepend-icon="mdi-send"
                    >Enviar</v-btn
                  >
                  <v-btn
                    v-else
                    type=""
                    disabled
                    color="teal"
                    prepend-icon="mdi-send"
                    >Enviando...</v-btn
                  >
                </div>
              </v-col>
            </v-row>
          </v-form>
        </div>
      </v-col>
    </v-row>
    <v-snackbar
      v-model="success"
      :timeout="2000"
      color="success"
      location="top right"
    >
      Mensagem enviada com sucesso!
    </v-snackbar>
    <v-snackbar
      v-model="error"
      :timeout="2000"
      color="error"
      location="top right"
    >
      Ocorreu um erro!<br />
      Verifique os campos e tente novamente!
    </v-snackbar>
  </div>
</template>
<script lang="ts">
export default {
  data: () => ({
    name: null,
    email: null,
    subject: null,
    message: null,
    isFormValid: false,
    loading: false,
    success: false,
    error: false,
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
      if (!this.isFormValid) {
        this.error = true
        return
      }
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
        this.error = false
        this.success = true
      }
    },
  },
}
</script>
