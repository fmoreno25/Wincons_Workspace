# Plantilla de inserción filtrable por `ReferenciaBase`

Usa esta plantilla en Excel para preparar las importaciones. Permite filtrar rápidamente por `ReferenciaBase` y completar los parámetros de dimensiones sin omisiones.

## Novedades recientes de la plantilla

* Se añadieron más **clases** en la lista desplegable de la hoja de materiales para cubrir todos los perfiles necesarios y evitar que falten valores al rellenar.
* Hay un **botón** que pliega y despliega las columnas menos usadas, dejando visibles solo las columnas clave mientras se cargan datos.
* Cada hoja de materiales incorpora una **columna extra al final** pensada para filtrar las `ReferenciaFinal` y localizar rápido las filas que deben ajustarse.

## Estructura de columnas sugerida

| ReferenciaBase | ReferenciaFinal | Serie | SeriesComunes | SeriesEsclavoComun | Role | Clase | TipoCalculo | Color | Lado | LongitudBarra | GrupoPresupuesto | GrupoProduccion | Niveles | CI | CE | AI | AE | AL | PI | PIY | DescuentoSeguridad |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

* Añade filtros en la fila de encabezados y agrupa por `ReferenciaBase` para revisar que cada perfil tiene todos los parámetros cumplimentados.
* Si un perfil es común (por ejemplo en SC1), rellena `SeriesEsclavoComun` con las series a las que aplica (separadas por `;`).
* Valida que las columnas de dimensiones (`CI`, `CE`, `AI`, `AE`, `AL`) y puntos de inserción (`PI`, `PIY`) no queden vacías antes de importar.
* Incluye los descuentos específicos en `DescuentoSeguridad` y confirma que los valores cuadran con la medición esperada.

## Uso recomendado

1. Crea una copia de esta tabla en Excel y activa el filtro en la fila de encabezados.
2. Filtra por `ReferenciaBase` para introducir o revisar todos los parámetros de cada perfil.
3. Después de completar S92 y SC1, duplica la hoja para las ocho series restantes y rellena con sus datos correspondientes.
4. Exporta o pega los datos en el Excel de importación final que consume la app.
