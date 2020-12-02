<template>
  <div>
    <barra-nav></barra-nav>
    <div id="vertical">
    <ul id="subnav" class="metro-nav metro-nav-vertical">
      <li><a href="#" @click="mostrarModificarVerdadero" >Modificar Usuario</a></li
    ><li><a href="#" @click="mostrarEliminarVerdadero" >Eliminar Usuario</a></li>
    </ul>
  </div>
    <div id="modificar" v-show="mostrarModificar">
      <div class="container">
          <h1>Modificar datos usuario</h1>
          <p>Modificar datos de usuario y para guadar cambios presione boton "Guardar"</p>

          <label for="nombre"><b>Nombre</b></label>
          <input type="text" placeholder="Ingresa tu nombre completo" name="nombre" required>

          <label for="tipoSexo"><b>Selecccione Sexo</b></label><br>
          <select type="submit"  name="tipoSexo" required>
            <option value="Masculino">Masculino</option>
            <option value="Femenino">Femenino</option>
            <option value="Otro">Otro</option>
          </select><br>

          <label for="edad"><b>Edad</b></label><br>
          <input type="number" placeholder="Ingresa edad" name="edad" required><br>


          <label for="email"><b>Correo Electronico</b></label>
          <input type="text" placeholder="Ingresa Corre Electronico" name="email" required>

          <label for="psw"><b>Password</b></label>
          <input type="password" placeholder="Ingresa Password" name="psw" required>

          <label for="psw-repeat"><b>Repite Password</b></label>
          <input type="password" placeholder="Repite Password" name="psw-repeat" required>
        <button @click="OcultarModificar" type="button" class="cancelbtn" >Cancelar</button>
        <button @click="OcultarModificar" type="submit" class="signupbtn">Guardar</button>

        </div>
       </div>
    <div id="eliminar" v-show="mostrarEliminar">
      <h1>Eliminar cuenta usuario</h1>
      <p>Para eliminar usuario ingrese el dato solicitado y persione boton "Eliminar"</p>
      <label ><b>Para eliminar usuario ingrese Contrasenia</b></label>
      <input type="password" placeholder="Ingrese Contrasenia" name="psw-repeat" required>
      <button @click="OcultarEliminar" type="button" class="cancelbtn">Cancelar</button>
      <router-link to="/login"><button type="submit" class="signupbtn">Eliminar</button></router-link>

    </div>
  </div>

</template>

<script>
import BarraNav from "@/components/barnav";
export default {
  name: "configuracion",
  components: {BarraNav},
  el: '#vertical',
  data() {
    return {
      mostrarModificar: false,
      mostrarEliminar: false,
    };
  },
  methods: {
    mostrarModificarVerdadero() {
      this.mostrarModificar = true,
          this.mostrarEliminar = false
    },
    OcultarModificar() {
      this.mostrarModificar = false
    },
    mostrarEliminarVerdadero() {
      this.mostrarEliminar = true,
          this.mostrarModificar = false
    },
    OcultarEliminar() {
      this.mostrarEliminar = true
    },
  }
}
</script>

<style scoped>


.metro-nav {
  box-shadow: 0 5px 15px #193047;
  list-style: none;
  padding: 0;
  margin: 0;
  float: left;
  text-transform: uppercase;
  font-family: "arial", serif;
  font-size: 10px;

}
.metro-nav li a{
  display: inline-block;
  *display: inline;
  zoom: 1;
}
.metro-nav li a {
  display: block;
  padding: 10px;
  transition: all 0.1s;
}

.metro-nav.metro-nav-vertical li  a{
  display: block;
}

.metro-list li a {
  padding: 8px 12px;
}


.metro-nav {
  background: deepskyblue;
  width: 80%;
  margin: 20px auto;
}
.metro-nav li a{
  margin: 0px;
}
.metro-nav li a {
  color: Black;
  text-decoration: none;
  padding: 20px 25px;
  margin: 0;
}
.metro-nav li a:hover{
  color: white;
  background: mediumslateblue;
  box-shadow: 0px 2px 10px 5px deepskyblue;
}

.metro-nav.metro-nav-vertical {
  width: 200px;
}


.metro-pricing-table li a{
  list-style: none;
}

.metro-pricing-table .metro-pricing-pricerow td {
  padding: 20px 0;
  text-align: left;
}

/* Modificar*/
#modificar{
  font-family: "arial", serif;
  text-align: center;
  padding-left: 250px;

}
input[type=text], input[type=password] {
  width: 100%;
  padding: 15px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  background: #f1f1f1;
}
select {
  width: 100%;
  padding: 15px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  background: #f1f1f1;
}

input[type=text]:focus, input[type=password]:focus {
  background-color: #ddd;
  outline: none;
}

hr {
  border: 1px solid #f1f1f1;
  margin-bottom: 25px;
}

/* Set a style for all buttons */
button {
  background-color: mediumslateblue;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
  opacity: 0.9;
}

button:hover {
  opacity:1;
}

/* Extra styles for the cancel button */
.cancelbtn {
  padding: 14px 20px;
  background-color: #f44336;
}

/* Float cancel and signup buttons and add an equal width */
.cancelbtn, .signupbtn {
  width: 50%;
}

/* Add padding to container elements */
.container {
  padding: 16px;
}

#eliminar{
  font-family: "arial", serif;
  text-align: center;
  padding-left: 250px;

}

</style>