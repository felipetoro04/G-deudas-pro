<template>
  <div>
    <barra-nav></barra-nav>
    <div id="vertical">
      <ul id="subnav" class="metro-nav metro-nav-vertical">
        <li><a href="#" @click="mostrarModificarVerdadero">Modificar Usuario</a></li
        >
        <li><a href="#" @click="mostrarEliminarVerdadero">Eliminar Usuario</a></li>
      </ul>
    </div>
    <div id="modificar" v-show="mostrarModificar">
      <form v-on:submit.prevent="updateUser()">
        <div class="container">
          <h1>Modificar datos usuario</h1>
          <p>Modificar datos de usuario y para guadar cambios presione boton "Guardar"</p>

          <label><b>Nombre</b></label>
          <input v-model="usuario.nombre" type="text" placeholder="Ingresa tu nombre completo" required>

          <label><b>Selecccione Sexo</b></label><br>
          <select v-model="usuario.idTipoSex" required>
            <option v-for="tipoSexo in tipoSexos" v-bind:key="tipoSexo.id" v-bind:value="tipoSexo.id">{{
                tipoSexo.nombre
              }}
            </option>
          </select><br>

          <label><b>Edad</b></label><br>
          <input v-model="usuario.edad" type="number" placeholder="Ingresa edad" required><br>
          <hr>
          <label><b>Correo Electronico</b></label>
          <input v-model="usuario.email" type="text" placeholder="Ingresa Corre Electronico" required>

          <label><b>Password</b></label>
          <input v-model="usuario.contrasenia" type="password" placeholder="Ingresa Password" required>

          <button type="submit" class="signupbtn">Guardar</button>
        </div>
      </form>
    </div>
    <div id="eliminar" v-show="mostrarEliminar">
      <h1>Eliminar cuenta usuario</h1>
      <p>Para eliminar usuario ingrese el dato solicitado y persione boton "Eliminar"</p>
      <label><b>Para eliminar usuario ingrese Contrasenia</b></label>
      <input v-model="password" type="password" placeholder="Ingrese Contrasenia" name="psw-repeat" required>
      <button @click="OcultarEliminar" type="button" class="cancelbtn">Cancelar</button>

        <button type="submit" @click="deleteUser()">Eliminar</button>


    </div>
  </div>

</template>

<script>
import BarraNav from "@/components/barnav";
import axios from "axios";

export default {
  name: "configuracion",
  components: {BarraNav},
  el: '#vertical',
  data() {
    return {
      password: null,
      mostrarModificar: false,
      mostrarEliminar: false,
      usuario: {
        idTipoDoc: null,
        numeroDoc: null,
        nombre: null,
        idTipoSex: null,
        edad: null,
        email: null,
        contrasenia: null,
        idPerfil: null
      }, tipoSexos: [
        {
          id: 3,
          nombre: "Masculino"
        },
        {
          id: 4,
          nombre: "Femenino"
        },
        {
          id: 5,
          nombre: "Otro"
        }],
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

    deleteUser() {
        if(this.password === this.usuario.contrasenia) {
          axios.delete('http://127.0.0.1:8000/api/usuarios/' + this.usuario.id)
              .then( () => {
                localStorage.clear()
                alert("usaurio eliminado ")
                this.$router.push('login')
              })
        }else {
          alert("la contrasenia no es valida")
        }
    },
    updateUser() {
      console.log(this.usuario)


      axios.put('http://127.0.0.1:8000/api/usuarios/' + this.usuario.id, this.usuario)
          .then(response => {
            this.boletas.push(response.data.data);
            alert("usaurio actualizado ")
          })

    },
  },
  mounted() {
    axios.get('http://127.0.0.1:8000/api/usuarios/' + localStorage.getItem("USER_ID"))
        .then(response => {


          this.usuario = response.data.data;


        })
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

.metro-nav li a {
  display: inline-block;
  *display: inline;
  zoom: 1;
}

.metro-nav li a {
  display: block;
  padding: 10px;
  transition: all 0.1s;
}

.metro-nav.metro-nav-vertical li a {
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

.metro-nav li a {
  margin: 0px;
}

.metro-nav li a {
  color: Black;
  text-decoration: none;
  padding: 20px 25px;
  margin: 0;
}

.metro-nav li a:hover {
  color: white;
  background: mediumslateblue;
  box-shadow: 0px 2px 10px 5px deepskyblue;
}

.metro-nav.metro-nav-vertical {
  width: 200px;
}


.metro-pricing-table li a {
  list-style: none;
}

.metro-pricing-table .metro-pricing-pricerow td {
  padding: 20px 0;
  text-align: left;
}

/* Modificar*/
#modificar {
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
  opacity: 1;
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

#eliminar {
  font-family: "arial", serif;
  text-align: center;
  padding-left: 250px;

}

</style>