 <template>
    <div id="qsomos">
      <barra-nav></barra-nav>
      <h1>G-Deudas</h1>
      <p>
        G-DEUDAS: Es una aplicación que viene a facilitar de administración de boletas, permitiendo almacenar todos
        los datos de las boletas emitidas por gastos comunes (luz, agua u otros), deudas o créditos con casas
        comerciales,         etc., haciendo más fácil el ordenamiento de todas las boletas.
      </p>
      <h4>Misión</h4>
      <p>
        Facilitar la administración de boletas para así gestionar de mejor maneras las deudas.
      </p>
      <h4>Visión</h4>
      <p>
        Una forma de vida libre de preocupaciones en relación a la gestión de boletas.
      </p>
      <div class="buttonHeader">
        <router-link to="/home"><button>Volver</button></router-link>
      </div>
    </div>
  </template>


<script>
import BarraNav from "@/components/barnav";
export default {
name: "q_somos",
  components:{BarraNav}
}
</script>

<style scoped>
#qsomos{
  text-align: center;
}
</style>