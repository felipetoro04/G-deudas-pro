<template>
  <div>

    <barra-nav :funcion="this.mostrarCreacion"/>
    <div  class="content-table" style="margin-top: 20px">
      Bienvenido : {{userEmail}}
    </div>
    <div id='Cuerpo' align="center">
      <Header></Header>
      <h1 v-if="hasError">API no disponible.</h1>

      <div v-else>
        <h1 v-if="loading">Cargando Boletas...</h1>
        <div v-else>
          <h1>Boletas</h1>

          <div >
            <form class="content-data" v-show ="mostrarCR">
            Institucion:
            <select v-model="boleta.idInstitucion" required>
              <option v-for="institucion in instituciones" v-bind:key="institucion.id" v-bind:value="institucion.id" >{{ institucion.nombre }}</option>
            </select>
            Numero de Boleta:<input v-model="boleta.numeroBoleta" type="text" required>
            Fecha de Emision:<input v-model="boleta.fechaEmision" type="date" required>
            Fecha de Vencimiento:<input v-model="boleta.fechaVencimiento" type="date" required>
            Monto a Pagar:<input v-model="boleta.montoPagar" type="int" required>
            Estado de Boleta:
            <select v-model="boleta.idEstado" required>
              <option v-for="estado in estados" v-bind:key="estado.id" v-bind:value="estado.id">{{ estado.nombre }}</option>
            </select>
            <button class="button-add" @click="addBoleta()">Agregar</button>
            <button class="button-clean" @click="clean()">Limpiar</button>
              <button class="button-clean" @click="ocultarCreacion">Cancelar</button>

            </form>
          </div>
          <div class="content-table">
            <table class="blueTable" >
              <tr>
                <th>Institucion</th>
                <th>Numero de Boleta</th>
                <th>Fecha de Emision</th>
                <th>Fecha de Vencimiento</th>
                <th>Monto de Pagar</th>
                <th>Estado de Boleta</th>
                <th>Acciones</th>

              </tr>
              <tr v-for="boleta in boletas" :key="boleta.id">
                <td>
                  {{ obtenerInstitucion(boleta.idInstitucion) }}
                </td>
                <td>
                  {{ boleta.numeroBoleta }}
                </td>
                <td>
                  {{ boleta.fechaEmision }}
                </td>
                <td>
                  {{ boleta.fechaVencimiento }}
                </td>
                <td>
                  {{ boleta.montoPagar }}
                </td>
                <td>
                  {{obtenerEstado(boleta.idEstado) }}
                </td>
                <td>
                  <button class="button-update"  @click="updateBoleta(boleta);mostrarCreacion()">Actualizar</button>
                  <button class="button-delete" @click="removeBoleta(boleta.id)">Eliminar</button>

                </td>
              </tr>
            </table>

          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>

import BarraNav from "@/components/barnav";
import axios from "axios";

export default {
  name: "Cuerpo",
  components: {BarraNav},
  el: '#creacionBoleta',
  data() {
    return {
      mostrarCR: false,
      boletas: null,
      hasError: false,
      loading: true,
      boleta: {
        idInstitucion: null,
        numeroBoleta: null,
        fechaEmision: null,
        fechaVencimiento: null,
        montoPagar: null,
        idEstado: null,
        idUsuario: 1
      },
      userEmail: null,
      instituciones: [
        {
          id: 1,
          nombre: "falabella"
        },
        {
          id: 2,
          nombre: "paris"
        },
        {
          id: 3,
          nombre: "ripley"
        }],
      estados: [
        {
          id: 6,
          nombre: "Por Pagar"
        },
        {
          id: 7,
          nombre: "Atrasada"
        }],
      creacion: true
    };
  },
  methods: {
    ocultarCreacion() {
      this.mostrarCR = false
    },
    mostrarCreacion() {
      this.mostrarCR = true
    },
    removeBoleta: function (id) {
      axios.delete('http://127.0.0.1:8000/api/boletas/' + id)
          .then(() => {
            this.boletas = this.boletas.filter(boleta => boleta.id !== id);
          });
    },
    addBoleta() {

      if (this.creacion) {


        axios.post('http://127.0.0.1:8000/api/boletas/', this.boleta)
            .then(response => {
              this.boletas.push(response.data.data);
              alert("boleta Añadida")
              this.clean();
            })
      } else {


        axios.put('http://127.0.0.1:8000/api/boletas/' + this.boleta.id, this.boleta)
            .then(response => {
              this.boletas.push(response.data.data);
              alert("Boleta Actualizada")
            })
        this.creacion = true;
        this.clean();
      }


    },

    updateBoleta(boleta) {
      this.boleta = boleta;
      this.creacion = false;
    },
    clean() {
      this.boleta = {
        idInstitucion: null,
        numeroBoleta: null,
        fechaEmision: null,
        fechaVencimiento: null,
        montoPagar: null,
        idEstado: null,
        idUsuario: 1
      };
      this.creacion = true;
    },
    obtenerInstitucion( id ) {


      for (const key in this.instituciones) {
            if (this.instituciones[key].id.toString() === id.toString()){
              return this.instituciones[key].nombre;
            }
      }

      return 'No hay informacion'


      //return instituciones.filter(institucion => institucion.id === id)[0].nombre;
    },
    obtenerEstado( id ) {

      for (const key in this.estados) {
        if (this.estados[key].id.toString() === id.toString()){
          return this.estados[key].nombre;
        }
      }

      return 'No hay informacion'

    },


  },

  mounted() {
    axios
        .get('http://127.0.0.1:8000/api/boletas')
        .then(response => (this.boletas = response.data.data))
        // eslint-disable-next-line no-unused-vars
        .catch(error => this.hasError = true)
        .finally(() => this.loading = false)

         this.userEmail = localStorage.getItem('USER_EMAIL')
  }

}
</script>

<style>

.content-data {
  -webkit-box-shadow: 2px 2px 5px 0px rgba(0,0,0,0.75);
  -moz-box-shadow: 2px 2px 5px 0px rgba(0,0,0,0.75);
  box-shadow: 2px 2px 5px 0px rgba(0,0,0,0.75);
  border-radius: 5px;
  margin-bottom: 20px;
  padding: 20px;
  display: grid;
  margin-left: 100px;
  margin-right: 100px;
}

.content-table{
  -webkit-box-shadow: 2px 2px 5px 0px rgba(0,0,0,0.75);
  -moz-box-shadow: 2px 2px 5px 0px rgba(0,0,0,0.75);
  box-shadow: 2px 2px 5px 0px rgba(0,0,0,0.75);
  border-radius: 5px;
  margin-bottom: 20px;
  padding: 20px;
}

table.blueTable {
  border: 1px solid #1C6EA4;
  background-color: #EEEEEE;
  width: 100%;
  text-align: left;
  border-collapse: collapse;
}
table.blueTable td, table.blueTable th {
  border: 1px solid #AAAAAA;
  padding: 3px 2px;
}
table.blueTable tbody td {
  font-size: 13px;
}
table.blueTable tr:nth-child(even) {
  background: #c0bae0;
}
table.blueTable thead {
  background: #1C6EA4;
  background: -moz-linear-gradient(top, #5592bb 0%, #327cad 66%, #1C6EA4 100%);
  background: -webkit-linear-gradient(top, #5592bb 0%, #327cad 66%, #1C6EA4 100%);
  background: linear-gradient(to bottom, #5592bb 0%, #327cad 66%, #1C6EA4 100%);
  border-bottom: 2px solid #444444;
}
table.blueTable thead th {
  font-size: 15px;
  font-weight: bold;
  color: #FFFFFF;
  border-left: 2px solid #D0E4F5;
}
table.blueTable thead th:first-child {
  border-left: none;
}

table.blueTable tfoot {
  font-size: 14px;
  font-weight: bold;
  color: #FFFFFF;
  background: #D0E4F5;
  background: -moz-linear-gradient(top, #dcebf7 0%, #d4e6f6 66%, #D0E4F5 100%);
  background: -webkit-linear-gradient(top, #dcebf7 0%, #d4e6f6 66%, #D0E4F5 100%);
  background: linear-gradient(to bottom, #dcebf7 0%, #d4e6f6 66%, #D0E4F5 100%);
  border-top: 2px solid #444444;
}
table.blueTable tfoot td {
  font-size: 14px;
}
table.blueTable tfoot .links {
  text-align: right;
}
table.blueTable tfoot .links a{
  display: inline-block;
  background: #1C6EA4;
  color: #FFFFFF;
  padding: 2px 8px;
  border-radius: 5px;
}

.button-add{
  margin-top: 5px;
  margin-bottom: 5px;
}
.button-clean{
  margin-bottom: 5px;
}
.button-update{
  margin-right: 5px;
}
.button-delete{
  margin-right: 5px;
}
</style>