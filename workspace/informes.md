

## Pruebas de inserción de materiales y descuentos

* Se prepararon pruebas usando **A_Descuentos_Scripts** (copia de wincenPRO) y **A_Descuentos_App** restaurada con los DXF para insertar materiales con parámetros y descuentos de las series S92 y SC1.
* Hallazgos sobre junquillos:
  * El junquillo **794000** debe tener la clase `SC1_JunquilloAcople` y el **GO579000** la clase `SC1_JunquilloHO` para diferenciar los modelos sin junta de vidrio.
  * La importación con la app falla al no contemplar estas clases; sin la clase correcta, las juntas no se añaden como esclavos del junquillo.
* Compatibilidades y esclavos:
  * El zócalo envía a la hoja como esclava, pero la Exterior no es compatible; revisar cómo excluirla.
  * Es crucial guardar los DXF con el punto de inserción correcto para que todo cuadre al insertarlos.
  * Cuando Marco y Travesaño se usan como maestros, no envían los descuentos de la solera como esclava; podría deberse a la clase ubicada en Comunes.
  * El Tapajuntas como maestro tampoco inserta descuentos, posiblemente por estar en SC1; debería enviar a todas las series y se plantea declararlas compatibles en la misma celda separadas por coma (p. ej., `S91, S92`).
* Ajustes propuestos: añadir nuevas clases `JunquilloAcople` y `JunquilloHO` para soportar los junquillos especiales y evitar fallos en la importación.
