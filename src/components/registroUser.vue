<template>
  <form style="border:1px solid #ccc"  v-on:submit.prevent="addUsuario()">
    <div class="container">

      <h1>Registrate</h1>
      <p>Por favor, completa todos los campos para registrarte.</p>
      <hr>
        <label><b>Selecccione Tipo Documento</b></label><br>
        <select v-model="usuario.idTipoDoc" required>
          <option v-for="tipoDocumento in tipoDocumentos" v-bind:key="tipoDocumento.id" v-bind:value="tipoDocumento.id" >{{ tipoDocumento.nombre }}</option>
        </select><br>
        <label><b>Numero de Documento</b></label>
        <input v-model="usuario.numeroDoc" placeholder="Ingresa Numero de Documento"  type="text" required>

        <label><b>Nombre</b></label>
      <input v-model="usuario.nombre" type="text" placeholder="Ingresa tu nombre completo" required>


      <label><b>Selecccione Sexo</b></label><br>
        <select v-model="usuario.idTipoSex" required>
          <option v-for="tipoSexo in tipoSexos" v-bind:key="tipoSexo.id" v-bind:value="tipoSexo.id" >{{ tipoSexo.nombre }}</option>
        </select><br>


      <label><b>Edad</b></label><br>
      <input v-model="usuario.edad" type="number" placeholder="Ingresa edad" required><br>
        <hr>
        <label><b>Correo Electronico</b></label>
        <input v-model="usuario.email" type="text" placeholder="Ingresa Corre Electronico"  required>

        <label><b>Password</b></label>
        <input v-model="usuario.contrasenia" type="password" placeholder="Ingresa Password"  required>
      <label><b>Selecccione Perfil de usuario</b></label><br>
        <select v-model="usuario.idPerfil" required>
          <option v-for="perfil in perfiles" v-bind:key="perfil.id" v-bind:value="perfil.id" >{{ perfil.nombre }}</option>
        </select><br>




      <div class="clearfix">

        <button type="submit" class="signupbtn">Registrar</button>
        <router-link to="/login"><button   class="cancelbtn">Cancel</button></router-link>

      </div>
    </div>
  </form>
</template>

<script>
import axios from "axios";

export default {
  name: "registroUser",

  data() {
    return {
      usuario: {
        idTipoDoc: null,
        numeroDoc: null,
        nombre: null,
        idTipoSex: null,
        edad: null,
        email: null,
        contrasenia: null,
        idPerfil: null
      },

      tipoDocumentos: [
        {
          id: 1,
          nombre: "Cedula de identidad"
        },
        {
          id: 2,
          nombre: "Pasaporte"
        }],
      tipoSexos: [
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
      perfiles: [
        {
          id: 1,
          nombre: "Administrador"
        },
        {
          id: 2,
          nombre: "Usuario"
        }],
    }
  },
  methods: {
        addUsuario () {
          axios.post('http://127.0.0.1:8000/api/usuarios/', this.usuario)
              .then(response => {
               // this.usuarios.push(response.data.data)
                console.log(
                    response
                )
                this.$router.push('login')

              })
        },

      }
    }

</script>

<style scoped>
* {box-sizing: border-box}

/* Full-width input fields */
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
  float: left;
  width: 50%;
}

/* Add padding to container elements */
.container {
  padding: 16px;
}

/* Clear floats */
.clearfix::after {
  content: "";
  clear: both;
  display: table;
}

</style>