<template>

  <div id="creacionBoleta" class="container">
    <Vue></Vue>

          <!-- Formulario para añadir pacientes -->
      <section class="form">
        <form action="" class="text-center">
        <input v-model="Institucion" @keyup.enter="creacion" type="text" class="form-control" placeholder="Institucion">
          <input v-model="NumeroBoleta" @keyup.enter="Creacion" type="text" class="form-control" placeholder="Numero de Boleta">
          <input v-model="imagen_Boleta" @keyup.enter="Creacion" type="text" class="form-control" placeholder="Boleta">
          <input v-model="monto" @keyup.enter="Creacion" type="text" class="form-control" placeholder="Monto a Cancelar">
          <input v-model="FechaE" @keyup.enter="Creacion" type="text" class="form-control" placeholder="Fecha de Emisión">
          <input v-model="FechaV" @keyup.enter="Creacion" type="text" class="form-control" placeholder="Fecha de Vencimiento">
          <input v-model="Estado" @keyup.enter="Creacion" type="text" class="form-control" placeholder="Estado">

          <!--<input id="image" v-on:change="imagen_Boleta" type="file"> -->
                <!-- Botón para añadir -->

          <button v-on:click="Creacion"> agregar</button>
        </form>
      </section>

    <section class="data">
        <table >
          <caption>Ultimos Movimientos</caption>
          <thead>
          <tr>
            <th scope="col">Institucion</th>
            <th scope="col">Numero de Boleta</th>
            <th scope="col">Boleta</th>
            <th scope="col">Monto a Cancelar</th>
            <th scope="col">Fecha de Emisión</th>
            <th scope="col">Fecha de Vencimiento</th>
            <th scope="col">Estado</th>
          </tr>
          </thead>
          <tbody>
          <tr v-for="(boleta) in Boletas" v-bind:key="boleta.id">
            <td>{{boleta.id}}</td>
          </tr>
          </tbody>
        </table>
    </section>
    </div>

</template>

<script>
import Vue from 'vue'
export default {
name: "Cuerpo"
}
// eslint-disable-next-line no-undef
  new Vue({
    el: '#body',
        data: {
      Institucion: '',NumeroBoleta: '',imagen_Boleta: '',monto:'', FechaE:'', FechaV:'',Estado:'',

      // Lista de boletas
      Boletas: []
    },
    methods: {
      Creacion: function () {
        this.Boletas.push({
          Institucion: this.Institucion,
          NumeroBoleta: this.NumeroBoleta,
          imagen_Boleta: this.imagen_Boleta,
          monto: this.monto,
          FechaE: this.FechaE,
          FechaV: this.FechaV,
          Estado: this.Estado,
        });
        // Vaciamos el formulario de añadir
        this.Institucion = '';
        this.NumeroBoleta = '';
        this.imagen_Boleta = '';
        this.monto = '';
        this.FechaE = '';
        this.FechaV = '';
        this.Estado = '';
      },
    },
  });


</script>











<style>
#creacionBoleta{
  padding-top: 150px;
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
