<template>
  <div id="bar">
    <div class="logo">
      <img src="../assets/images/logo.png">
    </div>
  <div class="links">
    <ul>
      <li><router-link to="/home">Inicio</router-link></li>
      <li><router-link to="/Politicas_de_privacidad">Nosotros</router-link></li>
      <li><router-link to="/Politicas_de_privacidad">Politicas de privacidad</router-link></li>
      </ul>
    </div>
  </div>

</template>

<script>
export default {
name: "BarraNav",
  }

</script>

<style>

#bar img{
  float: left;
  width: 55px;
  height: 55px;
  border: solid 1px #000000;
}

#bar .links{
  font-size: x-large;
  overflow: auto;
  border: solid 1px #000000;
  }

#bar .links ul {

  list-style-type: none;
  margin: 0;
  padding-left: 40%;
  overflow: hidden;
  }

#bar .links li {
  float: left;
  background-color: mediumslateblue;
}

#bar .links li a {
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

/* Change the link color to #111 (black) on hover */
#bar .links li a:hover {
  background-color: steelblue;
}


</style>