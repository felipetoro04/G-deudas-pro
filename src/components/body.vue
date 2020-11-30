<template>
  <div>
  <barra-nav :funcion="this.mostrarCreacion"/>
  <div id="creacionBoleta" class="container">
         <section class="form" v-show="mostrarCR">
        <form action="" class="text-center">
          <label><b>Ingresa Institucion</b></label><br>
          <input v-model="Institucion" @keyup.enter="creacion" type="text" class="form-control" placeholder="Institucion" name="Institucion"><br>
          <label><b>Ingresa Numero de Boleta</b></label><br>
          <input v-model="NumeroBoleta" @keyup.enter="Creacion" type="text" class="form-control" placeholder="Numero de Boleta"><br>
          <label><b>Ingresa Monto a Cancelar</b></label><br>
          <input v-model="monto" @keyup.enter="Creacion" type="number" class="form-control" placeholder="Monto a Cancelar"><br>
          <label><b>Ingresa Fecha de Emisión</b></label><br>
          <input v-model="FechaE" @keyup.enter="Creacion" type="date" class="form-control" placeholder="Fecha de Emisión"><br>
          <label><b>Ingresa Fecha de Vencimiento</b></label><br>
          <input v-model="FechaV" @keyup.enter="Creacion" type="date" class="form-control" placeholder="Fecha de Vencimiento"><br>
          <label><b>Selecciona Estado</b></label><br>
          <select v-model="Estado" @keyup.enter="Creacion" type="text" class="form-control" placeholder="Estado">
            <option value="PorPagar">Por Pagar</option>
            <option value="Atrasada">Atrasada</option>
          </select><br>
          <input @click="Creacion" type="button" value="Añadir" class="btn btn-success">
          <input  @click="ocultarCreacion" type="button" value="Cancelar" class="btn btn-success">
        </form>
      </section>
    <section class="data">
        <table >
          <caption>Ultimos Movimientos</caption>
          <thead>
          <tr>
            <th scope="col">id</th>
            <th scope="col">Institucion</th>
            <th scope="col">Numero de Boleta</th>

            <th scope="col">Monto a Cancelar</th>
            <th scope="col">Fecha de Emisión</th>
            <th scope="col">Fecha de Vencimiento</th>
            <th scope="col">Estado</th>
          </tr>
          </thead>
          <tbody>
          <tr v-for="(boleta,index) in Boletas" :key="index">
            <td>{{boleta.Id}}</td>


            <td>
              <span v-if="formActualizar && idActualizar == index">
                <input v-model="InstitucionActualizar" type="text" class="form-control">
              </span>
              <span v-else>
                {{boleta.Institucion}}
              </span>
            </td>
            <td>
              <span v-if="formActualizar && idActualizar == index">
                <input v-model="NumeroBoletaActualizar" type="text" class="form-control">
              </span>
              <span v-else>
                {{boleta.NumeroBoleta}}
              </span>
            </td>
            <td>
              <span v-if="formActualizar && idActualizar == index">
                <input v-model="montoActualizar" type="text" class="form-control">
              </span>
              <span v-else>
                {{boleta.monto}}
              </span>
            </td>
            <td>
              <span v-if="formActualizar && idActualizar == index">
                <input v-model="FechaEActualizar" type="text" class="form-control">
              </span>
              <span v-else>
                {{boleta.FechaE}}
              </span>
            </td>
            <td>
              <span v-if="formActualizar && idActualizar == index">
                <input v-model="FechaVActualizar" type="text" class="form-control">
              </span>
              <span v-else>
                {{boleta.FechaV}}
              </span>
            </td>
            <td>
              <span v-if="formActualizar && idActualizar == index">
                <input v-model="EstadoActualizar" type="text" class="form-control">
              </span>
              <span v-else>
                {{boleta.Estado}}
              </span>
            </td>


            <td>
              <!-- Botón para guardar la información actualizada -->
              <span v-if="formActualizar && idActualizar == index">
                <button @click="guardarActualizacion(index)" class="btn btn-success">Guardar</button>
                <button @click="CancelarButton(index)" class="btn btn-danger">Cancelar</button>
              </span>
              <span v-else >
                <!-- Botón para mostrar el formulario de actualizar -->
                <button @click="verFormActualizar(index)" class="btn btn-warning">Modificar</button>
                <!-- Botón para borrar -->
                <button v-show="mostrarModiEli" @click="borrarBoleta(index)" class="btn btn-danger">Borrar</button>
                <button v-show="mostrarM_E" @click="ocultarModiEli"  class="btn btn-back">Cancelar</button>


              </span>
            </td>
          </tr>
          </tbody>
        </table>
    </section>
    </div>
  </div>
</template>
<script>

import BarraNav from "@/components/barnav";
export default {
  name: "Cuerpo",
  components: {BarraNav},
  el: '#creacionBoleta',
  data() {
    return {
      Id: '',
      Institucion: '',
      NumeroBoleta: '',
      monto: '',
      FechaE: '',
      FechaV: '',
      Estado: '',
      Boletas: [],
      formActualizar: false,
      // La posición de tu lista donde te gustaría actualizar
      idActualizar: -1,
      InstitucionActualizar: '',
      NumeroBoletaActualizar: '',
      montoActualizar: '',
      FechaEActualizar: '',
      FechaVActualizar: '',
      EstadoActualizar: '',
      mostrarCR:false,
      mostrarM_E:false,
    };
  },
  methods: {
    Creacion: function () {
      this.Boletas.push({
        Id: +new Date(),
        Institucion: this.Institucion,
        NumeroBoleta: this.NumeroBoleta,
        monto: this.monto,
        FechaE: this.FechaE,
        FechaV: this.FechaV,
        Estado: this.Estado,
      });
      this.Institucion = '';
      this.NumeroBoleta = '';
      this.monto = '';
      this.FechaE = '';
      this.FechaV = '';
      this.Estado = '';
    },
    verFormActualizar: function (boleta_id) {
      // Antes de mostrar el formulario de actualizar, rellenamos sus campos
      this.idActualizar = boleta_id;
      this.InstitucionActualizar = this.Boletas[boleta_id].Institucion;
      this.NumeroBoletaActualizar = this.Boletas[boleta_id].NumeroBoleta;
      this.montoActualizar = this.Boletas[boleta_id].monto;
      this.FechaEActualizar = this.Boletas[boleta_id].FechaE;
      this.FechaVActualizar = this.Boletas[boleta_id].FechaV;
      this.EstadoActualizar = this.Boletas[boleta_id].Estado;
      // Mostramos el formulario
      this.formActualizar = true;
    },
    borrarBoleta: function (boleta_id) {
      // Borramos de la lista
      this.Boletas.splice(boleta_id, 1);
    },
    guardarActualizacion: function (boleta_id) {
      // Ocultamos nuestro formulario de actualizar
      this.formActualizar = false;
      // Actualizamos los datos
      this.Boletas[boleta_id].Institucion = this.InstitucionActualizar;
      this.Boletas[boleta_id].NumeroBoleta = this.NumeroBoletaActualizar;
      this.Boletas[boleta_id].monto = this.montoActualizar;
      this.Boletas[boleta_id].FechaE = this.FechaEActualizar;
      this.Boletas[boleta_id].FechaV = this.FechaVActualizar;
      this.Boletas[boleta_id].Estado = this.EstadoActualizar;
    },
    CancelarButton: function () {
      this.formActualizar = false;
    },
    mostrarCreacion(){
      this.mostrarCR = true
    },
    ocultarCreacion(){
      this.mostrarCR = false
    },
    mostrarModiEli(){
      this.mostrarM_E = true
    },
    ocultarModiEli(){
      this.mostrarM_E = false
    },
  }
}
</script>
<style>
.form{
  font-family: "Open Sans", sans-serif;
  text-align: center;
  margin: .5em 0 .75em;
  }
.form label,input,select,option{
  text-align: center;
  line-height: 1.25;
  padding: .625em;
  width: 30%;
  border-bottom: 3px solid #ddd;
   margin-bottom: .625em

}

#creacionBoleta{
  padding-top: 70px;
}
table {
  font-family: "Open Sans", sans-serif;
  line-height: 1.25;
  border: 1px solid #ccc;
  border-collapse: collapse;
  margin: 0;
  padding: 0;
  width: 100%;
  table-layout: fixed;

}

table caption {
  font-size: 1.5em;
  margin: .5em 0 .75em;
}

table tr {
  background-color: #f8f8f8;
  border: 1px solid #ddd;
  padding: .35em;
}

table th,
table td {
  padding: .625em;
  text-align: center;
}

table th {
  font-size: .85em;
  letter-spacing: .1em;
  text-transform: uppercase;
}

@media screen and (max-width: 600px) {
  table {
    border: 0;
  }

  table caption {
    font-size: 1.3em;
  }

  table thead {
    border: none;
    clip: rect(0 0 0 0);
    height: 1px;
    margin: -1px;
    overflow: hidden;
    padding: 0;
    position: absolute;
    width: 1px;
  }

  table tr {
    border-bottom: 3px solid #ddd;
    display: block;
    margin-bottom: .625em;
  }

  table td {
    border-bottom: 1px solid #ddd;
    display: block;
    font-size: .8em;
    text-align: right;
  }

  table td::before {
    /*
    * aria-label has no advantage, it won't be read inside a table
    content: attr(aria-label);
    */
    content: attr(data-label);
    float: left;
    font-weight: bold;
    text-transform: uppercase;
  }

  table td:last-child {
    border-bottom: 0;
  }
}


</style>
