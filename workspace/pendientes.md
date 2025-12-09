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

9. **Nuevas tareas tras pruebas S92/SC1:**
   * Identificar todos los perfiles esclavos comunes de cada serie (revisar BD Lingote) antes de completar las importaciones.
   * Actualizar los Excel de S92 y SC1 con los perfiles validados y reimportar con la app para confirmar que todo queda correcto.
   * Rellenar los Excel de las ocho series restantes con los parámetros definitivos y cargarlos en la app.
   * Revisar niveles de ubicación de materiales, clases y demás metadatos antes de cerrar cada importación.

10. **Seguimiento de Excel pendientes:**
    * Aún falta añadir parámetros de dimensiones y descuentos antes de importar las siguientes hojas: CE 40_S60E, CE 45 XTA_S56E, CE 45_S70E, CE 55 XTA_S66E, CE RPT 45_S59E, CE RPT 60 HO_S90E, CE RPT 70 HO_S91E, CE RPT MAXLight_S22E, CO Efficient_S68, CO RPT Efficient Plus_S78, CO RPT Evoque_S82 y PlantillaMaterialesV4.
    * Las hojas C16 40_S60, C16 RPT 70 HO PLUS_S79P, C16 RPT 70 HO_S79, C16 RPT 70_S92, CE 40_S60E y Materiales_Comunes_SC1 ya están importadas y validadas en PrefWise a través de **A_Descuentos_App**.
    * Próximo paso: actualizar los Excel pendientes, validarlos en PrefWise e importarlos con la app.
 * Identificar todos los perfiles esclavos comunes de cada serie (revisar BD Lingote) antes de completar las importaciones.
  * Actualizar los Excel de S92 y SC1 con los perfiles validados y reimportar con la app para confirmar que todo queda correcto.
  * Rellenar los Excel de las ocho series restantes con los parámetros definitivos y cargarlos en la app.
  * Revisar niveles de ubicación de materiales, clases y demás metadatos antes de cerrar cada importación.

## Notas recientes (S79 / S79P y descuentos)

* **DXF cargados:** se insertaron los DXF 791167 y 601126 en **A_Descuentos_App**.
* **Series S79P y S79:**
  * S79P solo aporta el marco.
  * En descuentos, todos los perfiles deben asociarse a clases de **S79**; revisar la clase de cada perfil antes de disparar descuentos.
* **Descuentos pendientes por maestro → esclavo:**
  * Marco: aplicar descuento de **Exterior** sobre el marco esclavo.
  * Hoja: enviar descuento al Vierteaguas solera **AP560000**.
  * Solera: reglas **Z** por altura de marco; marcar series por grupo (marco 40 → Z=40, marco 45 → Z=45…) y crear clusters por medida para aplicar el Z fijo según el marco del grupo.
* **HojaExt:** el maestro actual no envía descuentos; al crear un nuevo maestro HojaExt sí funciona.
* **SeriesEsclavoComún en SC1:** evitar comodines `S%` porque envían a todas las series; listar series explícitas (p. ej., `S79;S92;S60;…`) para que la app respete la clase y evite descuentos incorrectos.
* **PrefWise:** corregidos los textos a “Mecanizado Interior” y “Mecanizado Exterior” (con espacio) para que se muestren alineados.
* **Punto de inserción Y:** los Excel nuevos no incluyen la columna; de momento solo la plantilla, juntas y cepillos la usan; no se requiere acción.
* **Procedimiento para los Excel restantes:**
  1. Añadir descuento en Maestro **Marco** con esclavo **Marco** de tipo Exterior.
  2. Añadir descuento en Maestro **Hoja** con esclavo **VierteaguasHoja**.
  3. Añadir descuento en Maestro **HojaExt** porque la hoja normal no los crea.
  4. Ajustar los nombres de **META** copiándolos de la plantilla.
  5. Actualizar el Excel **.xlsm** con macro y después pasarlo a **.xlsx**.
* **Importación en la app:** al importar añadir **SC1** (comunes) junto a las demás series y, antes, eliminar la tabla **Distances** en SQL. Estas acciones se aplican sobre la base de datos de **Centroalum**.
