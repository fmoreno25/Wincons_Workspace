## Pruebas de inserción de materiales y descuentos

* Se prepararon pruebas usando **A_Descuentos_Scripts** (copia de wincenPRO) y **A_Descuentos_App** restaurada con los DXF para insertar materiales con parámetros y descuentos de las series S92 y SC1.
* Hallazgos sobre junquillos:
  * Los junquillos especiales ya se cubren con las clases existentes `JunquilloExtHO` y `JunquilloSuplemento`; se descartan las clases adicionales `JunquilloAcople` y `JunquilloHO`.
  * La importación con la app debe apoyarse únicamente en estas clases vigentes para que las juntas se añadan como esclavos del junquillo.
* Compatibilidades y esclavos:
  * El zócalo envía a la hoja como esclava, pero la Exterior no es compatible; revisar cómo excluirla.
  * Es crucial guardar los DXF con el punto de inserción correcto para que todo cuadre al insertarlos.
  * Cuando Marco y Travesaño se usan como maestros, no envían los descuentos de la solera como esclava; podría deberse a la clase ubicada en Comunes.
  * El Tapajuntas como maestro tampoco inserta descuentos, posiblemente por estar en SC1; debería enviar a todas las series y se plantea declararlas compatibles en la misma celda separadas por coma (p. ej., `S91, S92`).
* Ajustes propuestos: añadir nuevas clases `JunquilloAcople` y `JunquilloHO` para soportar los junquillos especiales y evitar fallos en la importación.

## Actualización Alex (importación y descuentos)

1. Se añadieron las clases especiales `JunquilloAcople` y `JunquilloHO`; tras reimportar el Excel, no hay errores y los descuentos de juntas se aplican únicamente a sus clases correspondientes.
2. La hoja exterior ya tiene asignada la clase `HojaExt`, y la relación maestro–esclavo funciona correctamente.
3. Compatibilidad por nombre de clase: ahora funciona con el nombre exacto, sin depender de comodines que terminen en `%`.
4. Tapajuntas y compatibilidades por serie: se incorpora la columna `SeriesEsclavoComun` para declarar esclavos de series comunes que deben relacionarse con maestros de series específicas (p. ej., un tapajuntas en SC1 como maestro del marco en `S91;S92`). Es aplicable también a los Excel de las series por si aparece algún perfil especial.
5. Fórmulas de `ZPDistance`: funcionan correctamente; validado el caso `X-AL` para aplicar descuentos en el lado opuesto al PIX.
6. Seguimiento: recordatorio sobre DXF y punto de inserción; sin acciones pendientes. No hay bloqueos abiertos para Alex.

## Notas tras pruebas de importación S92 y SC1

* Las incidencias detectadas se debieron principalmente a parámetros incorrectos en el Excel; con datos correctos la app responde bien.
* Es imprescindible cumplimentar `SeriesEsclavoComun` para perfiles comunes y definir las dimensiones con precisión, pues afectan directamente a los descuentos y mediciones.
* Los descuentos deben revisarse con cuidado: cualquier desviación altera la medición o la sección resultante.
* Con la app lista pueden crearse todas las series, pero primero hay que identificar todos los perfiles esclavos comunes para evitar omisiones.
