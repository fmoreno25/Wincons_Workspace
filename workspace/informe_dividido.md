# Informe separado por ámbito

## Wincons y App

- Flujo validado en **A_Descuentos_Scripts** y **A_Descuentos_App**: el procedimiento estándar de importación (materiales con parámetros y descuentos, inserción de cada DXF referencia por referencia y ajuste automático del punto de inserción) funciona correctamente sin bloqueos abiertos para Alex.
- Junquillos: los especiales quedan cubiertos con las clases `JunquilloExtHO` y `JunquilloSuplemento`; no se requieren `JunquilloAcople` ni `JunquilloHO`.
- Compatibilidades y esclavos: la columna **SeriesEsclavoComun** habilita declarar esclavos comunes que se relacionan con maestros de series específicas (p. ej., tapajuntas en SC1 que envía a marcos de `S91;S92`) con coincidencia exacta de nombre de clase.
- Descuentos y fórmulas: los travesaños ya incluyen los descuentos exteriores al definir el tipo; `ZPDistance` opera con fórmulas como `X-AL` para descontar el lado opuesto al PIX.
- Seguimiento de importaciones: las series C16 RPT 70_HO_S92, C16 40_S60, C16 RPT 70_HO PLUS_S79P, C16 RPT 70_HO_S79, CE 40_S60E y Materiales_Comunes_SC1 ya están importadas y validadas en PrefWise; faltan CE 40_S60E, CE 45 XTA_S56E, CE 45_S70E, CE 55 XTA_S66E, CE RPT 45_S59E, CE RPT 60 HO_S90E, CE RPT 70 HO_S91E, CE RPT MAXLight_S22E, CO Efficient_S68, CO RPT Efficient Plus_S78, CO RPT Evoque_S82 y PlantillaMaterialesV4.
- Próximos pasos en la app: revisar niveles de ubicación, clases y metadatos antes de cerrar cada importación; identificar todos los perfiles esclavos comunes en BD Lingote; y actualizar los Excel de S92 y SC1 con los perfiles validados antes de reimportar.

## Centroalum

- Copia para el workspace de Centroalum: la sección vive también en `centroalum/informe_centroalum.md` para compartirla de forma independiente.
- Importaciones en la app sobre la base de datos de Centroalum: cargar la serie **SC1** (comunes) junto al resto de series y, antes de importar, eliminar la tabla **Distancias** en SQL.
- Descuentos pendientes (incluidas S79/S79P): evitar comodines de serie (`S%`) en **SeriesEsclavoComún**, listar las series explícitas y confirmar que el marco envía el descuento Exterior al marco esclavo, la hoja al vierteaguas **AP560000** y la solera aplica reglas **Z** por altura (marco 40 → Z=40, marco 45 → Z=45, etc.).
- Excel por completar: añadir descuentos en los maestros Marco, Hoja y HojaExt (necesario porque la hoja normal no crea descuentos), ajustar nombres de META desde la plantilla y actualizar el `.xlsm` con macro antes de convertirlo a `.xlsx`.
- DXF y pruebas: cargados los DXF 791167 y 601126 en **A_Descuentos_App** como base para las verificaciones de descuentos de S79/S79P.
