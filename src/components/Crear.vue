<template>
    
    <div class="container">
        <div class="card">
            <div class="card-header">
               Agregar nuevo Empleado

            </div>
            <div class="card-body">
                <form  v-on:submit.prevent=" agregarRegistro">
                    <div class="from-group">
                        <label for="nombre">NOMBRE:</label>
                        <input type="text"
                        class="form-control" required name="nombre" v-model="empleado.nombre" id="nombre" aria-describedly="helpId" placehold>
                        <small id="helpId" class="form-text text-muted"> ESCRIBA EL NOMBRE DEL EMPLEADO</small>

                    </div>

                        <div class="from-group">
                        <label for="">Correo</label>
                        <input type="email"
                        class="form-control" required name="correo" id="correo" v-model="empleado.correo" aria-describedly="helpId" placehold>
                        <small id="helpId" class="form-text text-muted"> ESCRIBA EL CORREO</small>
                        </div>

                        <div class="btn-group" role="group" arria-label="">
                            <button type="submit" class="btn btn-success">agregar</button>
                             <router-link :to="{name:'Listar'}" class="btn btn-warning">Cancelar</router-link>
                             
                      </div>
                        
                            
                        
                </form>

            </div>

        </div>
    </div>
</template>
<script>
export default{
    data(){
        return{
            empleado:{}
        }
    },
    methods:{
        agregarRegistro(){
            console.log(this.empelado);


            var datosEnviar={nombre:this.empleado.nombre,correo:this.empleado.correo}

             fetch("http://localhost/empleados/?insertar=1",{
                 method:"POTS",
                 body:JSON.stringify(datosEnviar)
             })
        
       
        .then(respuesta=>respuesta.js())
        .then((datosRespuesta=>{
            console.log(datosRespuesta);
            window.location.href='listar'
        }))
    }
}
 }
</script>
