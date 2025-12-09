# Informe Centroalum

## Importaciones y preparación de bases
- Para las importaciones en la app sobre la base de datos de Centroalum, cargar la serie **SC1** (comunes) junto al resto de series y eliminar previamente la tabla **Distancias** en SQL.

## Descuentos y reglas
- En los Excel de descuentos pendientes (incluidas S79/S79P), evitar comodines de serie (`S%`) en **SeriesEsclavoComún**; listar las series explícitas para que la app respete las clases y evite descuentos incorrectos.
- Tareas de descuentos pendientes: revisar que el marco envía el descuento Exterior al marco esclavo; que la hoja envía descuento al vierteaguas **AP560000**; y que la solera aplique reglas **Z** por altura agrupando por medida (marco 40 → Z=40, marco 45 → Z=45, etc.).

## Pendientes por serie
- Para completar los Excel de las series restantes: añadir descuentos en los maestros Marco, Hoja y HojaExt (este último necesario porque la hoja normal no crea descuentos), ajustar los nombres de META desde la plantilla y actualizar el `.xlsm` con macro antes de pasarlo a `.xlsx`.

## Referencias DXF
- Recordatorio de DXF cargados en **A_Descuentos_App**: referencias 791167 y 601126, usados como base para las verificaciones de descuentos de S79/S79P.
