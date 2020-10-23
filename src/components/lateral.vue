<template>
  <div id="lateral">
    <nav>
    <ul>
      <li><a href="#">Creacion de Boleta</a></li>
      <li><a href="#">Actualizacion Boleta</a></li>
      <li><a href="#">Consultas sobre Boletas</a><ul>
        <li><a href="#">Por Institucion</a></li>
        <li><a href="#">Por Mes de Emision</a></li>
        <li><a href="#">Por Mes de Vencimiento</a></li>
        <li><a href="#">Por Estado</a></li>
      </ul></li>
      <li><router-link to="/login">Cerrar sesion</router-link></li>

    </ul>
    </nav>
</div>
</template>

<script>
export default {
name: "BarraLateral"
}
</script>

<style scoped>
#lateral{
  float: left;
  padding-top: 40px;
}

#lateral *{
  font-size: x-large;
  box-sizing:border-box;
  margin:0;
  padding:0;
}

li{
  list-style-type:none;
  position:relative;
  width:220px;
}

li a{
  text-decoration:none;
  display:inline-block;
  padding:5px 10px;
  width:260px;
  height:50px;
  border:1px solid mediumslateblue;
  color:#fff;
  background-color: mediumslateblue;
}

li a:hover{
  background-color: steelblue;

}
li ul ul li a{
  background-color: steelblue;
}
.more{
  display:inline-block;
  float: left;
  right:0px;
  font-size:30px;
}

nav li ul{
  display:none;
  position:absolute;
  top:0px;
  left:260px;
}

nav li:hover ul{display:block;
}
</style>