<template>
  <div>
    <barra-nav></barra-nav>
    <div id="vertical">
      <ul id="subnav" class="metro-nav metro-nav-vertical">
        <li><a href="#" @click="mostrarConsultasUsuariosVerdadero">Consultas Sobre Usuarios</a></li
        ><li><a href="#" @click="mostrarConsultasBoletasVerdadero">Consultas Sobre Boletas</a></li>
      </ul>
    </div>
    <div id="Conuser" v-show="mostrarConsultasUsuarios">
      <ul>
        <li><button>CANTIDAD DE USUARIOS LOGEADOS HOY</button></li>
        <li><button>PROMEDIO DE BOLETAS POR USUARIOS</button></li>
      </ul>

    </div>
    <div id="Condbol" v-show="mostrarConsultasBoletas">
    <div id = "selector">
      <h1>Seleccione su parametro de busqueda</h1>
      <select v-model="Estado" @keyup.enter="Creacion" type="text" class="form-control" placeholder="Parametro de busqueda">
        <option>Institucion</option>
        <option>Estado de Boleta</option>
        <option>Numero de boleta</option>
        <option>Mes de Emision</option>
        <option>Mes de Vencimiento</option>
      </select><br>
    </div>
      <div id="cover">
        <form method="get" action="">
          <div class="tb">
            <div class="td">
              <input type="text" placeholder="Buscar" required>
            </div>
            <div class="td" id="s-cover">
              <button type="submit">
                <div id="s-circle"></div>
                <span></span>
              </button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>



</template>

<script>
import BarraNav from "@/components/barnav";
export default {
name: "consultas",
  components: {BarraNav},
  data() {
    return {
      mostrarConsultasUsuarios: false,
      mostrarConsultasBoletas: false,
    };
  },
  methods: {
    mostrarConsultasUsuariosVerdadero() {
      this.mostrarConsultasUsuarios = true,
          this.mostrarConsultasBoletas = false
    },
    OcultarConsultaUsuario() {
      this.mostrarConsultasUsuarios = false
    },
    mostrarConsultasBoletasVerdadero() {
      this.mostrarConsultasBoletas = true,
          this.mostrarConsultasUsuarios = false
    },
    OcultarConsultaBoleta() {
      this.mostrarConsultasBoletas = true
    },
  }
}
</script>

<style scoped>
/*Barra lateral*/
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
/*Consultas sobre Usuarios*/
#Conuser{
    padding-left: 400px;
  padding-top: 100px;

}
#Conuser button {
  text-align: center;
  text-transform: uppercase;
  cursor: pointer;
  font-size: 10px;
  background-color: mediumslateblue;
  border: none;
  color: #fff;
  padding: 20px;
  width: 200px;
  transition-duration: 0.4s;
  overflow: hidden;
  box-shadow: 0 5px 15px #193047;
  border-radius: 4px;
}

#Conuser li{
  display:inline-block;
  border:none;
  text-align:center;
  }

#Conuser button:hover{
  background: #fff;
  box-shadow: 0px 2px 10px 5px #1abc9c;
  color: #000;
  cursor: pointer;
}
#Conuser button:after{
  content: "";
  background: #1abc9c;
  display: block;
  position: absolute;
  padding-top: 300%;
  padding-left: 350%;
  margin-left: -20px !important;
  margin-top: -120%;
  opacity: 0;
  transition: all 0.8s

}
#Conuser button:active:after{
  padding: 0;
  margin: 0;
  opacity: 1;
  transition: 0s
}
#Conuser button:focus{outline:0;}


/*Consultas sobre boletas*/


#selector{
  text-align: center;
  padding-top: 80px;
}

*
{
  outline: none;
}
select{
  text-align: center;
}
html, body
{
  height: 100%;
  min-height: 100%;
}

body
{
  margin: 0;
  background-color: #ffd8d8;
}

.tb
{
  display: table;
  width: 100%;
}

.td
{
  display: table-cell;
  vertical-align: middle;
}

input, button
{
  color: #fff;
  font-family: Nunito;
  padding: 0;
  margin: 0;
  border: 0;
  background-color: transparent;
}

#cover
{
  position: absolute;
  top: 50%;
  left: 0;
  right: 0;
  width: 550px;
  padding: 35px;
  margin: -83px auto 0 auto;
  background-color: mediumslateblue;
  border-radius: 20px;
  box-shadow: 0 10px 40px mediumslateblue, 0 0 0 20px #ffffffeb;
  transform: scale(0.6);
}

form
{
  height: 96px;
}

input[type="text"]
{
  width: 100%;
  height: 96px;
  font-size: 60px;
  line-height: 1;
}

input[type="text"]::placeholder
{
  color: black;
}

#s-cover
{
  width: 1px;
  padding-left: 35px;
}

button
{
  position: relative;
  display: block;
  width: 84px;
  height: 96px;
  cursor: pointer;
}

#s-circle
{
  position: relative;
  top: -8px;
  left: 0;
  width: 43px;
  height: 43px;
  margin-top: 0;
  border-width: 15px;
  border: 15px solid #fff;
  background-color: transparent;
  border-radius: 50%;
  transition: 0.5s ease all;
}

button span
{
  position: absolute;
  top: 68px;
  left: 43px;
  display: block;
  width: 45px;
  height: 15px;
  background-color: transparent;
  border-radius: 10px;
  transform: rotateZ(52deg);
  transition: 0.5s ease all;
}

button span:before, button span:after
{
  content: '';
  position: absolute;
  bottom: 0;
  right: 0;
  width: 45px;
  height: 15px;
  background-color: #fff;
  border-radius: 10px;
  transform: rotateZ(0);
  transition: 0.5s ease all;
}

#s-cover:hover #s-circle
{
  top: -1px;
  width: 67px;
  height: 15px;
  border-width: 0;
  background-color: #fff;
  border-radius: 20px;
}

#s-cover:hover span
{
  top: 50%;
  left: 56px;
  width: 25px;
  margin-top: -9px;
  transform: rotateZ(0);
}

#s-cover:hover button span:before
{
  bottom: 11px;
  transform: rotateZ(52deg);
}

#s-cover:hover button span:after
{
  bottom: -11px;
  transform: rotateZ(-52deg);
}
#s-cover:hover button span:before, #s-cover:hover button span:after
{
  right: -6px;
  width: 40px;
  background-color: #fff;
}

#ytd-url {
  display: block;
  position: fixed;
  right: 0;
  bottom: 0;
  padding: 10px 14px;
  margin: 20px;
  color: #fff;
  font-family: Nunito;
  font-size: 14px;
  text-decoration: none;
  background-color: #ff7575;
  border-radius: 4px;
  box-shadow: 0 10px 20px -5px rgba(255, 117, 117, 0.86);
  z-index: 125;
}
</style>