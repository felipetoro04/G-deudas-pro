<template>
<div id="creacion">
  <barra-nav></barra-nav>
  <div class="form-style-5">
    <form>
      <fieldset>
        <legend>Datos de Boleta</legend>
        <label>Ingresar Nombre de Institucion</label>
        <input type="text" name="field1" placeholder="Nombre de Institucion *">
        <label>Ingresar Numero de Boleta</label>
        <input type="varchar" name="field2" placeholder="Numero de Boleta *">
        <label>Seleccionar Imagen</label>
        <button>seleccionar</button><input type="image" name="field3" alt="ImagenBoleta">
        <label>Ingresar Monto a Cancelar</label>
        <input type="number" name="field4" placeholder="Monto a Cancelar *">
        <label>Ingresar Fecha Emision</label>
        <input type="date" name="field5" placeholder="Fecha Emision *">
        <label>Ingresar Fecha Vencimiento</label>
        <input type="date" name="field6" placeholder="Fecha Vencimiento *">
        <label for="estados">Seleccionar Estado de Boleta:</label>
        <select id="estados" name="field4">
          <optgroup label="Estados">
            <option value="activo">Activo</option>
            <option value="atrasada">Atrasada</option>
          </optgroup>
        </select>
      </fieldset>

      <input type="submit" value="Apply" />
    </form>
  </div>




</div>
</template>

<script>
import BarraNav from "@/components/barnav";
export default {
name: "creacionBoleta",
  components: {BarraNav}
}
</script>

<style type="text/css">
#creacion{
padding-top: 200;
}
.form-style-5{
  max-width: 500px;
  padding: 10px 20px;
  background: #f4f7f8;
  margin: 10px auto;
  padding: 20px;
  background: #f4f7f8;
  border-radius: 8px;
  font-family: Georgia, "Times New Roman", Times, serif;
}

.form-style-5 fieldset{
  border: none;
}
.form-style-5 legend {
  font-size: 1.4em;
  margin-bottom: 10px;
}
.form-style-5 label {
  display: block;
  margin-bottom: 8px;
}
.form-style-5 input[type="text"],
.form-style-5 input[type="date"],
.form-style-5 input[type="datetime"],
.form-style-5 input[type="varchar"],
.form-style-5 input[type="number"],
.form-style-5 input[type="search"],
.form-style-5 input[type="time"],
.form-style-5 input[type="time"],
.form-style-5 input[type="image"],
.form-style-5 textarea,
.form-style-5 select {
  font-family: Georgia, "Times New Roman", Times, serif;
  background: rgba(255,255,255,.1);
  border: none;
  border-radius: 4px;
  font-size: 15px;
  margin: 0;
  outline: 0;
  padding: 10px;
  width: 100%;
  box-sizing: border-box;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  background-color: #e8eeef;
  color:#8a97a0;
  -webkit-box-shadow: 0 1px 0 rgba(0,0,0,0.03) inset;
  box-shadow: 0 1px 0 rgba(0,0,0,0.03) inset;
  margin-bottom: 30px;
}
.form-style-5 input[type="text"]:focus,
.form-style-5 input[type="date"]:focus,
.form-style-5 input[type="datetime"]:focus,
.form-style-5 input[type="varchar"]:focus,
.form-style-5 input[type="number"]:focus,
.form-style-5 input[type="search"]:focus,
.form-style-5 input[type="image"]:focus,
.form-style-5 input[type="time"]:focus,
.form-style-5 input[type="url"]:focus,
.form-style-5 textarea:focus,
.form-style-5 select:focus{
  background: #d2d9dd;
}
.form-style-5 select{
  -webkit-appearance: menulist-button;
  height:35px;
}


.form-style-5 input[type="submit"],
.form-style-5 input[type="button"]
{
  position: relative;
  display: block;
  padding: 19px 39px 18px 39px;
  color: #FFF;
  margin: 0 auto;
  background: #1abc9c;
  font-size: 18px;
  text-align: center;
  font-style: normal;
  width: 100%;
  border: 1px solid #16a085;
  border-width: 1px 1px 3px;
  margin-bottom: 10px;
}
.form-style-5 input[type="submit"]:hover,
.form-style-5 input[type="button"]:hover
{
  background: #109177;
}
</style>