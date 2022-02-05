<template>
  


<nav class="navbar navbar-expand navbar-light bg-light">
    <div class="nav navbar-nav">

       <router-link to="/crear" class="nav-link">Crear</router-link>
        <router-link to="/listar" class="nav-link">Usuarios</router-link>

       </div>
</nav>



<br/>



    <!-- <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> -->
     <!-- <router-link to="/crear">Crear</router-link>
|
      
|
       <router-link to="/editar">Editar</router-link> -->
 
  <router-view/>
</template>

