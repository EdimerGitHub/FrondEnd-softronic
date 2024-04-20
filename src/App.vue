<template>
  <div id="app" class="app m-0">
    <div class="header mb-0" v-if="is_auth">

      <nav class="navbar navbar-expand-lg  mb-0 bg-primary">

        <div class="container-fluid">

            <a class="navbar-brand text-white" href="#" >Menu</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbar1" aria-controls="navbar1" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbar1">

                <ul class="navbar-nav me-auto mb-2 mb-lg-0">

                    <li class="nav-item dropdown" >
                        <a class="nav-link dropdown-toggle text-white" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false" aria-current="page">
                            Gestion de usuarios
                        </a>
                        <ul class="dropdown-menu">
                            <li><a class="dropdown-item" href="#" v-on:click="loadHome">Inicio</a></li>
                            <li><a class="dropdown-item" href="#" v-on:click="loadSignUp">Crear nuevo usuario</a></li>
                        </ul>
                    </li>

                    <li class="nav-item dropdown" >
                        <a class="nav-link dropdown-toggle text-white" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false" aria-current="page">
                            Gestion administrativa
                        </a>
                        <ul class="dropdown-menu">
                            <li><a class="dropdown-item" href="#">Inicio</a></li>
                            <li><a class="dropdown-item" href="#">Buscar dispositivo</a></li>
                            <li><a class="dropdown-item" href="#">Ingresar nuevo</a></li>
                            <li><a class="dropdown-item" href="#">Diagnosticos</a></li>
                            <li><a class="dropdown-item" href="#">Reparaciones</a></li>
                            <li><a class="dropdown-item" href="#">Facturas</a></li>
                            <li><a class="dropdown-item" href="#">Clientes</a></li>
                        </ul>
                    </li>

                    <li class="nav-item dropdown" >
                        <a class="nav-link dropdown-toggle text-white" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false" aria-current="page">
                            Gestion tecnica
                        </a>
                        <ul class="dropdown-menu">
                            <li><a class="dropdown-item" href="#">Inicio</a></li>
                            <li><a class="dropdown-item" href="#" >Buscar Diagnosticos y reparaciones</a></li>
                        </ul>
                    </li>

                    <li class="nav-item" >
                      <a class="nav-link text-white" href="#" v-on:click="loadAccount">Cuenta de usuario</a>
                    </li>

                    <li class="nav-item" >
                      <a class="nav-link text-white" href="#" v-on:click="logOut">Salir</a>
                    </li>

                </ul>

            </div>

        </div>

      </nav> 

    </div>

    <div class="main-component">
      <router-view
        v-on:completedLogIn="completedLogIn"
        v-on:completedSignUp="completedSignUp"
        v-on:logOut="logOut"
      >
      </router-view>
    </div>

    <div class="bg-dark bg-gradient text-center text-white">
      <h6 class="m-0 p-0">Copyright © 2024 SOFTRONIC </h6>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'App',

    data: function(){
      return{
        is_auth: false
      }
    },

    components: {
    },

    methods:{
      verifyAuth: function() {
        this.is_auth = localStorage.getItem("isAuth") || false;
        if (this.is_auth == false)
          this.$router.push({ name: "logIn" });
        else
          this.$router.push({ name: "home" });
      },
      loadLogIn: function(){
        this.$router.push({name: "logIn"})
      },
      loadSignUp: function(){
        this.$router.push({name: "signUp"})
      },
      completedLogIn: function(data) {
        localStorage.setItem("isAuth", true);
        localStorage.setItem("username", data.username);
        localStorage.setItem("rol", data.rol);
        localStorage.setItem("token_access", data.token_access);
        localStorage.setItem("token_refresh", data.token_refresh);
        alert("Autenticación Exitosa");
        this.verifyAuth();
      },
      completedSignUp: function(data) {
        alert("Registro Exitoso");
        //this.completedLogIn(data);       
      },
      loadHome: function() {
        this.$router.push({ name: "home" });
      },
      logOut: function () {
        localStorage.clear();
        alert("Sesión Cerrada");
        this.verifyAuth();
      },
      loadAccount: function () {
        this.$router.push({ name: "account" });
      },
    },

    created: function(){
      this.verifyAuth()
    }
  }
</script>

<style>

</style>
