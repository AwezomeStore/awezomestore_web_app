<template>
  <div>
    <b-card bg-variant="light">
      <b-form-group
        label-cols-lg="3"
        label="Pagos"
        label-size="lg"
        label-class="font-weight-bold pt-0"
        class="mb-0"
      >
        <b-form-group
          label="Usuario:"
          label-for="nested-street"
          label-cols-sm="3"
          label-align-sm="right"
        >
          <b-form-input id="nested-street"></b-form-input>
        </b-form-group>

        <b-form-group
          label="Orden:"
          label-for="nested-city"
          label-cols-sm="3"
          label-align-sm="right"
        >
          <b-form-input id="nested-city"></b-form-input>
        </b-form-group>

        <b-form-group
          label="Costo de envío:"
          label-for="nested-state"
          label-cols-sm="3"
          label-align-sm="right"
        >
          <b-form-input id="nested-state"></b-form-input>
        </b-form-group>

        <b-form-group
          label="Valor del producto:"
          label-for="nested-country"
          label-cols-sm="3"
          label-align-sm="right"
        >
          <b-form-input id="nested-country"></b-form-input>
        </b-form-group>

        <div>
          <b-form-select v-model="selected" :options="options"></b-form-select>
          <div class="mt-3">Método de Pago: <strong>{{ selected }}</strong></div>
        </div>

        <div>
          <b-form-select v-model="selected2" :options="options2"></b-form-select>
          <div class="mt-3">Regalo: <strong>{{ selected2 }}</strong></div>
        </div>
      </b-form-group>
      <b-button class="btn-lg" @click="sendPayment()">Enviar</b-button>
    </b-card>
  </div>
</template>

<script>

import axios from 'axios'
export default {
  data() {
    return {

      selected: null,
      selected2: null,
      options: [
        { value: null, text: 'Seleccione' },
        { value: '1', text: 'VISA' },
        { value: '2', text: 'Master Card' },
        { value: '3', text: 'American Express' },
        { value: '4', text: 'Diners Club' }
      ],
      options2: [
        { value: null, text: 'Seleccione' },
        { value: '1', text: 'True' },
        { value: '2', text: 'False' },
      ]
    }
  },
  methods: {

    async sendPayment() {
      const res = await axios.post('https://7ed8-2800-484-5181-98e0-c0c6-3d11-1df-9179.ngrok.io', {
        query: `mutation {
                  signIn(data: {
                  username: "${this.username}",
                  password: "${this.password}"
                  }) {
                    id
                    userId
                    token
                    roles{
                      id
                      roleName
                    }
                  }
                }`
      }).then(res =>{
        console.log(res);
      }).catch(error => {
        console.log(error);
      })
      console.log(res);
    }
  }
}
</script>

<style>

</style>