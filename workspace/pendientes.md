# Tareas Pendientes

1. **Resuelto:** los precios no se insertaban por un nombre de tarifa incorrecto en el Excel. Se añadirá un mensaje de error cuando la tarifa no exista en destino.
2. **Resuelto:** los travesaños ya incluyen los descuentos de la cara exterior al añadir el tipo (Interior, Exterior, etc.) en su columna.
3. **Validado:** procedimiento definitivo confirmado como correcto:

   * Importación de materiales con parámetros de dimensiones, punto de inserción y descuentos entre perfiles.
   * Inserción de un DXF referencia por referencia tras la importación.
   * Ajuste automático del punto de inserción al cargar el DXF según el valor importado desde Excel y presente en SQL.
4. El punto de inserción no presenta inconvenientes siguiendo el procedimiento validado.
5. No es necesario ejecutar el plan alternativo de importación en dos fases.
6. No se requieren pasos adicionales de verificación relacionados con descuentos o dimensiones.
7. Validación final: el flujo completo funciona correctamente y queda establecido como estándar.
8. **Alex — Estado actual:** sin bloqueos pendientes. Últimos ajustes completados:
   * Las clases `JunquilloAcople` y `JunquilloHO` se eliminan; ya existen `JunquilloExtHO` y `JunquilloSuplemento` para cubrir esos casos.
   * Se añade la columna `SeriesEsclavoComun` para definir esclavos compatibles por serie desde series comunes (p. ej., un tapajuntas en SC1 que envía a marcos de `S91;S92`).
   * La hoja exterior tiene la clase `HojaExt`, corrigiendo la relación maestro–esclavo.
   * Compatibilidad por nombre de clase operativa con coincidencia exacta (sin comodines `%`).
   * Tapajuntas: se gestionará manualmente por serie en la hoja de descuentos o con la nueva columna de serie común.
   * Fórmulas de `ZPDistance` verificadas; ejemplo `X-AL` aplica el descuento en el lado opuesto al PIX.
   * Recordatorio: mantener el punto de inserción correcto en los DXF.

9. **Estado tras pruebas S92/SC1:**
   * Identificar todos los perfiles esclavos comunes de cada serie (revisar BD Lingote) antes de completar las importaciones: **Pendiente**.
   * Actualizar los Excel de S92 y SC1 con los perfiles validados y reimportar con la app para confirmar que todo queda correcto: **Hecho**.
   * Rellenar los Excel de las ocho series restantes con los parámetros definitivos y cargarlos en la app: **Hecho**.
   * Revisar niveles de ubicación de materiales, clases y demás metadatos antes de cerrar cada importación: **Hecho**.

10. **Seguimiento de Excel pendientes:**
    * Parámetros de dimensiones y descuentos completados e importados en PrefWise para: CE 40_S60E, CE 45 XTA_S56E, CE 45_S70E, CE 55 XTA_S66E, CE RPT 45_S59E, CE RPT 60 HO_S90E, CE RPT 70 HO_S91E, CE RPT MAXLight_S22E, CO Efficient_S68, CO RPT Efficient Plus_S78, CO RPT Evoque_S82 y PlantillaMaterialesV4 (**Hecho**).
    * Las hojas C16 40_S60, C16 RPT 70 HO PLUS_S79P, C16 RPT 70 HO_S79, C16 RPT 70_S92, CE 40_S60E y Materiales_Comunes_SC1 ya están importadas y validadas en PrefWise a través de **A_Descuentos_App**.
    * Próximo paso: mantener las validaciones en PrefWise tras cualquier ajuste puntual.

## Nuevos pendientes (completados)

1. Añadir las juntas personalizadas en la nueva columna **ReferenciaBaseEsclavo** para el Excel **CE RPT MAXLight_S22E**: **Hecho**.
2. Revisar uno por uno los catálogos para identificar perfiles complementarios, juntas y lo que corresponda: **Hecho**.
3. Maestro **Hoja** → esclavo **Vierteaguas solera AP560000** en las series compatibles: **Hecho**.
4. Revisar puntos de inserción de las gomas para hacerlo común y fácil: **Hecho**.
5. Establecer una medida común para todos los vidrios (¿**-14**?): **Hecho**.
6. Asignar las juntas de perfiles de la serie **S60** (carga por **Regla** junto con los descuentos): **Hecho**.

## Notas recientes (S79 / S79P y descuentos) — completado

* **DXF cargados:** se insertaron los DXF 791167 y 601126 en **A_Descuentos_App**.
* **Series S79P y S79:**
  * S79P solo aporta el marco.
  * En descuentos, todos los perfiles deben asociarse a clases de **S79**; revisión realizada antes de disparar descuentos.
* **Descuentos por maestro → esclavo (completados):**
  * Marco: descuento de **Exterior** aplicado sobre el marco esclavo.
  * Hoja: descuento enviado al Vierteaguas solera **AP560000**.
  * Solera: reglas **Z** por altura de marco aplicadas; series marcadas por grupo y clusters por medida definidos para aplicar el Z fijo según el marco del grupo.
* **HojaExt:** se creó el nuevo maestro HojaExt y ya envía descuentos correctamente.
* **SeriesEsclavoComún en SC1:** se evitaron comodines `S%` y se listaron series explícitas (p. ej., `S79;S92;S60;…`) para respetar clases y evitar descuentos incorrectos.
* **PrefWise:** textos corregidos a “Mecanizado Interior” y “Mecanizado Exterior” (con espacio).
* **Punto de inserción Y:** se mantiene el criterio actual; plantilla, juntas y cepillos siguen usando la columna cuando aplica.
* **Procedimiento para los Excel restantes (realizado):**
  1. Descuento en Maestro **Marco** con esclavo **Marco** de tipo Exterior.
  2. Descuento en Maestro **Hoja** con esclavo **VierteaguasHoja**.
  3. Descuento en Maestro **HojaExt** para cubrir los casos en que la hoja normal no los crea.
  4. Nombres de **META** ajustados copiándolos de la plantilla.
  5. Excel **.xlsm** actualizado con macro y convertido a **.xlsx**.
* **Importación en la app:** **SC1** (comunes) añadido junto a las demás series; tabla **Distances** eliminada en SQL antes de importar. Acciones aplicadas sobre la base de datos de **Centroalum**.
