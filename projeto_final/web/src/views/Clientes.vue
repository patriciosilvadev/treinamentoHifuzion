<template>
  <div id="clientes">
    <v-container fluid
                 grid-list-md>
      <v-layout wrap row>
        <v-flex xs12>
          <app-crud style="margin-top: -70px;"
                    title="Clientes"
                    :items="items"
                    :data="clientes"
                    apiModule="cliente"
          ></app-crud>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  computed: {
    ...mapState('cliente', ['clientes']),
    requiredField () {
      return v => !!v || 'Campo obrigatório'
    },
    items () {
      return [
        { text: '#', value: 'id', width: '10', component: 'v-text-field' },
        {
          text: 'Nome',
          value: 'name',
          width: '200',
          component: 'v-text-field',
          rules: [this.requiredField]
        },
        {
          text: 'Apelido',
          value: 'nick_name',
          width: '200',
          component: 'v-text-field',
          rules: [this.requiredField]
        },
        { text: 'Fone', value: 'phone', width: '100', component: 'v-text-field', showInTable: false },
        {
          text: 'Celular',
          value: 'mobile_phone',
          width: '150',
          component: 'v-text-field',
          rules: [this.requiredField]
        },
        {
          text: 'Email',
          value: 'email',
          component: 'v-text-field',
          rules: [
            this.requiredField,
            v => /[\w_.-]+@[\w-]+\.[\w-]{1,3}(?:\.[\w-]{1,3})?/.test(v) || 'Insira um email válido'
          ]
        },
        {
          text: 'Nascimento',
          value: 'birthday',
          component: 'v-text-field',
          rules: [this.requiredField],
          showInTable: false
        },
        { text: 'Opções', value: '', width: '10', sortable: false }
      ]
    }
  }
}
</script>

<style scoped>

</style>
