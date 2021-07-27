<template lang="pug">
.curso-main-container.pb-3
  BannerInterno
  .container.tarjeta.tarjeta--blanca.p-4.p-md-5

    .titulo-principal
      .titulo-principal__numero
        span 1
      h1 Tipos de pruebas
    p.mt-3 En el proceso de desarrollo de software existen diferentes tipos de pruebas, con muchas clasificaciones y subclasificaciones. Así, las del proceso de desarrollo comprenden todas las etapas de continuación y producción de software hasta que el producto está terminado, a saber:
    Tabla1.mt-4
    LineaTiempoDoble.mt-5
    .row.mt-4
      .col-10.col-md-8.offset-1.offset-md-2
        .cajon.color-primario.p-4.mb-4
          p Según el breve panorama presentado hasta ahora, se describieron los tipos de prueba que se estudiarán en adelante, sin embargo, se deben considerar que están orientas al sistema de bases de datos. Las pruebas a realizar se enfocan, inicialmente, #[strong en pruebas de acceso y luego pruebas de integridad de datos e integridad] referencial. 
</template>

<script>
import Tabla1 from '../components/Tabla1'
import LineaTiempoDoble from '../components/LineaTiempoDoble'
export default {
  name: 'Tema1',
  components: {
    Tabla1,
    LineaTiempoDoble,
  },
  data: () => ({
    // variables de vue
  }),
  mounted() {
    this.$nextTick(() => {
      this.$aosRefresh()
    })
  },
  updated() {
    this.$aosRefresh()
  },
}
</script>

<style lang="sass" scoped></style>
