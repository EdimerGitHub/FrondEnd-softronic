<template>
    <div class="bg-primary bg-gradient text-center text-white"><h2 class="m-0">SOFTRONIC</h2></div>
    <div class="backg-image pt-3" >
        <div class="container">

            <div class="row mb-3">
                <div class="col">
                    <img src="../assets/img2.png" class="img-fluid rounded">
                </div>
            </div>

            <div class="row mb-3">
                <div class="col text-center">
                    <h1>Iniciar sesion</h1>
                </div>
            </div>

            <div class="row">
                <form  v-on:submit.prevent="processLogInUser">

                    <div class="row mb-3">
                        <label for="inputRol1" class="col-sm-2 col-form-label">Rol</label>
                        <div class="col-sm-10">
                            <select v-model="user.rol" class="form-select" id="inputRol1">
                                <option selected disabled value="">Seleccione su Rol</option>
                                <option value="1">Jefe Especialista</option>
                                <option value="2">Recepcionista</option>
                                <option value="3">Tecnico</option>
                            </select>
                        </div> 
                    </div> 

                    <div class="row mb-3">
                        <label for="inputAlias1" class="col-sm-2 col-form-label">Alias</label>
                        <div class="col-sm-10">
                            <input type="text" class="form-control" id="inputAlias1" v-model="user.username" placeholder="Ingrese su usuario">
                        </div>
                    </div>

                    <div class="row mb-3">
                        <label for="inputPassword1" class="col-sm-2 col-form-label">Contraseña</label>
                        <div class="col-sm-10">
                        <input type="password" class="form-control" id="inputPassword1" v-model="user.password" placeholder="Debe contener letras y numeros">
                        </div>
                    </div>

                    <button type="submit" class="btn btn-primary">Ingresar</button>

                </form>
            </div> 

        </div>
    </div>
</template>

<script>
    import axios from 'axios';
    export default {
        name: "LogIn",
        data: function(){
            return {
                user: {
                    username:"",
                    password:"",
                    rol:""
                }
            }
        },
        methods: {
            processLogInUser: function(){
                let usern = this.user.username
                let rolu = usern.charAt(usern.length-1);
                if(rolu==this.user.rol)  {
                    axios.post(
                    "https://softronic2-54ae1e74c70e.herokuapp.com/login/",
                    this.user,
                    {headers: {}}
                    )
                    .then((result) => {
                        let dataLogIn = {
                            username: this.user.username,
                            rol: this.user.rol,
                            token_access: result.data.access,
                            token_refresh: result.data.refresh,
                        }

                        this.$emit('completedLogIn', dataLogIn)

                    })
                    .catch((error) => {
                        if (error.response.status == "401") 
                        alert(`ERROR 401: Credenciales Incorrectas para usuario: "${this.user.username}"`);
                    });
                }else alert(`ERROR 401: Credenciales Incorrectas para usuario: "${this.user.username}"`);
            }
        }
    }
</script>

<style>  
    .backg-image{
        background-image: url('../assets/bg2.jpg');
        height: 100vh;
    }
</style>