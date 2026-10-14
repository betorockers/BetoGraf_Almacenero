# 📋 Guía de Ingreso de Precios — BetoGraf Almacenero POS
### Módulo: Estructura de Precios (Contabilidad)
**Versión del sistema:** v2.3.9.6 · **Fecha:** Septiembre 2026
**Elaborado por:** BetoGraf_Inc SpA — Servicios Tecnológicos Toledos SpA

---

## ¿Para qué sirve este módulo?

Cuando usted crea o edita un producto, el sistema incluye una sección llamada **"Estructura de Precios (Contabilidad)"**. Este módulo realiza todos los cálculos tributarios y de rentabilidad de forma **automática**, evitando errores de digitación y garantizando que su negocio siempre venda con ganancia.

---

## Los campos del formulario

| Campo | Color | ¿Qué es? |
|---|---|---|
| **Costo Neto ($)** | Azul | Lo que usted pagó al proveedor, **sin IVA** |
| **Costo Bruto ($)** | Azul | Lo que usted pagó al proveedor, **con IVA incluido** |
| **Margen (%)** | Ambar | Porcentaje de ganancia sobre el costo. **Mínimo recomendado: 30%** |
| **ILA/IABA (%)** | Rojo | Impuesto adicional para alcohol, tabaco u otros (si aplica) |
| **Venta Neta ($)** | Verde | Precio de venta **sin IVA** (base para la boleta SII) |
| **Venta Bruta (Público) ($)** | Verde brillante | **El precio que el cliente ve y paga en caja** |
| **Aplica IVA (19%)** | Checkbox | Actívelo si el producto está afecto a IVA |

---

## ¿Cómo ingresar un producto? — 3 métodos

### MÉTODO 1: Tengo la factura del proveedor (RECOMENDADO)

Este es el método más exacto para su contabilidad.

**Ejemplo:** Compré una caja de conservas a $1.000 neto (sin IVA).

**Paso a paso:**
1. Active "Aplica IVA (19%)" si corresponde.
2. Ingrese en **Costo Neto**: `1000`
3. El sistema calculará automáticamente:
   - Costo Bruto = $1.190 (1.000 × 1.19)
   - Venta Neta = $1.300 (1.000 × 1.30, con margen 30%)
   - Venta Bruta = **$1.547** (precio para el cliente)

> El margen quedará exactamente en **30%**.

---

### MÉTODO 2: Solo sé el precio que quiero cobrar al cliente

Use este método cuando ya tiene definido cuánto quiere vender el producto (precio de mercado o competencia).

**Ejemplo:** Quiero vender una bebida a **$1.190** (precio que ve el cliente).

**Paso a paso:**
1. Active "Aplica IVA (19%)".
2. Deje en blanco el Costo Neto.
3. Ingrese directamente en **Venta Bruta (Público)**: `1190`
4. El sistema calculará automáticamente:
   - Venta Neta = $1.000 (1.190 ÷ 1.19)
   - Costo Neto estimado = $769 (1.000 ÷ 1.30 con margen mínimo 30%)
   - Costo Bruto estimado = $915
   - Margen = **30%** (mínimo garantizado)

> **ATENCIÓN — Aviso Amarillo:** El sistema mostrará un aviso que dice **"Costo estimado"**. Esto significa que el costo fue calculado automáticamente asumiendo un margen mínimo del 30%. Si usted conoce el costo real del proveedor, ingréselo en el campo "Costo Neto" para obtener el margen definitivo real.

---

### MÉTODO 3: Ajustar el margen libremente

Use este método si ya tiene costo y quiere cambiar la ganancia.

**Ejemplo:** El costo neto es $800 y quiero ganar un 45%.

**Paso a paso:**
1. Ingrese en **Costo Neto**: `800`
2. Cambie el **Margen (%)**: `45`
3. El sistema calculará:
   - Venta Neta = $1.160 (800 × 1.45)
   - Venta Bruta = **$1.380** (precio público)

---

## ¿Qué significa el aviso amarillo "Costo estimado"?

Cuando usted ingresa solo el precio de venta y el sistema no tiene el costo real, aparece este aviso:

    AVISO: Costo estimado por margen mínimo 30% —
    Ingrese el costo real del proveedor para
    obtener el margen definitivo.

Este aviso **no impide guardar el producto**. Significa:

- El precio al cliente está correcto.
- El sistema garantiza que usted gana **al menos un 30%**.
- El costo ingresado es una **estimación**, no el costo real.
- Cuando llegue la factura del proveedor, edite el producto y corrija el Costo Neto.

Para cerrar el aviso haga clic en la "X" que aparece a la derecha del mensaje.

---

## La regla de oro del IVA

| Si el producto... | ¿Aplica IVA? | Ejemplo |
|---|---|---|
| Se vende con boleta normal | Sí (19%) | Abarrotes, bebidas, limpieza |
| Es de primera necesidad exento | No | Algunos alimentos según SII |
| Lleva impuesto adicional (alcohol, tabaco) | IVA + ILA/IABA | Vinos, cervezas, cigarrillos |

> Consulte con su contador para saber qué productos de su rubro están exentos o afectos a impuestos adicionales.

---

## Ejemplo completo — Supermercado / Almacén

| Producto | Costo Neto | Margen | Venta Neta | Venta Bruta (cliente) |
|---|---|---|---|---|
| Arroz 1 kg | $500 | 30% | $650 | $773 |
| Aceite 1 lt | $1.200 | 35% | $1.620 | $1.928 |
| Cerveza | $600 | 40% | $840 | $1.000 (+ ILA 15%) |
| Solo precio conocido: $2.990 | estimado: $1.726 | 30% | $2.513 | $2.990 |

---

## Resumen del flujo de cálculo

**Si conoce el costo (método recomendado):**

    Costo Neto  -->  x margen%  -->  Venta Neta  -->  x 1.19 (IVA)  -->  Venta Bruta
    Costo Neto  -->  x 1.19 (IVA)  -->  Costo Bruto

**Si solo conoce el precio al cliente (cálculo inverso):**

    Venta Bruta  -->  ÷ 1.19 (IVA)  -->  Venta Neta
    Venta Neta   -->  ÷ 1.30 (30% margen mínimo)  -->  Costo Neto estimado (*)
    Costo Neto   -->  x 1.19 (IVA)  -->  Costo Bruto estimado (*)

    (*) Estimado: reemplácelo con el costo real de la factura del proveedor.

---

## Preguntas frecuentes

**¿Puedo guardar un producto sin el costo?**
Sí. El sistema estimará el costo asumiendo 30% de margen. Recuerde actualizarlo cuando tenga la factura del proveedor.

**¿Qué pasa si ingreso el costo y el precio de venta no alcanza el 30%?**
El sistema mostrará el margen real aunque sea menor al 30%. Es su decisión si acepta vender con ese margen.

**¿El sistema cambia los precios automáticamente en las boletas ya emitidas?**
No. Los precios en boletas históricas son inmutables. Solo afecta las ventas futuras.

**¿Dónde veo la Venta Bruta en caja?**
El precio que se muestra en la pantalla de ventas (POS) y el que aparece en la boleta siempre es la **Venta Bruta (Público)** — el precio con todos los impuestos incluidos.

**¿Puedo modificar el margen después?**
Sí. Edite el producto en cualquier momento desde el Panel de Administración > Productos.

---

*Este documento forma parte del Manual de Usuario del sistema BetoGraf Almacenero POS.*
*Para asistencia técnica: contactar a BetoGraf_Inc SpA — Servicios Tecnológicos Toledos SpA.*
*(c) 2026 BetoGraf_Inc SpA. Todos los derechos reservados.*
