
# Contexto del Proyecto

* Se ha preparado un Excel con marcos, hojas y travesaños utilizando la plantilla de inserción.
* Se elimina la necesidad de nuevas clases de junquillo: se mantienen `JunquilloExtHO` y `JunquilloSuplemento`; las clases `JunquilloAcople` y `JunquilloHO` dejan de usarse.
* Se añade la columna `SeriesEsclavoComun` para declarar esclavos de series específicas cuando el maestro está en la serie común (p. ej., tapajuntas en SC1 que envía a marcos de `S91;S92`).
* Esta plantilla importa materiales y envía datos de dimensiones de perfiles y descuentos entre ellos.
* El problema de los precios se debía a que el Excel tenía un nombre de tarifa incorrecto; se añadirá un mensaje de error si la tarifa no existe.
* Los travesaños ya aplican descuentos interiores y exteriores al incluir el tipo (Interior, Exterior, etc.) en su columna.
* Se probó un modelo sin DXF de perfiles y la visualización fue correcta.
* El punto de inserción se mantiene coherente al seguir el procedimiento validado y se ajusta automáticamente al insertar el DXF con el valor importado desde Excel (presente en SQL).
* Procedimiento validado como estándar:

  1. Importar los materiales con parámetros de dimensiones, punto de inserción y descuentos entre perfiles.
  2. Insertar los DXF referencia por referencia tras la importación.
  3. Confirmar que el punto de inserción se ajusta automáticamente al cargar cada DXF.
* Ya no es necesario aplicar el plan alternativo de importación en dos fases ni realizar verificaciones adicionales de descuentos o dimensiones.

## Preparación de pruebas de descuentos

* Bases de datos en uso:
  * **A_Descuentos_Scripts**: copia de wincenPRO con todos los materiales y DXF usada para probar los scripts de descuentos de perfiles y detectar ajustes.
  * **A_Descuentos_App**: base restaurada desde wincenPRO donde se insertarán materiales con parámetros y descuentos de la serie S92 y la SC1 común para comparar resultados y afinar el Excel.
* Objetivo de las pruebas: validar qué esclavos corresponden a cada maestro y ajustar los descuentos reales antes de fijar la hoja de Excel de Descuentos.

## Criterio para mostrar tipos de descuento

* Para evitar dudas en documentos o interfaces, mostrar siempre el tipo de descuento en cada línea. Preseleccionar el tipo por defecto cuando exista, pero mantenerlo editable para capturar excepciones y acompañarlo de una breve leyenda o tooltip que aclare los tipos disponibles.
