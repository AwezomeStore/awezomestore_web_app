<template>
  <div id="app">
    <div class="row" id="header" >
      <b-navbar type="dark">
        <b-navbar-nav >
          <img src="./assets/logoNegroNaranja.png" @click="ir('/')" id="Logo" width="15%" style="background: var(--orange-1);">
          <b-nav-item class="link-session" @click="ir('/Registrar')">Crear cuenta</b-nav-item>
          <b-nav-item class="link-session" @click="ir('/login')">Iniciar Sesión</b-nav-item>
        </b-navbar-nav>
        <div class="search-product-container">
          <b-form-input size="sm" class="mr-sm-2 product-search" placeholder="Search"></b-form-input>
          <b-button size="sm" class="my-2 my-sm-0 search-btn" type="submit">Search</b-button>
        </div>
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
.navbar .navbar-nav .link-session .nav-link{
  color: white;
  font-weight: 500;
}

.search-product-container .product-search {
  width: 20rem;
  margin: 0 0.5rem;
}

.search-product-container .search-btn {
  background-color: var(--gray-1);
  border-color: var(--gray-1);
}

.principal-content {
  margin: 0;
  padding: 0;
  height: 80%;
}

.search-product-container{
  display: flex;
  margin: 0 1rem;
}

#header .navbar-expand{
  justify-content: space-between;
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

