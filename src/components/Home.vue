<template>
<div id="home">
  <BarraNav></BarraNav>
  <Cuerpo></Cuerpo>
</div>
</template>

<script>

import BarraNav from "@/components/barnav";
import Cuerpo from "@/components/body";
export default {
name: "home",
  components: {Cuerpo, BarraNav},
}

</script>

<style scoped>
#home {
  width: 100%; margin: 0 auto;}

</style>