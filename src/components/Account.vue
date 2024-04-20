<template>
    <div v-if="loaded" class="backg-imageIn">

        <div class="container">

            <div class="row">          
                <div class="col-6 mx-auto" >
                    <img src="../assets/avatar1.png" class="col-6 img-fluid rounded mx-auto my-auto d-block mb-3">
                </div>
            </div>

            <h3 class="text-center">
                Usuario creado el {{ date_joined }} . El usuario se encuentra 
                <span v-if="is_active">Activo</span>
                <span v-else>Inactivo</span>
            </h3>

            <div class="row">

                <form id="form1">

                    <!-- ---------------------- datos de autenticacion--------------------- -->
                    <div class="row m-2 p-2 border border-secondary rounded">
                        <h6 class="mb-2">Datos de autenticacion</h6>

                        <label for="inputId1" class="col-md-2 col-form-label">ID usuario:</label>
                        <div class="col-md-2">
                                <input type="text" class="form-control-plaintext" id="inputId1" v-bind:value="id" readonly>
                        </div>

                        <label for="inputRol1" class="col-md-2 col-form-label">Rol:</label>
                        <div class=" col-md-2">
                            <input type="text" class="form-control-plaintext" id="inputRol1" v-bind:value="rol"  readonly>
                        </div>

                        <label for="inputAlias1" class="col-md-2 col-form-label" >Alias:</label>
                        <div class=" col-md-2">
                            <input type="text" class="form-control-plaintext" id="inputAlias1" v-bind:value="username"  readonly>
                        </div>
                    </div> 

                    <!-- ------------------------------- datos personales------------------------ -->
                    <div class="row m-2 p-2 border border-secondary rounded">
                        <h6 class="mb-2">Datos personales</h6>

                        <label for="inputNombre1" class="col-md-2 col-form-label mb-2">Nombres:</label>
                        <div class="col-md-2">
                            <input type="text" class="form-control-plaintext" id="inputNombre1" v-bind:value="first_name" readonly>
                        </div>

                        <label for="inputApellidos1" class="col-md-2 col-form-label">Apellidos:</label>
                        <div class="col-md-2">
                            <input type="text" class="form-control-plaintext" id="inputApellidos1" v-bind:value="last_name" readonly>
                        </div>

                        <label for="inputIdentificacion1" class="col-md-2 col-form-label">Identificacion:</label>
                        <div class="col-md-2">
                            <input type="text" class="form-control-plaintext" id="inputIdentificacion1" v-bind:value="cedula" readonly>
                        </div>

                        <label for="inputNacimiento1" class="col-md-2 col-form-label">Nacimiento:</label>
                        <div class="col-md-2">
                            <input type="date" class="form-control-plaintext" id="inputNacimiento1" v-bind:value="nacimiento" readonly>
                        </div>

                        <label for="inputSexo1" class="col-md-2 col-form-label">Genero:</label>
                        <div class="col-md-2">
                            <input type="text" class="form-control-plaintext" id="inputRh1" v-bind:value="genero" readonly>
                        </div>

                        <label for="inputRh1" class="col-md-2 col-form-label">Grupo Rh:</label>
                        <div class="col-md-2">
                                <input type="text" class="form-control-plaintext" id="inputRh1" v-bind:value="rh" readonly>
                        </div>
                    </div> 

                    <!-- -------------------------- datos de contacto------------------------ -->
                    <div class="row m-2 p-2 border border-secondary rounded">
                        <h6 class="mb-2">Datos de contacto</h6>

                        <label for="inputDireccion1" class="col-md-2 col-form-label">Direccion:</label>
                        <div class="col-md-2">
                            <input type="text" class="form-control-plaintext" id="inputDireccion1" v-bind:value="direccion" readonly>
                        </div>

                        <label for="inputTelefono1" class="col-md-2 col-form-label">Telefono:</label>
                        <div class="col-md-2">
                            <input type="text" class="form-control-plaintext" id="inputTelefono1" v-bind:value="telefono" readonly>
                        </div>

                        <label for="inputEmail1" class="col-md-1 col-form-label">Email:</label>
                        <div class="col-md-3">
                                <input type="text" class="form-control-plaintext" id="inputEmail1" v-bind:value = "email" readonly disabled>
                        </div>
    
                    </div>


                </form>
            </div> 
        </div> 
    </div> 
</template>

<script>
    import jwt_decode from "jwt-decode";//import * as jwt_decode from 'jwt-decode';
    import axios from 'axios';

    export default {
        name: "Account",

        data: function(){
            return {
                id: "",
                username: "",
                rol: "",
                first_name: "",
                last_name: "",
                cedula: "",
                nacimiento: "",
                genero: "",
                rh: "",
                email: "",
                telefono: "",
                direccion: "",
                date_joined: "",
                is_active: "",
                loaded: false,
            }
        },

        methods: {
            getData: async function () {
                if (localStorage.getItem("token_access") === null || localStorage.getItem("token_refresh") === null) {
                    this.$emit('logOut');
                    return;
                }
                await this.verifyToken();
                let token = localStorage.getItem("token_access");
                let userId = jwt_decode(token).user_id.toString();

                axios.get(`https://softronic2-54ae1e74c70e.herokuapp.com/user/${userId}/`, {headers: {'Authorization': `Bearer ${token}`}})

                    .then((result) => {
                        this.id = result.data.id;
                        this.username = result.data.username;
                        if(result.data.rol==1){
                            this.rol = "Jefe especialista"
                        };
                        
                        this.first_name = result.data.first_name;
                        this.last_name = result.data.last_name;
                        this.cedula = result.data.cedula;
                        this.nacimiento = result.data.nacimiento;
                        this.genero = result.data.genero;
                        this.rh = result.data.rh;
                        this.email = result.data.email;
                        this.telefono = result.data.telefono;
                        this.direccion = result.data.direccion;
                        this.is_active = result.data.is_active;
                        this.date_joined = result.data.date_joined.substring(0, 10);
                        this.loaded = true;
                    })
                    .catch(() => {
                        this.$emit('logOut');
                    });
            },
            
            verifyToken: async function () {

                return axios.post("https://softronic2-54ae1e74c70e.herokuapp.com/refresh/", {refresh: localStorage.getItem("token_refresh")}, {headers: {}}
                )
                    .then((result) => {
                        localStorage.setItem("token_access", result.data.access);
                    })
                    .catch(() => {
                        this.$emit('logOut');
                    });
            }
        },

        created: async function(){
        this.getData();
        },
    }
</script>


<style>

</style>