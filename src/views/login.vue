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
            <b-col class="login-btns">
              <b-button class="btn-lg" @click="login1()">Ingresar</b-button>
              <b-button class="btn-lg" @click="ir('/Registrar')">Registrar</b-button>
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
          alert('Login Exitoso');
          this.ir('/');
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
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10rem 1rem 30rem 1rem;
}

.login-btns {
  display: flex;
  justify-content: center;
}

.login-btns .btn-lg {
  margin: 0 .5rem;
  background-color: var(--orange-1);
  border-color: var(--orange-1);
}

</style>