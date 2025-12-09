# Informe separado por ámbito

## Wincons y App

- Importación y descuentos validados en las bases **A_Descuentos_Scripts** y **A_Descuentos_App**: junquillos especiales cubiertos con las clases existentes `JunquilloExtHO` y `JunquilloSuplemento`; no se necesitan `JunquilloAcople` ni `JunquilloHO`.
- Compatibilidades: la columna **SeriesEsclavoComun** permite declarar esclavos de series comunes que deben relacionarse con maestros de series específicas (p. ej., tapajuntas en SC1 que envía a marcos de `S91;S92`), usando coincidencia exacta de nombre de clase.
- Procedimiento estándar confirmado para importaciones: cargar materiales con parámetros y descuentos, insertar cada DXF referencia por referencia y validar que el punto de inserción se ajusta automáticamente con el valor importado desde Excel/SQL.
- Descuentos: los travesaños ya incluyen los descuentos exteriores al indicar el tipo; el ZPDistance funciona con fórmulas como `X-AL` para aplicar descuentos al lado opuesto al PIX.
- Validaciones finales: el flujo completo funciona correctamente sin bloqueos abiertos para Alex; no es necesario el plan alternativo de importación en dos fases ni verificaciones adicionales de descuentos o dimensiones.

## Centroalum

- Copia lista para el workspace de Centroalum: `centroalum/informe_centroalum.md` contiene esta sección en un archivo separado.
- Para las importaciones en la app sobre la base de datos de Centroalum, cargar la serie **SC1** (comunes) junto al resto de series y eliminar previamente la tabla **Distancias** en SQL.
- En los Excel de descuentos pendientes (incluidas S79/S79P), evitar comodines de serie (`S%`) en **SeriesEsclavoComún**; listar las series explícitas para que la app respete las clases y evite descuentos incorrectos.
- Tareas de descuentos pendientes: revisar que el marco envía el descuento Exterior al marco esclavo; que la hoja envía descuento al vierteaguas **AP560000**; y que la solera aplique reglas **Z** por altura agrupando por medida (marco 40 → Z=40, marco 45 → Z=45, etc.).
- Para completar los Excel de las series restantes: añadir descuentos en los maestros Marco, Hoja y HojaExt (este último necesario porque la hoja normal no crea descuentos), ajustar los nombres de META desde la plantilla y actualizar el `.xlsm` con macro antes de pasarlo a `.xlsx`.
- Recordatorio de DXF cargados en **A_Descuentos_App**: referencias 791167 y 601126, usados como base para las verificaciones de descuentos de S79/S79P.
