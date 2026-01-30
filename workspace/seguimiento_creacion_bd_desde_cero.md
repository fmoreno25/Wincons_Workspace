# 📘 Seguimiento — Creación de BD desde cero (Excel → App)

Documento de **estado validado** del proceso de creación de una Base de Datos **desde cero**, mediante inserción completa **Excel → App** sobre **BD vacía**.

La BD **ya ha sido creada y utilizada con éxito**, confirmando que el enfoque es correcto y estable.  
Durante esta validación se observan únicamente los puntos descritos a continuación.

---

## ✅ Estado general

- BD creada desde cero (BD vacía).
- Inserción completa Excel → App ejecutada.
- Flujo operativo y estable.
- Incidencias técnicas localizadas y no bloqueantes.

---

## 🔧 Ajustes e incidencias detectadas

### 1. Divisas
- ✔️ Definidas en Excel.
- ✔️ Importadas correctamente.
- ➜ Cerrado.

---

### 2. Colores — RGB
- ✔️ Columna RGB añadida en Excel.
- ✔️ Inserción correcta en BD.
- ✔️ Usado por PrefCad en dibujos según acabado.

---

### 3. Materia Prima — RGB (INCIDENCIA)
- ❌ La Materia Prima hereda el RGB del último color insertado.

**Causa**
- El RGB se toma desde la fila de color.

**Corrección necesaria**
- Añadir **columna RGB propia para Materia Prima**.
- Separar:
  - RGB del color.
  - RGB de la Materia Prima.

---

### 4. Colores — Campos ambientales (INCIDENCIA)
- ❌ No se insertan correctamente:
  - `AmbientRed`
  - `AmbientGreen`
  - `AmbientBlue`
  - (y campos asociados)

**Corrección necesaria**
- Mapear e insertar explícitamente los valores por defecto correctos.

---

## 📌 Fases del proceso

| Fase | Estado |
| ---- | ------ |
| Fase 0 | ✅ |
| Fase 1 | ✅ |
| Fase 2 | ✅ |
| Fase 3 | ✅ |
| Fase 4 | ✅ |
| Fase 5 | ✅ |
| Fase 6 | 🟡 Reglas |
| Fase 7 | 🟡 Escandallos |

---

## 🧩 Pendientes finales

1. **Materia Prima**
   - RGB propio, sin herencia de colores.

2. **Colores**
   - Inserción correcta de campos ambientales.

3. **Fase 6 — Reglas**
4. **Fase 7 — Escandallos**

---

## 🏁 Conclusión

Una vez resueltos:
- RGB independiente en Materia Prima.
- Campos ambientales correctamente insertados en Colores.

La **app quedará totalmente operativa**,  
**sin necesidad de ajustes en PrefWise**,  
quedando pendientes únicamente las fases finales de **Reglas y Escandallos**.
