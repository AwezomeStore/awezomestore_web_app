<template>
  <div id="app">
    <div class="row" id="header" >
      <b-navbar type="dark">
        <b-navbar-nav >
          <img src="./assets/logoNegroNaranja.png" @click="ir('/')" id="Logo" width="15%" style="background: #FF9900;">
          <b-nav-item  @click="ir('/Registrar')">Crear cuenta</b-nav-item>
          <b-nav-item  @click="ir('/login')">Iniciar Sesión</b-nav-item>
          
        </b-navbar-nav>
      </b-navbar>
    </div>
    <div class="row" id="nav" style="high:80%">
      <router-view/>
    </div>
    
  </div>
</template>

<script>
export default {
	data() {
    return {  
    }
  },
  methods: {
    ir (a){
        this.$router.push(a)
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
}
#header{
  left: 0%;
  right: 0%;
  top: 19px;
  bottom: 29px;
  background: #FF9900;
  display: flex;
  align-items: center;
}
#logo{
  background: #FF9900;
  height: 15px;
  width: 15px;
}
#nav {
  padding: 30px;
  background: #202020;
}

#nav a {
  font-weight: bold;
  color: #ffffff;
}

#nav a.router-link-exact-active {
  color: #ffffff;
}
#navbar-light #navbar-nav #nav-link {
    color: rgb(255 255 255);
}
</style>

