<template>
  <div id="bar">
    <nav><ul>
      <li><router-link to="/home"><button>Inicio</button></router-link></li>
      <li><button>Quiénes somos</button><ul>
      <li><router-link to="/Politicas_de_privacidad"><button>Politicas de Privacidad</button></router-link></li>
      </ul></li>
      <li ><router-link to="/Creacion"><button>Creacion de Boleta</button></router-link></li>
      <li><button>Actualizacion Boleta</button></li>
      <li><button>Eliminar Boleta</button></li>
      <li><button>Consultas sobre Boletas</button><ul>
        <li><button>Por Institucion</button></li>
        <li><button>Por Mes de Emision</button></li>
        <li><button>Por Mes de Vencimiento</button></li>
        <li><button>Por Estado</button></li>
      </ul></li>
      <li><router-link to="/login"><button>Cerrar sesion</button></router-link></li>

    </ul></nav>
  </div>

</template>

<script>
export default {
  name: "BarraNav",
}

</script>

<style>
#bar *{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-size:0;
}
#bar nav button{
  text-align: center;
  text-transform: uppercase;
  cursor: pointer;
  font-size: 10px;

  position: relative;
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


#bar nav li{
  display:inline-block;
  border:none;
  text-align:center;
  position:relative;
}

#bar nav button:hover{
  background: #fff;
  box-shadow: 0px 2px 10px 5px #1abc9c;
  color: #000;
  cursor: pointer;

}
#bar nav button:after{
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
#bar nav button:active:after{
  padding: 0;
  margin: 0;
  opacity: 1;
  transition: 0s
}
#bar nav button:focus{outline:0;}

#bar nav li>ul{
  display: none;
}

#bar nav li:hover>ul{
  display:block;
  position:absolute;
  top:50px;
  left:0px;
}

</style>

