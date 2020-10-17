<template>
  <div id="lateral">
    <ul class="acorh">
      <li><a href="Creacion">Creacion de Boleta</a>
        <ul>
          <li><a href="Crear">Crear Boleta</a></li>
          </ul>
      </li>
      <li><a href="Actualizacion">Actualizacion Boleta</a>
        <ul>
          <li><a href="Actualizar">actualizar boleta</a></li>
        </ul>
      </li>
      <li><a href="ConsultaBoletas">Consultas sobre Boletas</a>
        <ul>
          <li><a href="ConsultaInstitucion">Por Institucion</a></li>
          <li><a href="ConsultaEmision">Por Mes de Emision</a></li>
          <li><a href="ConsultaVencimiento">Por Mes de Vencimiento</a></li>
          <li><a href="ConsultaEstado">Por Estado</a></li>
        </ul>
      </li>
      <li><a href="Configuracion">Configuracion Cuenta</a>
        <ul>
          <li><a href="Dpersonales">Datos personales</a></li>
        </ul>
      </li>
      <li><a href="CerrarSesion">Cerrar Sesion</a>
      </li>
    </ul>
</div>
</template>

<script>
export default {
name: "BarraLateral"
}
</script>

<style scoped>
#lateral{
  width: 20%;

}
ul.acorh,
ul.acorh * {
  margin: 0;
  padding: 0;
  border: 0;
}
ul.acorh {
  margin: 10px auto;
  padding: 0;
  list-style: none;
  width: 100%;
  font-size: 18px;
}
ul.acorh li {
  list-style: none;
}
ul.acorh li a {
  display: block;
  padding: 10px 10px 10px 20px;
  background: #333;
  color: #eee;
  border-bottom: 1px solid #000;
  border-top: 1px solid #666;
  text-decoration: none;
  box-sizing: border-box;
}
ul.acorh li ul {
  max-height: 0;
  margin: 0;
  padding: 0;
  list-style: none;
  overflow: hidden;
  transition: .3s all ease-in;
}
ul.acorh li li a {
  padding: 10px 10px 10px 40px;
  background: #999;
  color: #000;
  font-size: 16px;
  border: 0;
  border-bottom: 1px solid #ccc;
  box-sizing: border-box;
}
ul.acorc li li:last-child a {
  border-bottom: 0;
}
ul.acorh li:hover ul {
  max-height: 300px;
  transition: .3s all ease-in;
}
ul.acorh li a:hover {
  background: #666;
  color: #fff;
}
</style>