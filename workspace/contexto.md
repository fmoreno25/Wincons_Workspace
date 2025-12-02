
# Contexto del Proyecto

* Se ha preparado un Excel con marcos, hojas y travesaños utilizando la plantilla de inserción.
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
