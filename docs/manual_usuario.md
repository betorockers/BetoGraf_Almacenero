# 📖 Manual de Usuario Oficial — BetoGraf Almacenero POS

**Versión Oficial:** v2.3.9.10 rev.1.0 PRO  
**Arquitectura:** Cloud-Hybrid (Operación 100% Offline-First con sincronización en la Nube)  
**Desarrollado por:** BetoGraf Inc. (Omar Toledo)

---

## 1. ⚡ Introducción y Filosofía del Sistema

Bienvenido a **BetoGraf Almacenero POS**, la solución de punto de venta y gestión de inventario para el comercio minorista chileno.

- **Offline-First:** Tu caja nunca se detiene. Aunque se caiga internet, puedes seguir vendiendo, emitiendo boletas e ingresando clientes con total normalidad.
- **Cifrado de Grado Militar:** Toda la información local reside protegida en %APPDATA%\betograf_almacenero\almacen.db con cifrado AES-256 (SQLCipher).
- **Diseño Ergonómico Dark Mode:** Interfaz optimizada para reducir la fatiga visual en jornadas de trabajo continuas.

---

## 2. 📦 Instalación y Puesta en Marcha

1. **Descarga del Instalador:** Descarga BetoGraf_Almacen_Setup_v2.3.9.10.exe.
2. **Asistente Automatizado:** Ejecuta el instalador. Detectará automáticamente tu arquitectura Windows (10 u 11 de 64 bits) y configurará los accesos directos necesarios.
3. **Arranque Inmediato:** El launcher iniciará el motor del servidor local y abrirá la aplicación en modo ventana limpia (sin marcos de navegador que distraigan al operador).

---

## 3. 🔑 Activación de Licencias

- **Modo Trial (Demostración 20 días):** Al iniciar sin serial, dispones de 20 días con todas las funciones de venta, caja, stock y boleta electrónica activas.
- **Activación Inmediata con Serial:** Desde el menú lateral (*Planes / Activación*), ingresa tu serial de 16 caracteres (ej. POS-MS-XXXX-XXXX-XXXX). El sistema valida con la base de datos central en Supabase y activa tu licencia permanente en 2 segundos.
- **Compra en la App:** Puedes adquirir tu suscripción directamente pagando con tarjeta o WebPay vía Mercado Pago; el sistema se auto-activa solo al completarse el pago.

---

## 4. 🖥️ Operación en el Punto de Venta (Ventas y Cobro)

- **Búsqueda Instantánea:** Ingresa el código de barras con lector óptico o escribe las primeras letras del nombre del producto.
- **Venta por Fracción (Balanza / Granel):** Para productos pesables (kg, lt, mt), se abre el modal de pesaje exacto con cálculo de precio proporcional automático.
- **Botones de Acceso Rápido:** Configura los productos de mayor rotación (pan, verduras, bebidas, promociones) para agregarlos al carrito en 1 toque.
- **Medios de Pago Soportados:**
  * **Efectivo:** Cálculo automático de vuelto y aplicación de la **Ley de Redondeo (Ley 20.956)**.
  * **Tarjetas Débito / Crédito:** Integración con SmartPOS Mercado Pago Point, SumUp y Flow.
  * **Transferencia Bancaria:** Registro ordenado del comprobante.
  * **Fiado / Crédito Almacén:** Asignación directa a la ficha del cliente con límite de crédito y control de deuda histórica.

---

## 5. 🛡️ Panel Administrativo e Inventario

- **Gestión de Productos:** Creación, edición, stock mínimo, precio costo, IVA (19%), margen y precio de venta bruto sugerido.
- **Soft Delete con Integridad Referencial:** Los productos con ventas históricas no se eliminan físicamente; se archivan para mantener la cuadratura contable y los reportes tributarios sin roturas.
- **Exportación Contable a Excel:** Genera planillas Excel nativas (.xlsx) desglosadas en 9 columnas cuadradas para enviar directamente a tu contador.
- **Cuentas por Pagar:** Control de facturas de proveedores, vencimientos y amortizaciones en cuotas.

---

## 6. 🌐 Omnicanalidad y Sincronización en la Nube

- **Integración con Tiendas Web:** Compatible con WooCommerce, Shopify y catálogos en línea mediante Webhooks y Cloud Sync.
- **Meta Omnichannel (WhatsApp e Instagram):** Recibe pedidos y mensajes de compra directamente en la pantalla de pedidos del POS.
- **Descuento de Stock Centralizado:** Cada venta presencial o por internet descuenta del mismo inventario en tiempo real.

---

## 7. ⚙️ Hardware e Impresión Térmica Oficial SII

- **Estándar Oficial:** Boleta de Lujo de alta definición a 203 DPI (renderizado Pillow) con recuadro oficial SII, Código de Barras 1D (Code128) y Timbre Electrónico fiscal.
- **Selector Flexible de Rollo:**
  * **80 mm (Ticket de Lujo SII):** Tamaño comercial estándar con desglose amplio y espacioso.
  * **58 mm (Estándar Almacén):** Compatible con impresoras térmicas compactas.
- **Detección Automática:** Compatible con Xprinter (XP-80, XP-58, XP-A160H), Epson TM-T, Bixolon, Pos-D y genéricos ESC/POS.

---

## 8. 🔄 Actualizaciones Continuas Over-The-Air (OTA)

- Cuando exista una nueva actualización oficial o parche de seguridad, aparecerá una notificación en el panel superior.
- Al hacer clic en **Actualizar**, el sistema descarga el parche, cierra los procesos, aplica las mejoras y se reinicia en menos de 10 segundos preservando todos tus datos intactos.

---

## 9. 🔒 Seguridad y Guardián de Ventana Anti-Cierre

- **Protección contra Cierre Accidental:** La combinación Alt + F4 está neutralizada; minimiza la ventana a la barra de tareas para no perder carritos de compra ni interrumpir turnos.
- **Única Instancia (Mutex Global):** Si haces doble clic accidental al acceso directo, el sistema no abre dos programas duplicados; simplemente enfoca la ventana activa.

---

## 10. 📞 Soporte Técnico y Contacto

- **Portal Web:** [https://betograf.cl](https://betograf.cl)
- **WhatsApp Oficial:** [+56 9 3344 5244](https://wa.me/56933445244)
- **Correo Electrónico:** [contacto@betograf.cl](mailto:contacto@betograf.cl)
