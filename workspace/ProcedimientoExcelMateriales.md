# Procedimiento para insertar una nueva serie mediante Excel

## IMPORTANTE

1. Colores deben coincidir con los ya dados de alta.
2. Identificar la Clase antes de empezar.
3. DXF con posición correcta antes de importar materiales; de esto dependen PI y PIY.
4. Descuentos con precisión absoluta; cualquier desviación afecta mediciones y secciones.
5. SeriesEsclavoComun debe estar bien configurado o los descuentos no se insertarán.

---

## 1. Meta

Define el contexto de la serie.

**Obligatorio**
- NombreSerie, CódigoSerie, TipoSerie, SeriesComunes, listas de Roles/Clases/TipoCalculo.

**Regla**
- La serie aquí definida controla dónde se buscan los esclavos.

---

## 2. Roles (Marcos, Hojas, Travesaños, Inversoras, Zócalos)

Definición de cada referencia.

**Obligatorio**
- ReferenciaBase, ReferenciaFinal, Color, Lado, Descripción, Precio, TipoCalculo, LongitudBarra, DescuentoSeguridad, GrupoPresupuestado, GrupoProducción, Niveles, Clase, Role.

**Parámetros**
- CI, CE, AI, AE, AL, PI, PIY.

**Regla**
- Ningún parámetro vacío.

---

## 3. Descuentos Maestro–Esclavo

Define compatibilidades y fórmulas.

**Reglas clave**
- Interior por defecto.
- Travesaño como esclavo siempre Mecanizado.
- Vidrio y Junquillo siempre Interior.
- Si se indica ReferenciaBase → sobrescribe genéricos.
- SeriesEsclavoComun permite SC1, %, múltiples series separadas por ;.

**Fórmulas**
- P_Formula → PDistances
- Z_Formula → ZPDistances

---

## 4. Series Comunes (SC1)

Igual que una serie normal.

**Regla principal**
- Maestro = común → Esclavo = series incluidas en SeriesEsclavoComun.

---

## 5. Checklist previo

- Roles completos (Role + Clase).
- Parámetros geométricos completos.
- Sin duplicados.
- Descuentos completos.
- SeriesComunes declarada.
- SeriesEsclavoComun correcto.

---

## 6. Orden de importación

1. Meta
2. Roles
3. Descuentos
4. Series comunes
