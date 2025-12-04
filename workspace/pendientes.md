
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
8. **Pendiente con Alex:** la app de importación no contempla las clases `SC1_JunquilloAcople` (junquillo 794000) ni `SC1_JunquilloHO` (junquillo GO579000), lo que provoca errores y evita que las juntas se añadan como esclavos del junquillo. Solicitar soporte y creación de las nuevas clases `JunquilloAcople` y `JunquilloHO`.
9. Ajustar compatibilidades de esclavos: el zócalo envía a la hoja como esclava, pero la Exterior no es compatible; revisar cómo excluirla.
10. Asegurar que los DXF se guarden con el punto de inserción correcto para que cuadren al importarlos.
11. Marco y Travesaño como maestros no envían los descuentos de la solera como esclava, posiblemente por la clase ubicada en Comunes; investigar.
12. El Tapajuntas como maestro no inserta descuentos; puede deberse a que está en SC1. Evaluar declararlo compatible con todas las series en la misma celda (p. ej., `S91, S92`).
13. **Sugerencias para Alex:**
    * Añadir el punto de inserción Y a la importación.
    * Usar una fórmula de `ZPDistance` del tipo AL-PI o AL-AL para ajustar el eje Z de las gomas según las medidas de cada junquillo.
    * Revisar que, tras restaurar **A_Descuentos_App** desde wincenPRO (con DXF), los errores por `JuntaVidrioExt` desaparecieron al borrar `Distances`; documentar la causa.
