# 🛡️ BetoGraf Almacenero POS — Versión 2.0.6

<div align="center">
  <img src="./banner.png" alt="BetoGraf Almacenero" width="100%" style="border-radius: 8px; box-shadow: 0 4px 20px rgba(0,0,0,0.15);" />

  <br />
  
  ### **El Punto de Venta (POS) Profesional, Blindado y Offline-First para Comercios Exigentes**
  
  *Una solución local de alto rendimiento diseñada bajo estándares de ingeniería de software para maximizar la velocidad de cobro, resguardar tus datos y mantener tu negocio siempre activo.*

  <p>
    <a href="https://github.com/betorockers/BetoGraf_Almacenero/releases/tag/v2.0.6">
      <img src="https://img.shields.io/badge/Versi%C3%B3n-2.0.6_Estable-c69214?style=for-the-badge&logo=github" alt="Versión 2.0.6" />
    </a>
    <img src="https://img.shields.io/badge/Tecnolog%C3%ADa-Django_&_Waitress-1f8b4c?style=for-the-badge&logo=django" alt="Django Stack" />
    <img src="https://img.shields.io/badge/Cifrado-SQLCipher_3-4f46e5?style=for-the-badge&logo=sqlite" alt="SQLCipher 3" />
    <img src="https://img.shields.io/badge/Soporte-Windows_&_Linux-0078D6?style=for-the-badge&logo=windows" alt="Multiplataforma" />
  </p>

  <p>
    <b>¿Cansado de los sistemas lentos basados en la nube?</b><br />
    BetoGraf Almacenero opera directamente en tu equipo físico. Tus datos se quedan en tu máquina, cifrados bajo estándares de grado militar, y el sistema responde de forma instantánea sin requerir conexión a internet.
  </p>
</div>

---

## ⚡ Descarga Rápida de Instaladores Oficiales (v2.0.6)

A continuación, selecciona tu plataforma para descargar el instalador oficial optimizado:

<div align="center">
  <table style="width: 90%; border-collapse: collapse; border: 1px solid #e2e8f0;">
    <thead>
      <tr style="background-color: #f8fafc;">
        <th align="center" style="padding: 12px; border: 1px solid #e2e8f0; width: 50%;">🪟 Versión para Windows</th>
        <th align="center" style="padding: 12px; border: 1px solid #e2e8f0; width: 50%;">🐧 Versión para Linux</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td align="center" style="padding: 20px; border: 1px solid #e2e8f0; vertical-align: top;">
          <a href="https://github.com/betorockers/BetoGraf_Almacenero/releases/download/v2.0.6/BetoGraf_Almacen_Setup_v2.0.6.exe">
            <img src="https://img.shields.io/badge/Descargar_para-Windows_(.exe)-0078D6?style=for-the-badge&logo=windows&logoColor=white" alt="Descargar para Windows" />
          </a>
          <br /><br />
          <b>BetoGraf_Almacen_Setup_v2.0.6.exe</b><br />
          <small style="color: #64748b;">Instalador autogestionado para Windows 10 y 11 (64-bits)</small><br />
          <span style="display: inline-block; margin-top: 8px; padding: 2px 8px; background-color: #f1f5f9; color: #475569; font-size: 11px; border-radius: 4px; font-family: monospace;">Tamaño: ~47.6 MB</span>
        </td>
        <td align="center" style="padding: 20px; border: 1px solid #e2e8f0; vertical-align: top;">
          <a href="https://github.com/betorockers/BetoGraf_Almacenero/releases/download/v2.0.6/betograf-almacenero_2.0.6_amd64.deb">
            <img src="https://img.shields.io/badge/Descargar_para-Linux_(.deb)-1e293b?style=for-the-badge&logo=linux&logoColor=FCB900" alt="Descargar para Linux" />
          </a>
          <br /><br />
          <b>betograf-almacenero_2.0.6_amd64.deb</b><br />
          <small style="color: #64748b;">Paquete nativo para Debian, Ubuntu, Linux Mint y derivados</small><br />
          <span style="display: inline-block; margin-top: 8px; padding: 2px 8px; background-color: #f1f5f9; color: #475569; font-size: 11px; border-radius: 4px; font-family: monospace;">Tamaño: ~50.4 MB</span>
        </td>
      </tr>
    </tbody>
  </table>
</div>

---

## 💼 Matriz de Licenciamiento y Módulos

BetoGraf Almacenero cuenta con un esquema de licenciamiento escalable según tus necesidades operativas:

| Módulo Operativo | 🧪 Demo | ⏳ Trial (20 Días) | 💎 Comercial (Full) |
| :--- | :---: | :---: | :---: |
| **Punto de Venta (Caja y Ventas)** | Limitado (5 productos) | ✅ Completo | ✅ Ilimitado |
| **Control de Turnos y Efectivo** | ✅ Básico | ✅ Completo | ✅ Completo |
| **Gestión de Inventario FIFO** | ❌ Inactivo | ✅ Completo | ✅ Completo |
| **Reportes Financieros Avanzados** | ❌ Inactivo | ✅ Completo | ✅ Completo |
| **Omnicanalidad (WhatsApp/IG)** | ❌ Inactivo | ✅ Completo | ✅ Completo |
| **Sincronización Cloud (Respaldos)** | ❌ Inactivo | ✅ Opcional | ✅ Integrado |
| **Soporte Prioritario y OTA Updates** | ❌ Inactivo | ❌ Inactivo | ✅ Permanente |

---

## 🛠️ Especificaciones Técnicas (Ficha de Ingeniería)

El núcleo del sistema ha sido rediseñado en la versión **2.0.6** para asegurar una estabilidad del 99.9% frente a cortes eléctricos o de red:

*   **Arquitectura de Backend**: Django 5.x integrado con **Waitress WSGI**, garantizando una API local robusta, de alta concurrencia y sin fugas de memoria.
*   **Seguridad de Datos**: Base de datos SQLite cifrada nativamente con **SQLCipher 3** (cifrado AES-256). Tus ventas, costos y clientes están blindados ante accesos físicos no autorizados.
*   **Carga 100% Offline (Local-First)**: Toda la interfaz gráfica, plantillas e interactividad (Tailwind CSS, Alpine.js y HTMX) se encuentran integrados localmente en los assets. **Funciona a la perfección sin conexión a internet**.
*   **Interfaz de Usuario Vanguardista**: Renderizado directo mediante el motor de Google Chrome en modo `--app` (interfaz nativa fullscreen, eliminando elementos del navegador para simular una app de escritorio nativa).
*   **Gestión de Inventario FIFO**: Trazabilidad contable en tiempo real bajo la regla First-In, First-Out (lo primero que entra, es lo primero que se vende), calculando de forma exacta la utilidad neta de tu negocio.

---

## 🚀 Guías de Instalación Paso a Paso

### 🪟 Instalación en Windows (10 / 11)

1. Descarga el archivo de instalación [BetoGraf_Almacen_Setup_v2.0.6.exe](https://github.com/betorockers/BetoGraf_Almacenero/releases/download/v2.0.6/BetoGraf_Almacen_Setup_v2.0.6.exe).
2. Haz doble clic sobre el ejecutable descargado.
3. Sigue las instrucciones del asistente en pantalla (se encargará de crear los accesos directos en el escritorio y configurar el Firewall).
4. Abre **BetoGraf Almacen** desde tu escritorio.

> [!TIP]
> Si Windows Defender te muestra una advertencia de SmartScreen (debido a que es un ejecutable nuevo compilado a medida), haz clic en **"Más información"** y luego en **"Ejecutar de todas formas"**. El instalador incluye un certificado local seguro.

---

### 🐧 Instalación en Linux (Ubuntu, Mint, Debian y derivados)

1. Descarga el archivo [betograf-almacenero_2.0.6_amd64.deb](https://github.com/betorockers/BetoGraf_Almacenero/releases/download/v2.0.6/betograf-almacenero_2.0.6_amd64.deb).
2. Abre una terminal en la carpeta donde descargaste el archivo y ejecuta:
   ```bash
   sudo dpkg -i betograf-almacenero_2.0.6_amd64.deb
   ```
3. Si el instalador te solicita dependencias no instaladas, arréglalo automáticamente con:
   ```bash
   sudo apt-get install -f
   ```
4. Lanza el POS desde tu menú de aplicaciones buscando **BetoGraf Almacenero** o escribiendo `betograf-almacenero` en la terminal.

---

## ❓ Preguntas Frecuentes (FAQ)

#### ¿Mis datos se suben a algún servidor?
No de forma obligatoria. Toda la información de tus productos, ventas y cuadratura de caja se guarda localmente en tu equipo. Si cuentas con el módulo comercial activo, puedes habilitar respaldos en la nube en tiempo real.

#### ¿Cómo adquiero una clave de licencia comercial?
Puedes solicitar una licencia o agendar una demostración comercial personalizada a través de nuestros canales directos.

#### ¿El sistema es compatible con lectores de código de barras?
Sí, es compatible con cualquier lector de código de barras USB o inalámbrico que funcione en modo emulación de teclado (la gran mayoría del mercado).

---

## 📞 Soporte y Canales Directos

<div align="center">
  <table style="width: 80%; border-collapse: collapse;">
    <tr style="background-color: #f8fafc;">
      <td align="center" style="padding: 15px; border: 1px solid #e2e8f0; width: 50%;">
        🌐 <b>Sitio Web Oficial</b><br />
        <a href="https://betograf.cl">betograf.cl</a>
      </td>
      <td align="center" style="padding: 15px; border: 1px solid #e2e8f0; width: 50%;">
        💬 <b>Contacto por WhatsApp</b><br />
        <a href="https://wa.me/56933445244">+56 9 3344 5244</a>
      </td>
    </tr>
  </table>

  <br />
  <sub>BetoGraf Almacenero POS es un producto de BetoGraf. Todos los derechos reservados.</sub>
</div>
