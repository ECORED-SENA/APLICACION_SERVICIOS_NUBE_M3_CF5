<template lang="pug">
.curso-main-container.introduccion
  BannerInterno
  .container.tarjeta.tarjeta--blanca.p-4.p-md-5.mb-5
  
    .titulo-principal
      .titulo-principal__numero
        span
          i.fas.fa-info
      h1 Introducción
    
    .row.mt-5 
      .col-12.col-lg-9
        p Sobre los sistemas informáticos y, en esencia, para las bases de datos existen diversos tipos de pruebas como por ejemplo de  #[strong funcionalidad], que son las encargadas de validar que el sistema o componente cumpla con las condiciones que permitan resolver o ayudar a resolver un problema computacional o requerimiento. Concurren también las de #[strong rendimiento] que se encargan de validar que el sistema cumpla con tiempos óptimos de respuesta para determinadas cargas de trabajo proyectadas. También están las pruebas de #[strong estrés], que son las encargadas de dar a conocer el punto donde el sistema se bloquea por el exceso de procesamiento y, por último, figuran las de seguridad llamadas pruebas de #[strong vulnerabilidad]. 
        p Para cada una de las pruebas existen varias técnicas, métricas y tecnologías para realizarlas, sin embargo, a lo largo de este recorrido se conceptualizarán algunos aspectos técnicos, y se realizarán pruebas de integridad referencial orientadas a conocer si el modelo relacional sirve para cumplir el requerimiento y pruebas de acceso o conocidas también como pruebas de seguridad básicas para revocar sentencias y asignar o revocar permisos en una base de datos.
      .col-4.col-lg-3.offset-4.offset-lg-0.align-self-center
        figure
            img(src="@/assets/template/tema-0-1.svg" alt="Texto que describa la imagen")
    figure.mt-5
      .video
        iframe(width="560" height="315" src="https://www.youtube.com/embed/U3RWZi2CwQo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen)
   


</template>

<script>
export default {
  name: 'Introduccion',
  data: () => ({
    // variables de vue
  }),
}
</script>

<style lang="sass" scoped>
.introduccion
</style>
