<template lang="pug">
div
  table
    .row.mb-5
      .col-md-6
        //- LineaTiempoD debe ir acompañado de una de una de estas clases => 
        //- .color-primario, .color-secundario, .color-acento-contenido, .color-acento-botones
        LineaTiempoD.color-secundario
          .row(numero="1" titulo=" Pruebas estáticas")
            .col-6.col-md-5.offset-3.offset-md-1
              figure
                img(src='@/assets/template/tema-1-3.svg', alt='Texto que describa la imagen')
            .col-md-6.mb-4.mb-md-0.mt-4.mt-md-0
              p Se realizan mientras se construye el código fuente, se basan en las pruebas de escritorio antes vistas o más completas basadas en flujos de aplicación (hacer todo el proceso informático). 
          .row(numero="2" titulo="Pruebas dinámicas")
            .col-6.col-md-5.offset-3.offset-md-1
              figure
                img(src='@/assets/template/tema-1-4.svg', alt='Texto que describa la imagen')
            .col-md-6.mb-4.mb-md-0.mt-4.mt-md-0
              p Requieren que la aplicación esté 100 funcional y se dividen en pruebas de caja blanca (solo se validan características de un módulo o componente del sistema) o de caja negra (se revisa el cumplimiento de todo un requisito funcional completo desde un usuario final). 
          
      .col-md-6
        //- LineaTiempoD debe ir acompañado de una de una de estas clases => 
        //- .color-primario, .color-secundario, .color-acento-contenido, .color-acento-botones
        LineaTiempoD.color-secundario
          .row(numero="1" titulo="Pruebas de compatibilidad ")
            .col-6.col-md-5.offset-3.offset-md-1
              figure
                img(src='@/assets/template/tema-1-5.svg', alt='Texto que describa la imagen')
            .col-md-6.mb-4.mb-md-0.mt-4.mt-md-0
              p Garantizan que el sistema sea compatible con otros sistemas.
          .row(numero="2" titulo="Pruebas de seguridad")
            .col-6.col-md-5.offset-3.offset-md-1
              figure
                img(src='@/assets/template/tema-1-6.svg', alt='Texto que describa la imagen')
            .col-md-6.mb-4.mb-md-0.mt-4.mt-md-0
              p Validan que no se vulnere el acceso a datos o procedimientos no autorizados.
          .row(numero="3" titulo="Pruebas de estrés ")
            .col-6.col-md-5.offset-3.offset-md-1
              figure
                img(src='@/assets/template/tema-1-7.svg', alt='Texto que describa la imagen')
            .col-md-6.mb-4.mb-md-0.mt-4.mt-md-0
              p Conocen el punto de capacidad máxima del sistema.
          .row(numero="4" titulo="Pruebas de usabilidad")
            .col-6.col-md-5.offset-3.offset-md-1
              figure
                img(src='@/assets/template/tema-1-8.svg', alt='Texto que describa la imagen')
            .col-md-6.mb-4.mb-md-0.mt-4.mt-md-0
              p Determinan la facilidad con la que el usuario puede interactuar con el sistema.
          .row(numero="5" titulo="Pruebas de rendimiento o carga")
            .col-6.col-md-5.offset-3.offset-md-1
              figure
                img(src='@/assets/template/tema-1-9.svg', alt='Texto que describa la imagen')
            .col-md-6.mb-4.mb-md-0.mt-4.mt-md-0
              p Determinan el nivel de servicio o tiempos de respuesta del sistema para determinadas cargas de trabajo.
          .row(numero="6" titulo="Pruebas de escalabilidad")
            .col-6.col-md-5.offset-3.offset-md-1
              figure
                img(src='@/assets/template/tema-1-10.svg', alt='Texto que describa la imagen')
            .col-md-6.mb-4.mb-md-0.mt-4.mt-md-0
              p Indican que el sistema puede ser reconfigurado para soportar otros niveles de carga de trabajo.
            


            

</template>

<script>
export default {
  name: 'LineaTiempoDoble',
  data: () => ({}),
}
</script>

<style lang="sass" scoped></style>
