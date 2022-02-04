<template>
  <div class="container">
    <div class="card">
      <div class="card-header">Empleados</div>
      <div class="card-body">
        <table class="table">
          <thead>
            <tr>
              <th>ID</th>
              <th>NOMBRE</th>
              <th>CORREO</th>
              <th>AACCION</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="empleados in empleados" :Key="empleados.id">
              <td>{{ empleado.id }}</td>
              <td>{{ empleado.nombre }}</td>
              <td>{{ empleado.correo }}</td>
              <td>
                <div class="btn-group" role="group" arria-label="">
                  <button type="button" class="btn btn-info">Editar</button>
                  <button
                    type="button"
                    v-on:click="borrarEmpleado(empleado.id)"
                    class="btn btn-danger"
                  >
                    Borrar
                  </button>
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
      empleados: [],
    };
  },
  created: function () {
    this.consultarEmpleados();
  },
  methods: {
                 consultarEmpleados() {
                            fetch("http://localhost/empleados/")
                                   .then(respuesta=> respuesta.js())
                                          .then((datosRespuesta) => {

                                          console.log("datosRespuesta");
                                              this.empleados = [];
                                                    if (typeof datosRespuesta[0].success === "undefined") {
                                                           this.empleados = datosRespuesta;
                                                                 }
                                                                      })
                                                                .catch(console.log)
                                   }
      },
                                        borrarEmpleado(id) {

                                            console.log(id);

                                                fetch('http://localhost/empleados/?borrar='+id)
                                                    .then(respuesta=> respuesta.js())
                                                       .then((datosRespuesta)=>{

                                                              console.log("datosRespuesta");
                                                                 window.location.href="listar"
         
                                                  } )  

                                                  .catch(console.log)
                                                 }
    
                                      }     
                      
   


    
 

</script>
