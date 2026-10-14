# 📊 Manual de Contabilidad Avanzada, Asistente F29 y RCV SII
### BetoGraf Almacenero POS — Módulo Financiero y Tributario

---

## 🎯 Objetivo del Módulo

El **Módulo de Contabilidad Avanzada** de BetoGraf POS fue creado para que el dueño de almacén, minimarket o botillería tenga **control total sobre sus finanzas e impuestos sin depender exclusivamente de un contador** ni llevar cuadernos manuales.

Con este módulo podrás:
1. Conocer exactamente cuánto debes pagar de IVA a fin de mes (Formulario 29).
2. Importar tu **Registro de Compras y Ventas (RCV)** descargado del SII para cruzar facturas de proveedores.
3. Generar el **Balance Tributario de 8 Columnas en Excel** listo para presentar en bancos al solicitar créditos comerciales.
4. Monitorear tus ventas netas, costos reales y utilidad neta en tiempo real.

---

## 🚀 1. Asistente F29 Automático: ¿Cómo Funciona?

El Asistente F29 analiza automáticamente todas las boletas y facturas emitidas en tu punto de venta durante el mes y las cruza con las facturas de compra ingresadas.

### Datos que calcula automáticamente:
* **IVA Débito Fiscal:** El IVA del 19% cobrado a tus clientes por todas las ventas del mes.
* **IVA Crédito Fiscal:** El IVA del 19% contenido en las facturas de mercadería que compraste a tus proveedores.
* **Remanente de IVA:** Si compraste más mercadería de la que vendiste, el saldo a tu favor se guarda automáticamente para descontarlo el próximo mes.
* **Retención de Honorarios:** Desglose del porcentaje de retención correspondiente a boletas de honorarios recibidas.
* **Impuesto Determinado a Pagar:** Monto final a declarar en el formulario F29 del SII.

> 💡 **Consejo Comercial:** Revisa tu Asistente F29 el día 1 de cada mes. Así sabrás con días de anticipación el monto exacto de tu IVA y podrás planificar tu flujo de caja sin sorpresas.

---

## 📥 2. Carga del RCV del SII en 1 Clic

Para que el sistema conozca todas las compras que hiciste con factura (a proveedores como CCU, Coca-Cola, Soprole, Colun, etc.), puedes importar directamente el archivo del SII:

1. Ingresa a la página oficial del **SII (sii.cl)** con tu Clave Tributaria.
2. Ve a la sección **Servicios Online > Factura Electrónica > Registro de Compras y Ventas (RCV)**.
3. Selecciona el mes correspondiente, pestaña **Compras**, y presiona el botón **Descargar Detalle (CSV)**.
4. En BetoGraf Almacenero, entra a **Administración > Contabilidad > Cargar RCV**.
5. Selecciona el archivo descargado y presiona **Procesar RCV**.
6. El sistema registrará automáticamente todas las facturas de tus proveedores, alimentando tu IVA Crédito Fiscal al instante.

---

## 📑 3. Balance Tributario de 8 Columnas (IFRS / ProPyme 14 D3 y D8)

El **Balance de 8 Columnas** es el documento financiero oficial que exigen los bancos para evaluar préstamos comerciales, leasing o líneas de crédito:

* **Columnas 1 y 2 (Sumas):** Débitos y Créditos acumulados.
* **Columnas 3 y 4 (Saldos):** Saldo Deudor y Saldo Acreedor.
* **Columnas 5 y 6 (Inventario):** Activo y Pasivo.
* **Columnas 7 y 8 (Resultados):** Pérdidas y Ganancias del ejercicio.

### ¿Cómo exportarlo a Excel?
1. Dirígete a **Administración > Contabilidad > Balance 8 Columnas**.
2. Selecciona el año o periodo comercial.
3. Presiona el botón verde **Exportar a Excel**.
4. Se generará una planilla profesional con formato bancario, fórmulas validadas y sellado de integridad.

---

## 🔒 4. Seguridad y Sellado de Integridad

Cada registro del Libro Diario y Libro Mayor cuenta con un **sello criptográfico de integridad HMAC-SHA256**. Esto garantiza que:
* Ningún registro contable pueda ser adulterado o borrado accidentalmente.
* La información presentada ante el SII o ante auditorías externas sea 100% fidedigna y trazable.

---

## ❓ Preguntas Frecuentes

**¿Necesito tener internet para usar el Asistente F29?**  
No. Todas las boletas emitidas y facturas cargadas se procesan de forma local en tu equipo. Solo requieres internet para descargar el archivo CSV desde el sitio web del SII.

**¿Qué pasa si tengo boletas exentas de IVA?**  
El sistema las clasifica automáticamente bajo el código de ventas exentas (DTE 41), manteniéndolas separadas del IVA débito fiscal.

**¿Puedo entregarle este balance a mi contador?**  
¡Sí! El archivo Excel exportado cuenta con la estructura estándar exigida por los colegios de contadores y el SII, lo que le facilitará el trabajo a tu contador y te permitirá negociar una tarifa más económica por sus servicios.
