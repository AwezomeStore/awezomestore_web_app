<template>
  <div id="app">
    <div class="row" id="header" >
      <b-navbar type="dark">
        <b-navbar-nav >
          <img src="./assets/logoNegroNaranja.png" @click="ir('/')" id="Logo" width="15%" style="background: var(--orange-1);">
          <b-nav-item  @click="ir('/Registrar')">Crear cuenta</b-nav-item>
          <b-nav-item  @click="ir('/login')">Iniciar Sesión</b-nav-item>
        </b-navbar-nav>
      </b-navbar>
    </div>
    <div class="principal-content font-size-standard">
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
.principal-content {
  margin: 0;
  padding: 0;
  height: 80%;
}

#app {
  font-family: var(--global-font);
  color: var(--white-1);
}

#header{
  left: 0%;
  right: 0%;
  top: 19px;
  bottom: 29px;
  background: var(--orange-1);
  display: flex;
  align-items: center;
}

#logo{
  background: var(--orange-1);
  height: 15px;
  width: 15px;
}

#nav {
  padding: 30px;
  background: var(--gray-2);
}

#nav a {
  font-weight: bold;
  color: var(--white-1);
}

#nav a.router-link-exact-active {
  color: var(--white-1);
}

#navbar-light #navbar-nav #nav-link {
    color: var(--white-1);
}
</style>

