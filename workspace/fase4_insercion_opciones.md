# Fase 4 – Inserción de Opciones

## Contexto técnico para la app de importación (PrefSuite)

Este documento define el modelo estándar para crear opciones, poblarlas desde `MaterialesBase` y generar disparadas que activen la lógica de compatibilidades en PrefSuite. Toda la app de importación debe basarse en estas reglas.

---

## 1. Propósito

La Fase 4 permite:

* Crear **opciones visibles** por serie (Marco, Hoja, Travesaños…).
* Crear **opciones internas genéricas** (VeMarco, VeHoja…) que actúan como maestros.
* Poblar ambas a partir de **Clases** de `MaterialesBase`.
* Generar **TriggeredXML** que sincroniza valores visibles ↔ internos.
* Activar la lógica de compatibilidades (ocultar incompatibles, mostrar compatibles).

Este es el patrón oficial que la aplicación debe reproducir.

---

## 2. Modelo funcional

### 2.1 Opciones visibles

Ejemplos: *Marco Ventana S92*, *Hoja Ventana Neo*. Son las que el usuario selecciona.

Características:

* Tipo **Elección**.
* Contienen valores procedentes de `MaterialesBase` filtrados por **Clase**.
* Tienen valores base “oculta” y “Sin”.
* Viven en carpetas por serie (ej.: `❶ Perfiles Ventana S92`).

---

### 2.2 Opciones genéricas (internas)

Ejemplos: *VeMarco*, *VeHoja*. No se muestran al usuario.

Características:

* Tipo **Material**.
* Reúnen **todas** las referencias compatibles de todas las series.
* Se sitúan en `Cambio Perfiles`.
* Son el destino de las disparadas.

---

### 2.3 Disparadas

Las disparadas vinculan valores visibles con los internos:

```
Marco_X → VeMarco = Marco_X
Hoja_Y → VeHoja = Hoja_Y
```

Permiten:

* Activar perfiles compatibles.
* Ocultar perfiles incompatibles.
* Mantener la sincronía del modelo entre series, marcos, hojas y travesaños.

---

## 3. Plantilla Excel para la app (entrada de datos)

La app leerá este Excel y generará automáticamente opciones, valores y disparadas.

### 🟦 HOJA 1 — SERIES Y OPCIONES VISIBLES

Definen qué opciones existen para cada serie y cómo se cargan.

| Serie | Opción | Carpeta | Clase | Añadir oculta | Añadir Sin | Descripción |
| ----- | ------------------ | --------------- | ------ | ------------- | ---------- | ----------------------- |
| 4000 | Marco Ventana 4000 | ❶ Perfiles 4000 | 4Marco | 1 | 1 | Selección de marco 4000 |
| 4000 | Hoja Ventana 4000 | ❶ Perfiles 4000 | 4Hoja | 1 | 1 | Selección de hoja 4000 |
| Neo | Marco Ventana Neo | ❷ Perfiles Neo | 6Marco | 1 | 1 | Selección de marco Neo |
| Neo | Hoja Ventana Neo | ❷ Perfiles Neo | 6Hoja | 1 | 1 | Selección de hoja Neo |

**Interpretación por la app:**

* Crea la opción si no existe.
* Inserta “oculta” y “Sin”.
* Pobla valores desde `MaterialesBase` por Clase.
* Ordena la lista final de perfiles.

---

### 🟪 HOJA 2 — OPCIONES COMUNES (OCULTAS)

Son el núcleo de compatibilidades.

| OpciónComun | Clase(s) | Añadir oculta | Añadir Sin | Descripción |
| ----------- | ------------- | ------------- | ---------- | --------------------------- |
| VeMarcoInt | 4Marco,6Marco | 1 | 1 | Cambio de perfiles de marco |
| VeHoja | 4Hoja,6Hoja | 1 | 1 | Cambio de perfiles de hoja |

**Interpretación por la app:**

* Crea la opción.
* Inserta “oculta” y “Sin”.
* Pobla todas las referencias compatibles (una por Clase).
* Sirve de destino para todas las disparadas.

---

### 🟩 HOJA 3 — DISPARADAS

Define qué ocurre automáticamente cuando el usuario selecciona un valor.

| OpciónOrigen | ValorOrigen | OpciónDestino | Acción | ValorDestino |
| ------------------ | ----------- | ------------------ | ----------- | ------------ |
| Marco Ventana 4000 | * | VeMarcoInt | IgualValor | * |
| Marco Ventana 4000 | * | VeHoja | Ocultar | oculta |
| Marco Ventana Neo | * | VeMarcoInt | IgualValor | * |
| Serie Abisagrada | 4000 | Marco Ventana 4000 | Seleccionar | primer_valor |

**Interpretación por la app:**

* *IgualValor*: copia el valor origen dentro de la opción interna.
* *Ocultar*: asigna “oculta” al destino.
* *Seleccionar*: aplica un valor predefinido.
* "*" = se aplica a todos los valores visibles.

---

## 4. Resultado final en PrefSuite

Con estos datos procesados por la app:

* Todas las opciones visibles quedan generadas por serie.
* Todas las internas se llenan con valores de todas las clases.
* El modelo dispone de relaciones de compatibilidad completas.
* Las disparadas sincronizan la selección con el estado interno.
* El usuario ve únicamente perfiles compatibles con la serie y el marco elegidos.

El sistema se comporta como un motor lógico: **elegir un marco activa automáticamente los perfiles correctos y oculta los incompatibles.**

---

## 5. Scripts de referencia

### Script 1 — Creación de opciones

Crea opciones visibles + internas y carga valores por Clase.

### Script 2 — Disparadas

Vincula valores visibles con valores internos para activar compatibilidades.

Cada serie podrá reproducir este patrón sin cambios estructurales.
