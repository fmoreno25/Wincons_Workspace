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
   * Clases especiales `JunquilloAcople` y `JunquilloHO` añadidas y funcionando sin errores tras reimportar el Excel.
   * La hoja exterior tiene la clase `HojaExt`, corrigiendo la relación maestro–esclavo.
   * Compatibilidad por nombre de clase operativa con coincidencia exacta (sin comodines `%`).
   * Tapajuntas: se gestionará manualmente por serie en la hoja de descuentos.
   * Fórmulas de `ZPDistance` verificadas; ejemplo `X-AL` aplica el descuento en el lado opuesto al PIX.
   * Recordatorio: mantener el punto de inserción correcto en los DXF.
