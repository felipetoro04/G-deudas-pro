<template>

  <div id="creacionBoleta" class="container">
      <section class="form" >
        <form action="" class="text-center">
          <label><b>Ingresa Institucion</b></label><br>
          <input v-model="Institucion" @keyup.enter="creacion" type="text" class="form-control" placeholder="Institucion" name="Institucion"><br>
          <label><b>Ingresa Numero de Boleta</b></label><br>
          <input v-model="NumeroBoleta" @keyup.enter="Creacion" type="text" class="form-control" placeholder="Numero de Boleta"><br>
          <label><b>Ingresa Monto a Cancelar</b></label><br>
          $<input v-model="monto" @keyup.enter="Creacion" type="number" class="form-control" placeholder="Monto a Cancelar"><br>
          <label><b>Ingresa Fecha de Emisión</b></label><br>
          <input v-model="FechaE" @keyup.enter="Creacion" type="date" class="form-control" placeholder="Fecha de Emisión"><br>
          <label><b>Ingresa Fecha de Vencimiento</b></label><br>
          <input v-model="FechaV" @keyup.enter="Creacion" type="date" class="form-control" placeholder="Fecha de Vencimiento"><br>
          <label><b>Selecciona Estado</b></label><br>
          <select v-model="Estado" @keyup.enter="Creacion" type="text" class="form-control" placeholder="Estado">
            <option value="Activo">Activo</option>
            <option value="Vencida">Vencida</option>
          </select><br>


          <input @click="Creacion" type="button" value="Añadir" class="btn btn-success">
        </form>
      </section>

    <section class="data">
        <table >
          <caption>Ultimos Movimientos</caption>
          <thead>
          <tr>
            <th scope="col">Institucion</th>
            <th scope="col">Numero de Boleta</th>
            <th scope="col" type="image">Boleta </th>
            <th scope="col">Monto a Cancelar</th>
            <th scope="col">Fecha de Emisión</th>
            <th scope="col">Fecha de Vencimiento</th>
            <th scope="col">Estado</th>
          </tr>
          </thead>
          <tbody>
          <tr v-for="(boleta,id) in Boletas" :key="id">
            <td>{{boleta.Institucion}}</td>
            <td>{{boleta.NumeroBoleta}}</td>
            <td><input class="seleccionarIMG"  v-on:change="imagen_Boleta"  type="file" accept="image/*"></td>
            <td>{{boleta.monto}}</td>
            <td>{{boleta.FechaE}}</td>
            <td>{{boleta.FechaV}}</td>
            <td>{{boleta.Estado}}</td>
          </tr>

          </tbody>
        </table>
    </section>
    </div>

</template>

<script>

export default {
    name: "Cuerpo",
    el: '#creacionBoleta',
  data() {
    return {
      Institucion: '',
      NumeroBoleta: '',
      imagen_Boleta: '',
      monto: '',
      FechaE: '',
      FechaV: '',
      Estado: '',
      Boletas: [],

    };
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
.seleccionarIMG {
  width:135px;
  text-align: center;
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
