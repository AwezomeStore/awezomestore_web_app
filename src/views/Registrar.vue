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
            <b-button class="btn-dark btn-lg " @click="Registrar()">Registrar</b-button>
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
      
      const res = await axios.post('http://localhost:4010/api', {
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
  height: 600px;
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>
