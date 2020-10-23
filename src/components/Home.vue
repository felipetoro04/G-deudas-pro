<template>
<div id="home">
  <BarraNav></BarraNav>
  <BarraLateral></BarraLateral>
  <Cuerpo></Cuerpo>
</div>
</template>

<script>

import BarraNav from "@/components/barnav";
import BarraLateral from "@/components/lateral";
import Cuerpo from "@/components/body";
export default {
name: "home",
  components: {Cuerpo, BarraLateral, BarraNav},
}

</script>

<style scoped>
#home {
  border: solid 1px #000000;
  width: 100%; margin: 0 auto;}

</style>