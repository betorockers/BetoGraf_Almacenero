# BetoGraf Almacenero POS — Versión Oficial 2.3.9.10 rev.1.0

<div align="center">
  <img src="./banner.png" alt="BetoGraf Almacenero" width="100%" style="border-radius: 8px; box-shadow: 0 4px 20px rgba(0,0,0,0.15);" />

  <br />
  
  ### **El Punto de Venta (POS) Profesional, Blindado y Offline-First para Comercios Exigentes**
  
  *Una solución local de alto rendimiento diseñada bajo estándares de ingeniería de software para maximizar la velocidad de cobro, resguardar tus datos y mantener tu negocio siempre activo.*

  <p>
    <a href="https://github.com/betorockers/BetoGraf_Almacenero/releases/tag/v2.3.9.10">
      <img src="https://img.shields.io/badge/Versi%C3%B3n-2.3.9.10_rev.1.0_Oficial-c69214?style=for-the-badge&logo=github" alt="Versión 2.3.9.10 rev.1.0" />
    </a>
    <a href="./CERTIFICACION_Y_CALIDAD.md">
      <img src="https://img.shields.io/badge/Certificaci%C3%B3n-Calidad_y_Seguridad_100%25-22c55e?style=for-the-badge&logo=securityscorecard&logoColor=white" alt="Certificación de Calidad y Seguridad" />
    </a>
    <img src="https://img.shields.io/badge/Tecnolog%C3%ADa-Django_%26_Waitress-1f8b4c?style=for-the-badge&logo=django" alt="Django Stack" />
    <img src="https://img.shields.io/badge/Cifrado-SQLCipher_AES--256-4f46e5?style=for-the-badge&logo=sqlite" alt="SQLCipher AES-256" />
    <a href="./COMPARATIVA_RENDIMIENTO.md">
      <img src="https://img.shields.io/badge/Instalador-47.5_MB_Ultra--Ligero-0284c7?style=for-the-badge&logo=speedtest&logoColor=white" alt="Instalador 47.5 MB" />
    </a>
  </p>

  <p>
    <b>¿Cansado de los sistemas lentos basados en la nube que se caen cuando más los necesitas?</b><br />
    BetoGraf Almacenero opera directamente en tu computador local. Tus datos se quedan en tu máquina, protegidos bajo cifrado de grado militar (AES-256), con contraseñas seguras según norma internacional NIST SP 800-63B, y una velocidad de respuesta instantánea sin requerir conexión permanente a internet.
  </p>

  <p>
    👉 <b><a href="./CERTIFICACION_Y_CALIDAD.md">Lee aquí el Dictamen de Certificación Comercial, Rendimiento y Seguridad v2.3.9.10</a></b><br />
    ⚡ <b><a href="./COMPARATIVA_RENDIMIENTO.md">¿Por qué BetoGraf pesa ~47.5 MB mientras otros sistemas pesan más de 1 GB? Lee la comparativa técnica aquí</a></b>
  </p>
</div>

---

## 🚀 Descarga Rápida de Instaladores Oficiales (v2.3.9.10)

Selecciona la opción de instalación según tu caso:

<div align="center">
  <table style="width: 100%; border-collapse: collapse; border: 1px solid #e2e8f0;">
    <thead>
      <tr style="background-color: #f8fafc;">
        <th align="center" style="padding: 12px; border: 1px solid #e2e8f0; width: 50%;">📦 Instalador Completo Oficial (Equipos Nuevos)</th>
        <th align="center" style="padding: 12px; border: 1px solid #e2e8f0; width: 50%;">⚡ Parche Ligero Acumulativo (Clientes Existentes)</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td align="center" style="padding: 20px; border: 1px solid #e2e8f0; vertical-align: top;">
          <a href="https://github.com/betorockers/BetoGraf_Almacenero/releases/download/v2.3.9.10/BetoGraf_Almacen_Setup_v2.3.9.10.exe">
            <img src="https://img.shields.io/badge/Descargar-Instalador_Completo_(.exe)-0078D6?style=for-the-badge&logo=windows&logoColor=white" alt="Descargar Instalador Completo" />
          </a>
          <br /><br />
          <b>BetoGraf_Almacen_Setup_v2.3.9.10.exe</b><br />
          <small style="color: #64748b;">Instalador oficial para Windows 10 y 11 (64-bits). Configura base de datos cifrada, accesos directos y servicios base.</small><br />
          <span style="display: inline-block; margin-top: 8px; padding: 2px 8px; background-color: #f1f5f9; color: #475569; font-size: 11px; border-radius: 4px; font-family: monospace;">Tamaño: ~48 MB (Ultra-Optimizado)</span>
        </td>
        <td align="center" style="padding: 20px; border: 1px solid #e2e8f0; vertical-align: top;">
          <a href="https://github.com/betorockers/BetoGraf_Almacenero/releases/download/v2.3.9.10/BetoGraf_Almacen_Parche_v2.3.9.10.exe">
            <img src="https://img.shields.io/badge/Descargar-Parche_Ligero_(.exe)-10b981?style=for-the-badge&logo=windows&logoColor=white" alt="Descargar Parche" />
          </a>
          <br /><br />
          <b>BetoGraf_Almacen_Parche_v2.3.9.10.exe</b><br />
          <small style="color: #64748b;">Actualización express para comercios con versión anterior instalada. Conserva datos, inventario y licencias intactos.</small><br />
          <span style="display: inline-block; margin-top: 8px; padding: 2px 8px; background-color: #ecfdf5; color: #047857; font-size: 11px; border-radius: 4px; font-family: monospace;">Actualización Segura In-Place</span>
        </td>
      </tr>
    </tbody>
  </table>
</div>

---

## 💎 Matriz de Características por Tipo de Licencia

El sistema adapta sus capacidades dinámicamente según la serie de licencia activada:

| Módulo / Capacidad | PRO Mensual (`POS-MS-...`) | PRO Anual (`POS-AN-...`) | PRO Omnicanal (`POS-OM-...`) | Master DEV (`POS-DEV-...`) |
|---|:---:|:---:|:---:|:---:|
| **Terminales permitidas** | 1 Puesto | 1 Puesto | 1 Puesto | Ilimitado |
| **Venta POS Offline-first rápida (<25ms)** | ✅ Habilitado | ✅ Habilitado | ✅ Habilitado | ✅ Habilitado |
| **Facturación SII (Boleta/Factura + PDF417)** | ✅ Habilitado | ✅ Habilitado | ✅ Habilitado | ✅ Habilitado |
| **Control de Stock y Cierre de Caja ciego** | ✅ Habilitado | ✅ Habilitado | ✅ Habilitado | ✅ Habilitado |
| **Transbank POS USB y Mercado Pago Point** | ✅ Habilitado | ✅ Habilitado | ✅ Habilitado | ✅ Habilitado |
| **Gestión de Proveedores básica** | ✅ Habilitado | ✅ Habilitado | ✅ Habilitado | ✅ Habilitado |
| **Órdenes de Compra por Stock Crítico** | 🔒 Bloqueado | ✅ Habilitado | ✅ Habilitado | ✅ Habilitado |
| **Reportes de Márgenes y Ganancia Real** | 🔒 Bloqueado | ✅ Habilitado | ✅ Habilitado | ✅ Habilitado |
| **Suite Omnicanal (WhatsApp Cloud + Instagram)** | 🔒 Bloqueado | 🔒 Bloqueado | ✅ Habilitado | ✅ Habilitado |
| **Integración E-commerce (Shopify/WooCommerce)** | 🔒 Bloqueado | 🔒 Bloqueado | ✅ Habilitado | ✅ Habilitado |
| **Módulo "Cuentas por Pagar" Proveedores** | 🔒 Bloqueado | 🔒 Bloqueado | ✅ Habilitado (Exclusivo) | ✅ Habilitado |
| **Catálogo XML Meta & Links de Pago Auto** | 🔒 Bloqueado | 🔒 Bloqueado | ✅ Habilitado | ✅ Habilitado |
| **Soporte de Ingeniería y Telemetría** | Estándar | Prioritario (6/año) | VIP Continuo | Total / Ilimitado |

> ℹ️ *Todos los planes incluyen un periodo de prueba de 20 días con acceso de evaluación completo a las funciones operativas del sistema.*

---

## 🌟 Módulos Comerciales e Innovaciones Destacadas

### 1. ⚡ Punto de Venta Ultra-Rápido & 100% Offline-First
* **Velocidad sin esperas:** Cobros y escaneo de productos en menos de **25 milisegundos**, evitando filas en horas punta.
* **Autonomía total:** Opera de manera ininterrumpida frente a caídas de internet, cortes de fibra o fallas en servidores en la nube.
* **Múltiples métodos de pago:** Efectivo con cálculo de vuelto y Ley de Redondeo CLP, tarjetas bancarias Transbank POS por puerto COM/USB, Mercado Pago Point, transferencias y libreta de fiados.

### 2. 🧾 Facturación Electrónica SII & Timbre Digital PDF417
* **Cumplimiento Tributario Nativo:** Emisión de Boletas Electrónicas (DTE 39/41) y Facturas con cálculo automático de Débito Fiscal IVA 19% e impuestos adicionales (ILA).
* **Timbre Electrónico Oficial:** Generación en alta resolución del código de barras bidimensional PDF417 según resolución técnica del SII, impreso de forma nítida en vouchers de 58 mm y 80 mm.
* **Gestión de Folios CAF:** Consumo atómico de folios timbrados con alerta de bajo remanente para timbraje oportuno.

### 3. 💳 Módulo Financiero: Cuentas por Pagar (Exclusivo PRO Omnicanal)
* **Control Integral de Deuda con Proveedores:** Libro auxiliar de facturas a crédito recibidas (CCU, Soprole, Coca-Cola, etc.).
* **Semáforo Financiero de Vencimientos:** Monitoreo visual preventivo de facturas: *Al día* (verde), *Por vencer* (amarillo, dentro de los próximos 3 días) y *Vencida* (rojo).
* **Gestión Atómica de Abonos:** Registro de pagos parciales o totales con recálculo automático de saldo remanente, historial detallado de transacciones y KPIs de deuda consolidada.

### 4. 🌐 Suite Meta Omnichannel & Comercio Conversacional
* **WhatsApp Business Cloud API & Instagram Messaging:** Recepción centralizada de pedidos desde chats, consulta de stock por bot/operador y confirmación de compras.
* **Catálogo XML Sincronizado:** Feed RSS 2.0 XML generado al vuelo y sincronizado con Meta Commerce Manager para tiendas de Instagram y WhatsApp Shop.
* **Links de Pago Automatizados:** Generación automática de botones de pago con **Mercado Pago** y **Flow** enviados al cliente en el chat para cobro inmediato.

### 5. 🛒 Webhooks E-Commerce (Shopify & WooCommerce)
* **Sincronización Bidireccional:** Conexión con tiendas virtuales vía webhooks firmados con HMAC-SHA256.
* **Descuento Atómico de Stock:** Al concretarse una venta en la tienda online, el stock físico en la tienda se descuenta de inmediato evitando sobreventa.
* **API de Consulta de Catálogo:** Consulta de precios y niveles de inventario por SKU mediante API Key configurable.

### 6. 📊 Contabilidad Analítica & Motor de Precios Bidireccional
* **Utilidad y Margen Real:** Reportes detallados que calculan la ganancia neta ítem por ítem comparando precio de venta vs. costo de reposición.
* **Estructura de Precios Bidireccional:** Al fijar el precio bruto público, el sistema retrocede matemáticamente para inferir costo neto estimado y margen de ganancia garantizado, con decimales precisos.
* **Libro de Ventas Excel:** Exportación en un clic adaptada a las especificaciones contables y tributarias de Chile.

### 7. 🛰️ Telemetría y Salud en Nube (Supabase Cloud)
* **Worker Autónomo en Background:** Monitoreo periódico de salud del sistema (uso de memoria RAM, disco SSD, base de datos SQLite cifrada y uptime).
* **Sincronización Silenciosa:** Transmisión de métricas hacia Supabase con tolerancia a desconexión, asegurando supervisión preventiva sin impacto en el rendimiento de la caja.

---

## ⚡ Rendimiento & Arquitectura: ¿Por qué BetoGraf pesa ~48 MB mientras otros superan 1 GB?

| Parámetro Operativo | Software POS Convencional<br>*(Basado en Electron / Navegadores Duplicados)* | BetoGraf Almacenero POS<br>*(Arquitectura C-Hardened Local-First)* | Ventaja Competitiva BetoGraf |
| :--- | :---: | :---: | :---: |
| **Tamaño del Instalador** | `500 MB — 1.2 GB` | **`~48 MB`** | **95% más liviano** (descarga en segundos) |
| **Espacio Requerido en Disco** | `1.5 GB — 3.0 GB` | **`~120 MB`** | Ideal para terminales compactos y discos SSD |
| **Consumo de Memoria RAM** | `800 MB — 1.8 GB` | **`~150 MB`** *(Servidor + UI)* | **Ahorro del 80% de recursos** |
| **Tiempo de Arranque (Cold Boot)** | `6 a 15 segundos` | **`1.2 a 2.0 segundos`** | Listo para atender inmediatamente al encender el equipo |
| **Latencia de Escaneo de Productos** | `180 ms — 450 ms` (o lag por internet) | **`< 25 milisegundos`** | Cobro instantáneo sin demoras |
| **Motor de Base de Datos** | Servidor cliente-servidor externo pesado | **SQLCipher C-Nativo** (AES-256 embebido) | Cero servicios parásitos en segundo plano |
| **Seguridad de Archivos** | Archivos abiertos y legibles | **Binario C Blindado (Cython)** | Respaldo y máxima privacidad comercial |

---

## 💻 Guía de Instalación Rápida

### Instalación en Windows 10 y 11 (64-bits)

1. Descarga el instalador oficial [BetoGraf_Almacen_Setup_v2.3.9.10.exe](https://github.com/betorockers/BetoGraf_Almacenero/releases/download/v2.3.9.10/BetoGraf_Almacen_Setup_v2.3.9.10.exe) o el parche ligero si ya tienes una versión previa instalada.
2. Ejecuta el archivo descargado.
3. Sigue el asistente guiado de instalación; se crearán automáticamente los accesos directos en el escritorio y menú de inicio.
4. Inicia **BetoGraf Almacen** desde tu escritorio y comienza a operar.

> [!TIP]
> Si Windows SmartScreen muestra una pantalla preventiva por ser un software recién empaquetado, presiona **"Más información"** y luego **"Ejecutar de todas formas"**. El ejecutable cuenta con verificación de integridad nativa.

---

## 📞 Soporte Comercial y Asesoría Directa

<div align="center">
  <table style="width: 80%; border-collapse: collapse;">
    <tr style="background-color: #f8fafc;">
      <td align="center" style="padding: 15px; border: 1px solid #e2e8f0; width: 50%;">
        🌐 <b>Sitio Web Oficial</b><br />
        <a href="https://betograf.cl">betograf.cl</a>
      </td>
      <td align="center" style="padding: 15px; border: 1px solid #e2e8f0; width: 50%;">
        💬 <b>Atención Directa por WhatsApp</b><br />
        <a href="https://wa.me/56933445244">+56 9 3344 5244</a>
      </td>
    </tr>
  </table>

  <br />
  <sub>BetoGraf Almacenero POS es un desarrollo de BetoGraf. Todos los derechos reservados.</sub>
</div>
