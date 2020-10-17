<template>
  <div id="bar">
    <div class="logo">
      <img class="logo" src="assets/images/g-deudas.png" alt="logo">
    </div>
    <div class="search">
      <p><label>Ingresa atributo de busqueda: <input type="text" name="busqueda"></label><button>Search</button></p>
    </div>
    <div class="links">
    <ul>
      <li><button>Inicio</button></li>
      <li><button>Nosotros</button></li>
      <li><button>Politicas de Privacidad</button></li>
      </ul>
    </div>
  </div>

</template>

<script>
export default {
name: "BarraNav"
}
</script>

<style scoped>
.logo {
   }
.search{
}
.links{
}

</style>