<template>
  <div class="login">
    <b-overlay :show="showlogin" rounded="sm">
      <form >
        <b-col >
          <b-row sm="5">
            <b-col sm="2" >
              <img src="../assets/Usuario.png" style="width:50px" >
            </b-col>
            <b-col sm="10">
              <b-form-input type="text"  id="input-user" placeholder="Usuario"
                class="form-control form-control-lg" v-model="username" required="" ></b-form-input>
            </b-col>
          </b-row>
          <h1></h1>
          <b-row sm="5" >
            <b-col sm="2">
              <img src="../assets/Contraseña.png" style="width:50px" >
            </b-col>
            <b-col sm="10">
              <b-form-input id="input-contrasena" placeholder="Contraseña"
                type="password" class="form-control form-control-lg" v-model="password" required autocomplete="off" ></b-form-input>
            </b-col>
          </b-row>
          <h1></h1>
          <b-row sm="2">
            <b-col >
              <b-button class="btn-dark btn-lg " @click="login1()">Ingresar</b-button>
              <b-button class="btn-dark btn-lg " @click="ir('/Registrar')">Registrar</b-button>
            </b-col>
          </b-row>
        </b-col>
      </form >
    </b-overlay>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data() {
    return {
      username: "",
      password: "",
      showlogin: false,
      dismissSecs: 5,
      dismissCountDown: 0,
      tipe: '',
      mensaje: '',
    }
  },
  methods: {
    
    async login1 () {
      
      const res = await axios.post('http://localhost:4010/api', {
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
          alert('Login Exitoso')
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
.login{
  background: var(--gray-2);
  padding: 1rem 0.5rem;
  height: 600px;
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>