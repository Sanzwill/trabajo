<template>
  
<div class="container">
      <router-link to="/crear" class="btn btn-success">INGRESAR NUEVOS USUARIOS</router-link>
      <br/><br/>

<div class="card">
  <div class="card-header">
    empleados
  </div>
  <div class="card-body">

    <table class="table">
      <thead>
        <tr>
          <th>ID</th>
          <th>NOMBRE</th>
          <th>correr</th>
          <th>acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr  v v-for="empleado in empleados" :key="empleado.id">
          
          <td>{{empleado.id}}</td>
           <td>{{empleado.nombre}}</td>
            <td>{{empleado.correo}}</td>
           <td>
                            <div class="btn-group" role="group" aria-label="">
                        
                           <router-link :to="{name:'Editar',params:{id:empleado.id}}" class="bnt btn-info">Editar</router-link>
                            <button type="submit"  v-on:click="borrarEmpleado(empleado.id)" class="bnt btn-danger">Borrar</button>
                 </div>
           </td>
        </tr>
       
          
        
      </tbody>
    </table>
   </div>
     </div>
     </div>

 </template>
  <script>

            export default {
                   data() {
                   return {
                  empleados:[]
                  }
                  },
               created: function () {
                         this.consultarEmpleados();
                               },
                   methods:{
                                         consultarEmpleados(){
                                               fetch("http://localhost/empleados/")
                                                  .then(respuesta=>respuesta.json())
                                                     .then((datosRespuesta)=>{

                                                            console.log(datosRespuesta);
                                                         
                                                               this.empleados=[]
                                                                   if (typeof datosRespuesta[0].success==="undefined") {
                                                                            this.empleados=datosRespuesta;
                                                                               }
                                                                 })
                                                .catch(console.log);
                                              }
                                       },
                      borrarEmpleado(id){

                               console.log(id);

                                 fetch('http://localhost/empleados/?borrar=' +id)
                                   .then(respuesta=>respuesta.json())
                                    .then((datosRespuesta)=>{

                                                   console.log(datosRespuesta)
                                                    window.location.href="listar"
                                                })

                                                  .catch(console.log)
  }
}
</script>
