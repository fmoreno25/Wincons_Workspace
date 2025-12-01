
# Contexto del Proyecto

* Se ha preparado un Excel con marcos, hojas y travesaños utilizando la plantilla de inserción.
* Esta plantilla importa materiales y envía datos de dimensiones de perfiles y descuentos entre ellos.
* En la primera prueba, los materiales se insertaron pero **los precios no se importaron**.
* Los travesaños solo aplicaron **descuentos interiores**, faltando los de la cara exterior.
* Se probó un modelo sin DXF de perfiles y la visualización fue correcta.
* Al ajustar el punto de inserción a la derecha, se perdieron los datos de dimensiones.

  * El punto de inserción parece estar **vinculado al DXF**.
  * Aunque el parámetro llega desde Excel y aparece en SQL, **no aparece en PrefWise**.
  * Modificarlo desde PrefWise provoca que se rompan otros datos.
* Procedimiento de prueba recomendado:

  1. Importar los materiales.
  2. Añadir un DXF a un perfil para validar.
  3. Modificar el punto de inserción.
* Riesgo conocido: **desajuste de descuentos entre perfiles** tras cambiar el punto de inserción.
* Plan alternativo si falla el procedimiento:

  * Importar en dos fases:

    1. Materiales sin parámetros de dimensiones ni descuentos.
    2. Insertar los DXF.
    3. Importar los parámetros de dimensiones y descuentos posteriormente.
