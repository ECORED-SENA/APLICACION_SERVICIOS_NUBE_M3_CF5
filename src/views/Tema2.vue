<template lang="pug">
.curso-main-container.pb-3
  BannerInterno
  .container.tarjeta.tarjeta--blanca.p-4.p-md-5
    
    .titulo-principal
      .titulo-principal__numero
        span 2
      h1 Codificación de la API REST con Node.js
    figure
      img(src="@/assets/template/tema-2-1.png" alt="Texto que describa la imagen")
    p.mt-5 Es fundamental, en cualquier sistema, garantizar la seguridad de la información, por eso, es de interés conocer las sentencias que permiten asignar y revocar permisos de acceso sobre los componentes de una base de datos. Ahora, se revisarán las sentencias DCL (Data Control Language).

    #t_2_1.titulo-segundo
      .h4 2.1  Crear un usuario en MySQL
    p.mt-4 La sentencia para crear un usuario es: 
    .row.mt-5
      .col-12.col-md-12.bg-gris.rounded.text-center.letter-spacing-2
        .h5.px-5.py-4.mb-0 CREATE USER ‘newuser’@‘localhost’ IDENTIFIED BY ‘password’;
    .col-sm.mb-5.mb-sm-0.mt-4
      ul.lista-ul
        li 
          i.fas.fa-angle-right
          | #[strong ‘newuser’]: es el nombre del nuevo usuario 
        li
          i.fas.fa-angle-right
          | #[strong ‘localhost’]: es el computador de donde permitiremos que se conecte el usuario newuser
        li
          i.fas.fa-angle-right
          | #[strong ‘password’]: es la contraseña con la que se permitirá que se conecte ese usuario desde el computador especificado. 
    .row.mt-5
      .col-10.col-md-8.offset-1.offset-md-2
        .cajon.color-primario.p-4.mb-4
          .h4 Ejemplo:
          p.mt-3 Crear un usuario que se llame contabilidad, que tenga contraseña #FVRwQrFI y que pueda acceder desde el computador con dirección IP 192.168.1.25.
    p.mt-4 Solución: 
    .row.mt-4
      .col-12.col-md-12.bg-gris.rounded.text-center.letter-spacing-2
        .h5.px-5.py-4.mb-0 CREATE USER ‘contabilidad’@‘192.168.1.25’ IDENTIFIED BY ‘#FVRwQrFI’;
    .row.mt-4
      .col-10.col-md-8.offset-1.offset-md-2
        .cajon.color-primario.p-4.mb-4
          .h4 Ejemplo:
          p.mt-3 Crear un usuario que se llame producción, que tenga contraseña nDUR0#6eO y que acceda desde cualquier computador y que, adicionalmente, pueda crear usuario y asignar permisos
    p.mt-4 Solución:
    .row.mt-4
      .col-12.col-md-12.bg-gris.rounded.text-center.letter-spacing-2
        .h5.px-5.py-4.mb-0 CREATE USER ‘produccion’@‘%’ IDENTIFIED BY ‘nDUR0#6eO’ WITH GRANT OPTION;
    p.mt-4 Ahora, solo resta asignar permisos de acceso a sentencias MDL o DDL sobre la base de datos.
    #t_2_2.titulo-segundo.mt-5 
      .h4 2.2  Permisos de acceso
    .row.mt-4 
      .col-12.col-lg-9
        p Las sentencias GRANT y REVOKE permiten a los administradores de bases de datos asignar o revocar permisos a los usuarios, respectivamente. La sintaxis de las sentencias GRANT y REVOKE puede diferir un poco respecto de otros SGDB como Oracle, Postgres o MSSQL, sin embargo, las sentencias MDL vistas en otro componente son compatibles con cualquiera de estos motores.
        p.mt-4 Los privilegios que se asignan dentro de una base de datos pueden ser concedidos a los siguientes niveles:
      .col-3.d-none.d-lg-block.align-self-center
        figure
          img(src="@/assets/template/tema-2-2.svg" alt="Texto que describa la imagen")
    AcordionA.mb-5(tipo="b" clase-tarjeta="tarjeta bg-gris-claro").mt-5 
      .row(titulo="Nivel global: ")
        .col-12
          p.mt-4 los privilegios globales se aplican a todas las bases de datos del servidor donde se está invocando. Estos privilegios se almacenan en la tabla mysql.user. GRANT ALL ON *.* y REVOKE ALL ON *.* conceden y revocan solo privilegios globales.
          .row.mt-4
            .col-12.col-md-12.bg-gris.rounded.letter-spacing-2
              .h5.px-5.py-4.mb-0 GRANT ALL PRIVILEGES ON *.* TO ‘newuser’@‘localhost’;
          p.mt-4 Es posible ver qué privilegios se han concedido a determinado usuario mediante la sentencia SHOW GRANTS FOR:z
          .row.mt-4
            .col-12.col-md-12.bg-gris.rounded.letter-spacing-2
              .h5.px-5.pt-4.mb-0 MariaDB [acl]> SHOW GRANTS FOR ‘newuser’@‘localhost’;
              .h5.px-5.mt-2.mb-0 +—————————————————————————+
              .h5.px-5.mt-2.mb-0 | Grants for newuser@localhost |
              .h5.px-5.mt-2.mb-0 +—————————————————————————+
              .h5.px-5.mt-2.mb-0 | GRANT ALL PRIVILEGES ON *.* TO `newuser`@`localhost` |
              .h5.px-5.mt-2.mb-0 +—————————————————————————+
              .h5.px-5.mt-2.mb-0 1 row in set (0.003 sec)
              .h5.px-5.mt-3.mb-0.pb-4 MariaDB [acl]>
          p.mt-4 Y para revocarlos será:
          .row.mt-4
            .col-12.col-md-12.bg-gris.rounded.letter-spacing-2
              .h5.px-5.py-4.mb-0 GRANT ALL PRIVILEGES ON *.* TO ‘newuser’@‘localhost’;

      
      div(titulo="Nivel de base de datos: ")
        p los privilegios de base se pueden aplicar a todos los objetos en una base de la base de datos donde se ejecutan las sentencias GRANT ALL ON &lt;nombre_base_datos&gt;.* y REVOKE ALL ON   &lt;basedatos&gt; FROM &lt;usuario&gt;.
        p.mt-4 Ejemplo: crear una base de datos llamada “acl”, crear un usuario llamado acluser que pueda acceder desde el mismo computador con contraseña “98765*1234” y asignarle permisos solo a todos los objetos de la base de datos acl y, posteriormente, revoke los permisos dados.
        .h4.mt-4 Solución:       
        .row.mt-4
          .col-12.col-md-12.bg-gris.rounded.letter-spacing-2
            .h5.px-5.pt-4.mb-0 MariaDB [(none)]> CREATE DATABASE acl;
            .h5.px-5.mt-2.mb-0 Query OK, 1 row affected (0.001 sec)
            .h5.px-5.mt-5.mb-0 MariaDB [(none)]> CREATE USER ‘acluser’@‘localhost’ IDENTIFIED BY ‘98765*1234’;
            .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.008 sec)
            .h5.px-5.mt-5.mb-0 MariaDB [(none)]> GRANT ALL PRIVILEGES ON acl.* TO acluser@‘localhost’;
            .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.006 sec)
            .h5.px-5.mt-2.mb-0.pb-4 MariaDB [(none)]>

        p.mt-4 Ahora, serán revocados:
        .row.mt-4
          .col-12.col-md-12.bg-gris.rounded.letter-spacing-2
            .h5.px-5.pt-4.mb-0 MariaDB [(none)]> REVOKE ALL PRIVILEGES ON acl.* FROM  acluser@‘localhost’;
            .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.001 sec)
            .h5.px-5.mt-5.mb-0.pb-4 MariaDB [(none)]>

      div(titulo="Nivel de tabla: ")
        p.mt-4 los privilegios de tabla se aplican a todas las columnas de una tabla dada. GRANT ALL ON &lt;nombre_basedatos&gt;.&lt;nombre tabla&gt; y REVOKE ALL ON &lt;nombre_basedatos&gt;.&lt;nombre tabla&gt; conceden y revocan únicamente privilegios de tabla.
        p.mt-4 Se crea una tabla para realizar las pruebas de acceso: 
        .row.mt-4
          .col-12.col-md-12.bg-gris.rounded.letter-spacing-2
            .h5.px-5.pt-4.mb-0 MariaDB [(none)]> use acl,
            .h5.px-5.mt-2.mb-0 MariaDB [acl]> CREATE TABLE persona (
            .row.mt-2
              .col-10.offset-1.px-4
                ul.lista-ul
                  li.mb-1 
                    i.fas.fa-angle-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 id_persona INT KEY,
                  li.mb-1
                    i.fas.fa-angle-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 nombres VARCHAR(100),
                  li.mb-1
                    i.fas.fa-angle-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 apellidos VARCHAR(100),
                  li.mb-1
                    i.fas.fa-angle-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 correo VARCHAR(250),
                  li.mb-1
                    i.fas.fa-angle-right(style="color: #12263F;")
                    .h5.mb-0.pt-1 fecha_nacimiento DATE);
            .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.024 sec)
            .h5.px-5.mt-5.mb-0.pb-4 MariaDB [acl]>
        p.mt-4 Ahora, se asignarán los permisos de acceso sobre toda la tabla y se revocarán.
        .row.my-4
          .col-12.col-md-12.bg-gris.rounded.letter-spacing-2
            .h5.px-5.pt-4.mb-0 MariaDB [acl]> GRANT ALL ON acl.persona to acluser@‘localhost’;
            .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.005 sec)
            .h5.px-5.mt-5.mb-0.pb-4 MariaDB [acl]>
        p.mt-4 Seguidamente serán revocados.
        .row.my-4
          .col-12.col-md-12.bg-gris.rounded.letter-spacing-2
            .h5.px-5.pt-4.mb-0 MariaDB [acl]> REVOKE ALL PRIVILEGES ON acl.persona FROM  acluser@‘localhost’;
            .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.004 sec)
            .h5.px-5.mt-5.mb-0.pb-4 MariaDB [acl]>
    p.mt-5Las sentencias GRANT y REVOKE permiten a los administradores de bases de datos asignar o revocar permisos a los usuarios, respectivamente. La sintaxis de las sentencias GRANT y REVOKE puede diferir un poco respecto de otros SGDB como Oracle, Postgres o MSSQL, sin embargo, las sentencias MDL vistas en otro componente son compatibles con cualquiera de estos motores.
    .bloque-texto-a.color-secundario.p-4.p-md-5.mb-5.mt-5
      .row.m-0.align-items-center.justify-content-between
        .col-lg-8
          .bloque-texto-a__texto.p-4
            p Existen también privilegios a nivel de columna, aunque difícilmente son administrados por los DBA de tal forma que, al no ser comúnmente usuarios, serán nítidos. 
            p.mt-3 Los niveles pueden convocar no tipos de acceso, según el tipo de operación a ejecutar sobre el objeto; hasta ahora se ha visto el acceso total o acceso ALL. Otros privilegios que se pueden conceder son:
        .col-lg-4.mb-4.mb-lg-0
          figure
            img(src="@/assets/template/tema-2-3.svg" alt="Texto que describa la imagen")
    .col-sm.mb-5.mb-sm-0.mt-4
      ul.lista-ul
        li 
          i.fas.fa-angle-right(style="color: #4DD0E1;")
          | #[strong ALL]: para conceder todos los privilegios.
        li
          i.fas.fa-angle-right(style="color: #4DD0E1;")
          | #[strong CREATE.]: permite crear nuevas tablas.
        li
          i.fas.fa-angle-right(style="color: #4DD0E1;")
          | #[strong DELETE.]: permite usar la sentencia DELETE.
        li
          i.fas.fa-angle-right(style="color: #4DD0E1;")
          | #[strong DROP.]: permite borrar tablas.
        li
          i.fas.fa-angle-right(style="color: #4DD0E1;")
          | #[strong INSERT.]: permite insertar datos en tablas.
        li
          i.fas.fa-angle-right(style="color: #4DD0E1;")
          | #[strong UPDATE]: permite usar la sentencia UPDATE.     
    
    #t_2_3.titulo-segundo.mt-5 
      .h4 2.3  Permisos de acceso
    figure
      img(src="@/assets/template/tema-2-4.png" alt="Texto que describa la imagen")
    p.mt-4 Para la prueba de acceso se revisará un ejemplo de creación de una base de datos llamada #[strong test_acl] con las tablas listadas a continuación; luego, un usuario llamado #[strong readonly] que solo puede hacer selectos sobre todas las tablas y crear otro usuario llamado #[strong insertonly] que únicamente puede insertar datos y, finalmente, uno que se llame #[strong updateonly].
    TabsB.color-acento-contenido.mb-5
      .py-4.py-md-5(titulo="Crear bases de datos" :icono="require('@/assets/template/tema-2-12.svg')")
        .row.mt-4
          .col-8.col-md-8.bg-gris.rounded.letter-spacing-2
            .row
              .col-lg-12
                .h5.px-5.pt-4.mb-0 mysql> GRANT SELECT ON test_db.* TO readonly@‘%’;
                .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.00 sec)
                .h5.px-5.mt-5.mb-0 mysql> GRANT INSERT ON test_db.* TO insertonly@‘%’;
                .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.00 sec)
                .h5.px-5.mt-5.mb-0 mysql> GRANT UPDATE ON test_db.* TO updateonly@‘%’;
                .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.00 sec)
                .h5.px-5.mt-5.mb-0.pb-4 MariaDB [(none)]>
          .col-md-4.align-self-center
            figure
              img(src='@/assets/template/tema-2-5.svg', alt='Texto que describa la imagen')
      .py-4.py-md-5(titulo="Crear usuarios " :icono="require('@/assets/template/tema-2-13.svg')")
        .row.mt-4
          .col-8.col-md-8.bg-gris.rounded.letter-spacing-2
            .row
              .col-lg-8
                .h5.px-5.pt-4.mb-0 mysql> CREATE USER readonly@‘%’ IDENTIFIED BY ‘987*123*456’;
                .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.03 sec)
                .h5.px-5.mt-5.mb-0 mysql> CREATE USER insertonly@‘%’ IDENTIFIED BY ‘987*123*456’;
                .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.01 sec)
                .h5.px-5.mt-5.mb-0 mysql> CREATE USER updateonly@‘%’ IDENTIFIED BY ‘987*123*456’;
                .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.01 sec)
                .h5.px-5.mt-5.mb-0.pb-4 mysql>
          .col-md-4.align-self-center
            figure
              img(src='@/assets/template/tema-2-7.svg', alt='Texto que describa la imagen')
      .py-4.py-md-5(titulo="Asignar privilegios" :icono="require('@/assets/template/tema-2-14.svg')")
        .row.mt-4
          .col-8.col-md-8.bg-gris.rounded.letter-spacing-2
            .row
              .col-lg-8
                .h5.px-5.pt-4.mb-0 mysql> GRANT SELECT ON test_db.* TO readonly@‘%’;
                .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.00 sec)
                .h5.px-5.mt-5.mb-0 mysql> GRANT INSERT ON test_db.* TO insertonly@‘%’;
                .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.00 sec)
                .h5.px-5.mt-5.mb-0 mysql> GRANT UPDATE ON test_db.* TO updateonly@‘%’;
                .h5.px-5.mt-2.mb-0 Query OK, 0 rows affected (0.00 sec)
                .h5.px-5.mt-5.mb-0.pb-4 mysql>
          .col-md-4.align-self-center
            figure
              img(src='@/assets/template/tema-2-8.svg', alt='Texto que describa la imagen')


      .py-4.py-md-5(titulo="Verificar los accesos" :icono="require('@/assets/template/tema-2-15.svg')")
        .row.mt-4
          .col-8.col-md-8.bg-gris.rounded.letter-spacing-2
            .row
              .col-lg-9
                .h5.px-5.pt-4.mb-0 mysql> SHOW GRANTS FOR ‘readonly’@‘%’;
                .h5.px-5.mt-2.mb-0 +———————————————————————+
                .h5.px-5.mt-3.mb-0 | Grants for readonly@% |
                .h5.px-5.mt-2.mb-0 +———————————————————————+
                .h5.px-5.mt-3.mb-0 | GRANT USAGE ON *.* TO `readonly`@`%` |
                .h5.px-5.mt-2.mb-0 | GRANT SELECT ON `test_db`.* TO `readonly`@`%` |
                .h5.px-5.mt-2.mb-0 +———————————————————————+
                .h5.px-5.mt-2.mb-0 2 rows in set (0.00 sec)
                .h5.px-5.mt-5.mb-0 mysql> SHOW GRANTS FOR ‘updateonly’@‘%’;
                .h5.px-5.mt-2.mb-0 +————————————————————————+
                .h5.px-5.mt-2.mb-0 | Grants for updateonly@% |
                .h5.px-5.mt-2.mb-0 +————————————————————————+
                .h5.px-5.mt-2.mb-0 | GRANT USAGE ON *.* TO `updateonly`@`%` |
                .h5.px-5.mt-2.mb-0 | GRANT UPDATE ON `test_db`.* TO `updateonly`@`%` |
                .h5.px-5.mt-2.mb-0 +————————————————————————+
                .h5.px-5.mt-2.mb-0 2 rows in set (0.00 sec) 
                .h5.px-5.mt-5.mb-0 mysql> SHOW GRANTS FOR ‘insertonly’@‘%’;
                .h5.px-5.mt-2.mb-0 +————————————————————————+
                .h5.px-5.mt-2.mb-0 | Grants for insertonly@% |
                .h5.px-5.mt-2.mb-0 +————————————————————————+
                .h5.px-5.mt-2.mb-0 | GRANT USAGE ON *.* TO `insertonly`@`%` |
                .h5.px-5.mt-2.mb-0 | GRANT INSERT ON `test_db`.* TO `insertonly`@`%` |
                .h5.px-5.mt-2.mb-0 +————————————————————————+
                .h5.px-5.mt-2.mb-0 2 rows in set (0.00 sec)
                .h5.px-5.mt-5.mb-0.pb-4 mysql>
          .col-md-4
            figure
              img(src='@/assets/template/tema-2-6.svg', alt='Texto que describa la imagen')
    p.mt-5 Ahora, una vez realizada la creación de la base de datos se realiza la prueba de privilegios: 
    h5.mt-5 Prueba de privilegios
    TabsA.color-acento-botones.mb-5
      //- .tarjeta debe ir acompañado de una de una de estas clases => 
      //- .color-primario, .color-secundario, .color-acento-contenido, .color-acento-botones
      //- estas clases tambien tienen un modificador --borde
      .color-acento-botones--borde.py-4.bg-gris-claro(titulo="Paso 1")
        p.px-4 Ahora solo resta ingresar con otro usuario cada uno de los creados y probar a la base de datos MySQL para ello se debe abrir una consola de Windows: 
        figcaption 
          .h3.mb-0 Paso 1
          p.mt-3 Ejecutar consola de Windows
        figure
          img(src='@/assets/template/tema-2-9.png', alt='Texto que describa la imagen')
      .color-acento-botones--borde.py-4.bg-gris-claro(titulo="Paso 2")
        p.px-4 Una vez en la consola se debe ir al directorio donde está el cliente de consola de comandos instalados. 
        figcaption 
          .h3.mb-0 Paso 2
          p.mt-3 Directorio cliente consola de comandos
        figure
          img(src='@/assets/template/tema-2-10.png', alt='Texto que describa la imagen')
        
      .color-acento-botones--borde.py-4.bg-gris-claro(titulo="Paso 3")
        p.mt-4.px-4 Una vez en el directorio donde están los ejecutables de MySQL, con el siguiente comando se ingresa en la base de datos:
        .row.mt-4.px-4
          .col-7.bg-gris.rounded.letter-spacing-2
            .row
              .col-11
                .h5.px-5.pt-4.mb-4 mysql -u &lt;nombre_usuario&gt; -p
        figcaption.mt-4
          .h3.mb-0 Paso 3
          p.mt-3 Ingreso a la base de datos 
        figure
          img(src='@/assets/template/tema-2-11.png', alt='Texto que describa la imagen')
        
      .color-acento-botones--borde.py-4.bg-gris-claro(titulo="Paso 4")
        p.mt-4.px-4 Ahora queda como ejecución construir las sentencias SQL para hacer insert update, select y delete desde cada uno de los usuarios y donde se puede realizar la práctica de llenar la siguiente tabla de privilegios para completar las pruebas. 
        figcaption 
          .h4.mb-0 Paso 4
          p.mt-3 Práctica de completar las pruebas
        .row.bg-blanco.py-4.px-2
          .tabla-a.color-acento-botones.mb-5 
            table
              caption Referencia Tabla - Norma APA
              thead
                tr
                  th Tabla
                  th(colspan='4') Persona
                  th(colspan='4') Teléfonos
              tbody
                tr
                  th USUARIOS
                  th INSERT
                  th SELECT
                  th UPDATE
                  th DELETE
                  th INSERT
                  th SELECT
                  th UPDATE
                  th DELETE
                tr
                  th readonly
                  th NO
                  th SI
                  th 
                  th 
                  th 
                  th 
                  th 
                  th
                tr
                  th insertonly
                  th 
                  th 
                  th 
                  th 
                  th 
                  th 
                  th 
                  th
                tr
                  th updateonly
                  th 
                  th 
                  th 
                  th 
                  th 
                  th 
                  th 
                  th 














    //- TabsA.color-acento-botones.mb-5
    //-   //- .tarjeta debe ir acompañado de una de una de estas clases => 
    //-   //- .color-primario, .color-secundario, .color-acento-contenido, .color-acento-botones
    //-   //- estas clases tambien tienen un modificador --borde
    //-   .color-acento-botones--borde.py-4.bg-gris-claro(titulo="Paso 1").color-azul.mb-0  
    //-     p.px-4 Ahora solo resta ingresar con otro usuario cada uno de los creados y probar a la base de datos MySQL para ello se debe abrir una consola de Windows: 
    //-     figcaption 
    //-       .h4.mb-0 Paso 1
    //-       p.mt-3 Ejecutar consola de Windows
    //-     figure
    //-       img(src='@/assets/template/tema-2-9.png', alt='Texto que describa la imagen')
    //-   //- .tarjeta debe ir acompañado de una de una de estas clases => 
    //-   //- .color-primario, .color-secundario, .color-acento-contenido, .color-acento-botones
    //-   //- estas clases tambien tienen un modificador --borde
    //-   .color-acento-botones--borde.py-4.bg-gris-claro(titulo="Paso 1").color-azul.mb-0
        //- p.px-4 Ahora solo resta ingresar con otro usuario cada uno de los creados y probar a la base de datos MySQL para ello se debe abrir una consola de Windows: 
        //- figcaption 
        //-   .h4.mb-0 Paso 1
        //-   p.mt-3 Ejecutar consola de Windows
        //- figure
        //-   img(src='@/assets/template/tema-2-9.png', alt='Texto que describa la imagen')




</template>

<script>
import Tabs1 from '../components/Tabs1'
export default {
  name: 'Tema2',
  components: {
    Tabs1,
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
