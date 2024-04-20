<template>
    <div class="greetings">
        <h1>¡Bienvenido <span> {{username}} </span>!</h1>
    </div>
    <div class="container-fluid">

        <div class="row mb-3">

            <div class="col-md-6" >
                <img src="../assets/usu2.jpg" class="col-6 img-fluid rounded mx-auto my-auto d-block mb-3">
                <form class="col-6 mb-3 mx-auto">
                    <button type="submit" class="btn btn-primary">Ver foto</button>
                </form>
            </div>

            <form class="col-md-6 my-auto p-3 border border-secondary rounded">
                <h6 class="mb-2">Opciones de busqueda</h6>
                <div class="row mb-3 ">
                    <label for="inputRol1" class="col-sm-2 col-form-label">Rol</label>
                    <div class="col-sm-10">
                        <select class="form-select" id="inputRol1">
                            <option selected>Seleccione un Rol</option>
                            <option value="1">Jefe Especialista</option>
                            <option value="2">Recepcionista</option>
                            <option value="3">Tecnico</option>
                            <option value="3">Bloqueados</option>
                            <option value="3">Activos</option>
                        </select>
                    </div> 
                </div> 

                <div class="row mb-3">
                    <label for="inputAlias1" class="col-sm-2 col-form-label">Buscar</label>
                    <div class="col-sm-10">
                    <input type="text" class="form-control" id="inputAlias1">
                    </div>
                </div>

                <button type="submit" class="btn btn-primary">Iniciar busqueda</button>

            </form>

        </div>

        <div class="row mb-3">
            <div class="col text-center">
                <h1>Resultados de la busqueda</h1>
            </div>
        </div>

        <div class="row table-responsive">

        <table class="table table-striped">
            <thead class="table-dark">
            <tr>
                <th scope="col">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-check2-circle" viewBox="0 0 16 16">
                <path d="M2.5 8a5.5 5.5 0 0 1 8.25-4.764.5.5 0 0 0 .5-.866A6.5 6.5 0 1 0 14.5 8a.5.5 0 0 0-1 0 5.5 5.5 0 1 1-11 0"/>
                <path d="M15.354 3.354a.5.5 0 0 0-.708-.708L8 9.293 5.354 6.646a.5.5 0 1 0-.708.708l3 3a.5.5 0 0 0 .708 0l7-7z"/>
                </svg>
                </th>
                <th scope="col">Estado</th>
                <th scope="col">Alias</th>
                <th scope="col">Rol</th>
                <th scope="col">Identificacion</th>
                <th scope="col">Nombres</th>
                <th scope="col">Apellidos</th>
                <th scope="col">Fecha de Nacimiento</th>
                <th scope="col">Sexo</th>
                <th scope="col">Grupo sanguineo</th>
                <th scope="col">Direccion</th>
                <th scope="col">Telefono</th>
                <th scope="col">Email</th>
            </tr>
            </thead>
            <tbody>
            <tr>
                <th>
                <input class="form-check-input" type="radio" name="flexRadioDefault" id="flexRadio1">
                </th>
                <td>Activo</td>
                <td>JEED01</td>
                <td>Jefe-Especialista</td>
                <td>1066258652</td>
                <td>Eduardo</td>
                <td>Castillo Mercado</td>
                <td>07/06/1980</td>
                <td>Masculino</td>
                <td>O-</td>
                <td>Carrera 7 #15-07</td>
                <td>304 581 9898</td>
                <td>eduardo@uncorreo.com</td>
            </tr>
            <tr>
                <th>
                <input class="form-check-input" type="radio" name="flexRadioDefault" id="flexRadio1">
                </th>
                <td>Activo</td>
                <td>READ01</td>
                <td>Recepcionista</td>
                <td>1052245652</td>
                <td>Adriana Maria</td>
                <td>Ruiz Meza</td>
                <td>01/11/1998</td>
                <td>Femenino</td>
                <td>A+</td>
                <td>Calle 2 #24-22</td>
                <td>318 481 5201</td>
                <td>Adriana@uncorreo.com</td>
            </tr>
            <tr>
                <th>
                <input class="form-check-input" type="radio" name="flexRadioDefault" id="flexRadio1">
                </th>
                <td>Inactivo</td>
                <td>TEJU01</td>
                <td>Tecnico</td>
                <td>1065951357</td>
                <td>Julian</td>
                <td>Pacheco Diaz</td>
                <td>25/12/1990</td>
                <td>Masculino</td>
                <td>A+</td>
                <td>Calle 11 #15-42</td>
                <td>312 025 2937</td>
                <td>Julian@uncorreo.com</td>
            </tr>
            </tbody>
        </table>
        </div> 

        <div class="d-grid gap-2 d-md-flex justify-content-md-end">
                <button type="submit" class="btn btn-primary mb-2">Editar usuario</button>
                <button type="submit" class="btn btn-primary mb-2">Bloquear/Desbloquear usuario</button>
                <button type="submit" class="btn btn-primary mb-2">Eliminar Usuario</button>
        </div>

    </div>
</template>

<script>
    export default {
        name: "Home",
        data: function(){
            return {
                username: localStorage.getItem('username') || "none"
            }
        }
    }
</script>

<style>

</style>