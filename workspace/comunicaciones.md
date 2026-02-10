## Actualización reciente

* Ya está incorporado el RGB de Materia Prima en el Excel y funciona correctamente.
* Los colores también se insertan correctamente en `AmbientRed`, `AmbientGreen` y `AmbientBlue`.
* La columna `Trasparenci` se incorpora y funciona correctamente.
* Ahora se activa automáticamente el check de la línea de producción en Tipos de producción para que el informe de cortes salga correctamente.
* Los colores de materia prima ya se insertan sin checks ni datos irrelevantes.
* En la fase 5 (Acristalamientos) se añade una nueva columna para indicar el espesor de vidrio concreto:
  * Si se informa un espesor, se pasa a modo manual.
  * La app inserta los registros de la línea concreta y solo para ese espesor.
  * Esta opción está pensada para casos excepcionales.

* Se confirma que las clases de junquillo vigentes son `JunquilloExtHO` y `JunquilloSuplemento`; se retiran `JunquilloAcople` y `JunquilloHO`.
* Nueva columna `SeriesEsclavoComun` para definir esclavos de series específicas cuando el maestro pertenece a una serie común (ej.: tapajuntas en SC1 que envía a marcos de `S91;S92`).
* La plantilla Excel de materiales incorpora más clases ligadas a sus columnas, un botón para plegar/desplegar columnas poco usadas y una columna adicional al final de cada hoja para filtrar rápido las `ReferenciaFinal`.

## Resumen de estado — Trabajo completado (abisagradas)

**Estado general**

* Alcance completo finalizado.
* Base de datos lista para dar de alta.
* No quedan tareas pendientes dentro del alcance actual.
* Cualquier ajuste posterior se realizará solo si surge tras el alta.

**Pruebas**

* Pruebas realizadas y validadas.
* Funcionamiento correcto en todos los casos revisados.

**Acristalamientos**

* Acristalamientos importados desde Excel a través de la app.
* Correcta generación en modelo y secciones.

**Funcionamiento técnico**

* Secciones correctas con juntas de acristalamiento y estanqueidad.
* Reglas de perfiles y resto de reglas funcionando según lo previsto.
* Comportamiento validado para series abisagradas.

**Pendiente en abisagradas**

* Crear escandallos de perfiles y accesorios.
* Programar herraje Roto (fase final).

**Siguiente fase**

* Inicio del trabajo en correderas.
