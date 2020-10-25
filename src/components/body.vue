<template>
  <div id="tabla">
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
    <tr>
      <td data-label="Institucion">CGE</td>
      <td data-label="Numero de Boleta">181273162371263</td>
      <td data-label="Boleta"><input type="image" src="" alt="Submit"></td>
      <td data-label="Monto a Cancelar">$20.000</td>
      <td data-label="Fecha de Emisión">10/01/2020</td>
      <td data-label="Fecha de Vencimiento">10/31/2020</td>
      <td data-label="Estado">ACTIVO</td>
    </tr>
    <tr>
      <td data-label="Institucion">CGE</td>
      <td data-label="Numero de Boleta">222992929</td>
      <td data-label="Boleta"><input type="image" src="" alt="Submit"></td>
      <td data-label="Monto a Cancelar">$20.000</td>
      <td data-label="Fecha de Emisión">10/01/2020</td>
      <td data-label="Fecha de Vencimiento">10/31/2020</td>
      <td data-label="Estado">ACTIVO</td>
    </tr>
    <tr>
      <td data-label="Institucion">CGE</td>
      <td data-label="Numero de Boleta">23465465465</td>
      <td data-label="Boleta"><input type="image" src="" alt="Submit"></td>
      <td data-label="Monto a Cancelar">$20.000</td>
      <td data-label="Fecha de Emisión">10/01/2020</td>
      <td data-label="Fecha de Vencimiento">10/31/2020</td>
      <td data-label="Estado">ACTIVO</td>
    </tr>
    <tr>
      <td data-label="Institucion">CGE</td>
      <td data-label="Numero de Boleta">4564565</td>
      <td data-label="Boleta"><input type="image" src="" alt="Submit"></td>
      <td data-label="Monto a Cancelar">$20.000</td>
      <td data-label="Fecha de Emisión">10/01/2020</td>
      <td data-label="Fecha de Vencimiento">10/31/2020</td>
      <td data-label="Estado">ACTIVO</td>
    </tr>
    </tbody>
  </table>
    </div>
</template>

<script>
export default {
name: "Cuerpo"
}
</script>
<style>
#tabla{
  padding-top: 100px;
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
