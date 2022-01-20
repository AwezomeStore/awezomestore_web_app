<template>
  <div class="registro">
      <div>
        <b-card bg-variant="dark">
          <b-form-group
          >
            <b-form-group
              label="Nombres:"
              label-for="nested-street"
              
              label-align-sm="right"
            >
              <b-form-input id="nested-street" v-model="firstName" placeholder="Nombres"></b-form-input>
            </b-form-group>

            <b-form-group
              label="Apellidos:"
              label-for="nested-city"
              label-align-sm="right"
            >
              <b-form-input id="nested-city" v-model="lastname" placeholder="Apellidos"></b-form-input>
            </b-form-group>

            <b-form-group
              label="Usuario:"
              label-for="nested-state"
              label-align-sm="right"
            >
              <b-form-input id="nested-state" v-model="username" placeholder="Usuario"></b-form-input>
            </b-form-group>

            <b-form-group
              label="Contraseña:"
              label-for="nested-country"
              label-align-sm="right"
            >
              <b-form-input  type="password" v-model="password" placeholder="Contraseña"></b-form-input>
            </b-form-group>

            <b-form-group
              label="Repita la Contraseña:"
              label-for="nested-country"
              label-align-sm="right"
            >
              <b-form-input  :state=confirmacion() type="password" v-model="password2" placeholder="contraseña"></b-form-input>
            </b-form-group>

            <b-form-group
              label="Roles:"
              label-align-sm="right"
              class="mb-0"
              v-slot="{ ariaDescribedby }"
              v-model="roles"
            >
              <b-form-checkbox-group
                class="pt-2"
                :options="[ 'vendor', 'support' , 'buyer']"
                :aria-describedby="ariaDescribedby"
              ></b-form-checkbox-group>
            </b-form-group>
            <b-button class="btn-lg btn-signup" @click="Registrar()">Registrar</b-button>
          </b-form-group>
        </b-card>
      </div>

  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      firstName: "",
      lastname: "",
      username: "",
      password: "",
      password2: "",
      roles: [],
      showlogin: false,
      dismissSecs: 5,
      dismissCountDown: 0,
      tipe: '',
      mensaje: '',
    }
  },
  methods: {
    confirmacion(){
      if(this.password === this.password2){
        return true
      }else{
        return false
      }
    },
    async Registrar () {
      const res = await axios.post('https://7ed8-2800-484-5181-98e0-c0c6-3d11-1df-9179.ngrok.io', {
        query: `mutation {
                  signUp(data: {
                    firstName: "${this.firstName}",
                    lastName: "${this.lastname}",
                    username: "${this.username}",
                    password: "${this.password2}",
                    roles: ["${this.roles}"]
                  })
                }`
      }).then(res =>{
          console.log(res);
          alert('Registro Exitoso')
        }).catch(error => {
          if (!error.response) {
            // network error
            alert('Error de conexion')
          }
          if (error.response.status === 500) {
            alert('No se encentra el usuario')
          } else {
            alert('Error en la aplicación')
          }
        this.showLogin = false

        })
      console.log(res);
    },
    ir (a){
        this.$router.push(a)
    },
  }
}
</script>

<style>
.registro{
  background: var(--gray-2);
  padding: 1rem 0.5rem;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 3rem;
  padding: 5rem 1rem 10rem 1rem;
}

.btn-signup{
  margin: .5rem 0rem;
  background-color: var(--orange-1);
  border-color: var(--orange-1);
}

.card .card-body {
  background-color: var(--gray-3);
}

</style>
