
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

## Flujo Excel → App validado (creación de BD desde cero)

* La base de datos puede partir completamente vacía (sin máquina, grupos, planta, proveedores ni tarifas) y el proceso completo funciona.
* Todas las fases existentes han sido ejecutadas y validadas con éxito, confirmando estructura y lógica.

### Fase 0 — Estructura base

* Importación desde Excel de grupos, planta, proveedores y tarifas.
* Limpieza previa de datos existentes antes de importar.

### Fase 1 — Colores

* Importación de familias, colores y parámetros.
* Asignación de Materia Prima desde Excel.

### Fase 2 — Materiales y precios

* Importación de materiales, precios y parámetros dimensionales.
* Estudio previo de la posición correcta de los DXF para asignar valores.
* Estructura del Excel:
  * **Meta**: serie, proveedor, máquina, tipos de cálculo, clases, descuentos y roles.
  * **Materiales**: datos principales con selección mediante desplegables.
  * **Descuentos**: parametrización de descuentos entre perfiles.

### Fase 3 — Geometría

* Fase definida conceptualmente.
* Orientada a la introducción de DXF y asignación automática de parámetros.

### Fase 4 — Opciones

* Sistema de opciones implementado: Meta, OpcionesMaterial, OpcionesControl, OpcionesSerie y OpcionesDisparadas.
* Funcionamiento validado en su totalidad.

### Fase 5 — Acristalamientos

* Definición de juntas interiores con rangos mínimos y máximos.
* Gestión de junquillos desplazados mediante override cuando aplica.
* Cálculo basado en `AnchoTotalAcristalamiento`.
* Comportamiento validado:
  * Correderas: uso de `_JunquilloFicticio` y altura 0.
  * Perfiles normales: altura desde `dbo.Perfiles.Altura` con override cuando corresponde.

## Pendientes para cerrar la automatización

1. **Automatización de divisa:** identificar tabla y columna donde persistir la divisa y crearla desde la app.
2. **Color de materia prima:** localizar el almacenamiento en BD y automatizar su asignación desde Excel.
3. **Fase 3 — Geometría:** desarrollo técnico de importación DXF y asignación automática de parámetros.
4. **Simplificación del sistema de opciones:** reducir combinaciones en OpcionesDisparadas y separar cambio de serie vs. selección interna de materiales.
5. **Fase 6 — Reglas:** consolidar el trabajo basado en reglas y documentar alcance final.
6. **Fase 7 — Escandallos:** estandarizar escandallos genéricos e integrarlos con reglas y modelos.
