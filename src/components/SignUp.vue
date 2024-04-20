<template>
    <!-- <div class="signUp_user bg-imageIn">
        <div class="container_signUp_user ">
            <h2>Registrar nuevo usuario</h2>
            <form v-on:submit.prevent="processSignUp" >
                <input type="text" v-model="user.username" value="{{ usern }}">
    
                <input type="password" v-model="user.password" placeholder="Contraseña">
            
                <div>Rol: {{ user.rol }}</div>
                <input type="radio" id="uno" value=1 v-model="user.rol" />
                <label for="uno">Jefe especialista</label>
                <input type="radio" id="two" value=2 v-model="user.rol" />
                <label for="dos">Recepcionista</label>
                        
                <input type="text" v-model="user.first_name" placeholder="Nombres">
               
                <input type="text" v-model="user.last_name" placeholder="Apellidos">
            
                <input type="number" v-model="user.cedula" placeholder="Cedula">
              
                <input type="text" v-model="user.nacimiento" placeholder="Fecha de nacimiento">
            
                <select v-model="user.genero">
                    <option disabled value="">Seleccione un genero</option>
                    <option>Masculino</option>
                    <option>Femenino</option>
                    <option>Otro</option>
                </select>
                <br>
                <input type="text" v-model="user.rh" placeholder="Tipo de sangre">
                <br>              
                <input type="email" v-model="user.email" placeholder="Email">
                <br>
                <input type="number" v-model="user.telefono" placeholder="Telefono">
                <br>
                <input type="text" v-model="user.direccion" placeholder="Direccion"> 
                <br> 
                <button type="submit">Registrarse</button>
                <button type="reset">Reiniciar</button>
            </form>
        </div>
    </div> -->

    <div class="backg-imageIn">

        <div class="container">

            <div class="row">          
                <div class="col-6 mx-auto" >
                    <img src="../assets/avatar1.png" class="col-6 img-fluid rounded mx-auto my-auto d-block mb-3">
                    <form class="col-6 mb-2 mx-auto">
                        <button type="submit" class="btn btn-primary">Subir foto</button>
                    </form>
                </div>
            </div>

            <div class="row">
                <!-- Formulario total -->                
                <form v-on:submit.prevent="processSignUp" id="form1">

                    <!-- ----------------------Formulario datos de autenticacion--------------------- -->
                    <div class="row m-2 p-2 border border-secondary rounded">
                        <h6 class="mb-2">Datos de autenticacion</h6>

                        <label for="inputRol1" class="col-md-1 col-form-label">Rol</label>
                        <div class="col-md-3">
                            <select class="form-select" id="inputRol1" v-model="user.rol" required>
                                <option selected disabled value="">Seleccione un Rol</option>
                                <option value="1">Jefe Especialista</option>
                                <option value="2">Recepcionista</option>
                                <option value="3">Tecnico</option>
                            </select>
                        </div>

                        <label for="inputAlias1" class="col-md-1 col-form-label" >Alias</label>
                        <div class=" col-md-3">
                            <input type="text" class="form-control" id="inputAlias1" v-model="user.username" placeholder="Creado por el sistema" required readonly>
                        </div>

                        <!-- <label for="inputAlias1" class="col-md-1 col-form-label" >Alias</label>
                        <div class=" col-md-3">
                            <input type="text" class="form-control" id="inputAlias1" v-model="user.username"  placeholder="Creado por el sistema" required>
                        </div> -->

                        <label for="inputPassword1" class="col-md-1 col-form-label">Contraseña</label>
                        <div class="col-md-3">
                                <input type="password" class="form-control" id="inputPassword1" v-model="user.password" placeholder="Incluya letras y numeros" required>
                        </div>
                    </div> 

                    <!-- ---------------------Formulario datos personales------------------------ -->
                    <div class="row m-2 p-2 border border-secondary rounded">
                        <h6 class="mb-2">Datos personales</h6>

                        <label for="inputNombre1" class="col-md-1 col-form-label mb-2">Nombres</label>
                        <div class="col-md-3">
                            <input type="text" class="form-control" id="inputNombre1" v-model="user.first_name" required>
                        </div>

                        <label for="inputApellidos1" class="col-md-1 col-form-label">Apellidos</label>
                        <div class="col-md-3">
                            <input type="text" class="form-control" id="inputApellidos1" v-model="user.last_name" required>
                        </div>

                        <label for="inputIdentificacion1" class="col-md-2 col-form-label">Identificacion</label>
                        <div class="col-md-2">
                            <input type="number" class="form-control" id="inputIdentificacion1" v-model="user.cedula" required>
                        </div>

                        <label for="inputNacimiento1" class="col-md-2 col-form-label">Nacimiento</label>
                        <div class="col-md-2">
                            <input type="date" class="form-control" id="inputNacimiento1" v-model="user.nacimiento" required>
                        </div>

                        <label for="inputSexo1" class="col-md-2 col-form-label">Sexo</label>
                        <div class="col-md-2">
                            <select class="form-select" id="inputSexo1" v-model="user.genero" required>
                                <option selected disabled value="">Seleccione</option>
                                <option value="Masculino">Masculino</option>
                                <option value="Femenino">Femenino</option>
                                <option value="Otro">Otro</option>
                            </select>
                        </div>

                        <label for="inputRh1" class="col-md-2 col-form-label">Grupo Rh</label>
                        <div class="col-md-2">
                                <input type="text" class="form-control" id="inputRh1" v-model="user.rh" required>
                        </div>
                    </div> 

                    <!-- --------------------------Formulario datos de contacto------------------------ -->
                    <div class="row m-2 p-2 border border-secondary rounded">
                        <h6 class="mb-2">Datos de contacto</h6>

                        <label for="inputDireccion1" class="col-md-1 col-form-label">Direccion</label>
                        <div class="col-md-3">
                            <input type="text" class="form-control" id="inputDireccion1" v-model="user.direccion" required>
                        </div>

                        <label for="inputTelefono1" class="col-md-1 col-form-label">Telefono</label>
                        <div class="col-md-3">
                            <input type="text" class="form-control" id="inputTelefono1" v-model="user.telefono" required>
                        </div>

                        <label for="inputEmail1" class="col-md-1 col-form-label">Email</label>
                        <div class="col-md-3">
                                <input type="email" class="form-control" id="inputEmail1" v-model="user.email" required>
                        </div>
                    </div> 

                    <!-- ----------------------Botones del formulario principal------------------------ -->
                    <div class="d-grid gap-2 d-md-flex justify-content-md-end mb-3">
                        <input type="text" class="form-control-plaintext" id="infoUsuario" v-bind:value="'El nombre de usuario generado al momento de guardar sera:'+ user.cedula+user.rol"  placeholder="Creado por el sistema" disabled readonly>                    
                        <button type="submit" class="btn btn-secondary">Guardar</button>
                        <button type="button" class="btn btn-secondary" v-on:click="cleanForm">Cancelar</button>
                    </div>

                </form>
            </div> 
        </div> 
    </div>
</template>

<script>
    import axios from 'axios';
    export default {
        name: "SignUp", 
        
        data: function(){
            return {
                user: {
                    username: "" ,
                    password: "",
                    rol: "",
                    first_name: "",
                    last_name: "",
                    cedula: "",
                    nacimiento: "",
                    genero: "",
                    rh: "",
                    email: "",
                    telefono: "",
                    direccion: ""
                }
            }
        },

        methods: {
            processSignUp: function(){
                this.user.username = this.user.cedula + this.user.rol
                axios.post("https://softronic2-54ae1e74c70e.herokuapp.com/user/",this.user,{headers: {}})
                    .then((result) => {
                        let dataSignUp = {
                            username: this.user.username,
                            token_access: result.data.access,
                            token_refresh: result.data.refresh,
                        }

                        this.$emit('completedSignUp', dataSignUp)

                    })
                    .catch((error) => {
                        console.log(error)
                        alert("ERROR: Fallo en el registro.");
                    });
                alert("Por favor guarde el siguiente Alias porque lo necesitara para iniciar sesion: "+this.user.username)
            },
            cleanForm: function(event){
                alert('se han limpiado los campos del formulario')
                form1.reset();
            }
        }

    }
</script>

<style>  
    .backg-imageIn{/*este es un estilo propio*/
        background-image: url('../assets/bg2.jpg');
    }
</style>