<template lang="pug">
.curso-main-container.pb-3
  BannerInterno
  .container.tarjeta.tarjeta--blanca.p-4.p-md-5
    .titulo-principal
      .titulo-principal__numero
        span 3
      h1 Pruebas de integridad de datos
    figure
      img(src='@/assets/template/tema-3-1.png', alt='Texto que describa la imagen')
    p.mt-5 Las pruebas de integridad de base de datos son pruebas de los métodos y procesos utilizados para acceder y gestionar datos (base de datos), para asegurar que los métodos de acceso, los procesos y las reglas de los datos funcionan como se espera y que, durante el acceso a la base de datos, los datos no se corrompan, sean borrados, modificados o creados de forma inesperada #[strong (Globe Testing, 2021)].
    figure.mb-5.mt-5
      .video
        <iframe width="560" height="315" src="https://www.youtube.com/embed/SLPqBj9XjWc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
      .row.mt-4
        .col-10.col-md-6.offset-1.offset-md-3
          .cajon.color-secundario.p-4.mb-4
            .row
              .col-4.d-none.d-lg-block
                figure
                  img(src="@/assets/template/tema-3-2.svg" alt="Texto que describa la imagen")
              .col-12.col-lg-8
                p A continuación, se darán las instrucciones a seguir en un modelo de datos para realizar pruebas de integridad de datos, para lo cual debe crear la siguiente base de datos: 
    .h4.mt-5 Crear base de datos 
    .row.mt-4
      .col-8.col-md-8.bg-gris.rounded.letter-spacing-2
        .row
          .col-lg-8
            .h5.px-5.pt-4.mb-0 mysql> CREATE TABLE cliente(
            .row.mt-2
              .col-10.offset-2.px-4
                ul.lista-ul
                  li.mb-1 
                    i.fas.fa-arrow-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 id_cliente INT NOT NULL,
                  li.mb-1
                    i.fas.fa-arrow-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 nombre VARCHAR(30),
                  li.mb-1
                    i.fas.fa-arrow-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 PRIMARY KEY (id_cliente)
                  li.mb-1
                    i.fas.fa-arrow-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 )
                  li.mb-1
                    i.fas.fa-arrow-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 ;
            .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.04 sec)
            .h5.px-5.mt-5.mb-0.pb-4 mysql> CREATE TABLE venta(
            .row.mt-2
              .col-10.offset-2.px-4
                ul.lista-ul
                  li.mb-1 
                    i.fas.fa-arrow-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 id_factura INT NOT NULL,
                  li.mb-1
                    i.fas.fa-arrow-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 cliente_id INT NOT NULL,
                  li.mb-1
                    i.fas.fa-arrow-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 cantidad INT,
                  li.mb-1
                    i.fas.fa-arrow-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 PRIMARY KEY(id_factura),
                  li.mb-1
                    i.fas.fa-arrow-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 INDEX (cliente_id),
                  li.mb-1
                    i.fas.fa-arrow-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 FOREIGN KEY (cliente_id) REFERENCES cliente (id_cliente)
                  li.mb-1
                    i.fas.fa-arrow-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 ) ;
            .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.06 sec)
            .h5.px-5.mt-5.mb-0.pb-4 mysql>
    p.mt-5 Una vez creada la base de datos, se puede avanzar en la construcción con las siguientes instrucciones
    LineaTiempoD.color-secundario
      .row(numero="1" titulo="Intentar insertar una venta para un cliente y tomar nota del error.")
        .row.mt-4.px-4
          .col-11.bg-gris.rounded.letter-spacing-2
            .row
              .col-11
                .h5.px-5.pt-4.mb-0 mysql> INSERT INTO venta(id_factura,cliente_id, cantidad) VALUES (1,NULL, 19);
                .h5.px-5.pt-2.mb-0 ERROR 1048 (23000): Column ‘cliente_id’ cannot be null
                .h5.px-5.pt-2.mb-4 mysql>
      .row(numero="2" titulo="Insertar un cliente y usar el id_cliente como cliente_id en una factura.")
        .row.mt-4.px-4
          .col-11.bg-gris.rounded.letter-spacing-2
            .row
              .col-11
                .h5.px-5.pt-4.mb-0 mysql> INSERT INTO cliente (id_cliente, nombre) VALUES (1,’CLIENTE NUEVO’);
                .h5.px-5.pt-2.mb-0 Query OK, 1 row affected (0.01 sec)
                .h5.px-5.pt-4.mb-0 mysql> INSERT INTO venta(id_factura,cliente_id, cantidad) VALUES (1,1, 19);
                .h5.px-5.pt-2.mb-4 Query OK, 1 row affected (0.00 sec)
      .row(numero="3" titulo="Intentar borrar el cliente creado. ")
        .row.mt-4.px-4
          .col-11.bg-gris.rounded.letter-spacing-2
            .row
              .col-11
                .h5.px-5.pt-4.mb-0 mysql> DELETE FROM cliente WHERE id_cliente = 1;
                .h5.px-5.pt-2.mb-0 ERROR 1451 (23000): Cannot delete or update a parent row: a foreign key constraint fails (`test_idata`.`venta`, CONSTRAINT `venta_ibfk_1` FOREIGN KEY (`cliente_id`) REFERENCES `cliente` (`id_cliente`))
                .h5.px-5.pt-2.mb-4 mysql>
      .row(numero="4" titulo="Documentar el error y reflexionar por qué no permite borrar el cliente y qué debería hacer para que se pueda borrar.")
        
      .row(numero="5" titulo="Tratar de actualizar el campo id_cliente de la tabla cliente.")
        .row.mt-4.px-4
          .col-11.bg-gris.rounded.letter-spacing-2
            .row
              .col-11
                .h5.px-5.pt-4.mb-0 mysql> UPDATE cliente SET id_cliente = 2 WHERE id_cliente = 1;
                .h5.px-5.pt-2.mb-0 ERROR 1451 (23000): Cannot delete or update a parent row: a foreign key constraint fails (`test_idata`.`venta`, CONSTRAINT `venta_ibfk_1` FOREIGN KEY (`cliente_id`) REFERENCES `cliente` (`id_cliente`))
                .h5.px-5.pt-2.mb-4 mysql>
      .row(numero="6" titulo="Documentar el error y reflexionar por qué no permite editar el cliente y que debería hacer para que permita editarlo.")
        p.mt-4 Crear una nueva base de datos con la siguiente definición de tablas y realizar las pruebas de integridad propuestas. Al final, listar el contenido de las dos tablas. 
        .row.mt-4.px-4
          .col-11.bg-gris.rounded.letter-spacing-2
            .row
              .col-8.col-md-9.bg-gris.rounded.letter-spacing-2
                .h5.px-5.pt-4.mb-0 mysql> CREATE TABLE cliente(
                .row.mt-2
                  .col-12.offset-1.px-4
                    ul.lista-ul
                      li.mb-1.px-0 
                        i.fas.fa-arrow-right(style="color: #12263F;")
                        .h5.mb-0.pt-1 id_cliente INT NOT NULL,
                      li.mb-1
                        i.fas.fa-arrow-right(style="color: #12263F;")
                        .h5.mb-0.pt-1 nombre VARCHAR(30),
                      li.mb-1
                        i.fas.fa-arrow-right(style="color: #12263F;")
                        .h5.mb-0.pt-1 PRIMARY KEY (id_cliente)
                      li.mb-1
                        i.fas.fa-arrow-right(style="color: #12263F;")
                        .h5.mb-0.pt-1 )
                      li.mb-1
                        i.fas.fa-arrow-right(style="color: #12263F;")
                        .h5.mb-0.pt-1 ;
                .h5.px-5.pt-2.mb-0 Query OK, 0 rows affected (0.04 sec)
                .h5.px-5.pt-4.mb-0 mysql> CREATE TABLE venta(
                .row.mt-2
                  .col-12.offset-1.px-4
                    ul.lista-ul
                      li.mb-1.px-0 
                        i.fas.fa-arrow-right(style="color: #12263F;")
                        .h5.mb-0.pt-1 id_factura INT NOT NULL,
                      li.mb-1
                        i.fas.fa-arrow-right(style="color: #12263F;")
                        .h5.mb-0.pt-1 cliente_id INT NOT NULL,
                      li.mb-1
                        i.fas.fa-arrow-right(style="color: #12263F;")
                        .h5.mb-0.pt-1 cantidad INT,
                      li.mb-1
                        i.fas.fa-arrow-right(style="color: #12263F;")
                        .h5.mb-0.pt-1 PRIMARY KEY(id_factura),
                      li.mb-1
                        i.fas.fa-arrow-right(style="color: #12263F;")
                        .h5.mb-0.pt-1 INDEX (cliente_id),
                      li.mb-1
                        i.fas.fa-arrow-right(style="color: #12263F;")
                        .h5.mb-0.pt-1 FOREIGN KEY (cliente_id) REFERENCES cliente (id_cliente)
                      li.mb-1
                        i.fas.fa-arrow-right(style="color: #12263F;")
                        .h5.mb-0.pt-1 ON UPDATE CASCADE ON DELETE CASCADE
                      li.mb-1
                        i.fas.fa-arrow-right(style="color: #12263F;")
                        .h5.mb-0.pt-1  );
                .h5.px-5.pt-2.mb-0 Query OK, 0 rows affected (0.06 sec)
                .h5.px-5.pt-4.mb-4 mysql>

</template>

<script>
export default {
  name: 'Tema3',
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
