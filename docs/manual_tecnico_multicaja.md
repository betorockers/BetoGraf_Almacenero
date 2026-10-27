# 📡 Manual Técnico: Configuración de Roles y Topología de Red Multi-Caja (LAN)
**BetoGraf Almacenero POS — Versión Enterprise Multi-Caja (v2.3.9.14)**  
**Audiencia:** Técnicos de Campo Certificados BetoGraf & Administradores de Infraestructura TI  
**Plan de Licencia Requerido:** `PRO_PERSONALIZADO` (Multi-Caja Enterprise)  
**Fecha de Publicación:** Octubre 2026  

---

## 1. 🌐 Introducción y Filosofía Arquitectónica

El sistema **BetoGraf Almacenero POS Enterprise** implementa una arquitectura **Local-First & LAN-Resilient** diseñada para permitir que locales comerciales de alto flujo operen con múltiples puestos de cobro y atención simultáneos (Cajas Rápidas, Puntos de Pasillo, Balcones de Atención) compartiendo inventario, clientes y turnos en tiempo real sobre la red de área local (LAN), manteniendo al 100% la soberanía offline sin depender de Internet.

```
                    ┌──────────────────────────────────────────────┐
                    │       ROUTER LAN / SWITCH GIGABIT            │
                    │         Subred: 192.168.1.0/24               │
                    └───────┬──────────────────────────────┬───────┘
                            │                              │
         IP: 192.168.1.100:8000 (Fija)            IP: 192.168.1.105:8000 (DHCP)
    ┌───────────────────────┴──────────────┐     ┌─────────┴────────────────────┐
    │       CAJA 01: SERVIDOR MAESTRO      │     │    CAJA 02: SATÉLITE (LAN)   │
    │  - Base de Datos Central (SQLCipher) │◄────┤ - Punto de Venta Remoto      │
    │  - Motor Django Core & API LAN       │     │ - Impresión Térmica Local USB│
    │  - Impresión Térmica Local USB/80mm  │     │ - Sincronización Directa/Cola│
    └──────────────────────────────────────┘     └──────────────────────────────┘
```

---

## 2. 🖥️ Definición de Roles de Nodo (Topología)

En la pestaña **Multi-Caja** del módulo de Configuración (`/pos/settings/`), el software permite seleccionar uno de los siguientes tres roles operacionales:

### A. Caja Única (`standalone`) — Por Defecto
* **Descripción:** El equipo opera de forma completamente aislada.
* **Base de Datos:** Almacena y procesa sus datos en el archivo local cifrado `%APPDATA%\betograf_almacenero\almacen.db`.
* **Uso Recomendado:** Comercios con un único computador o en locales sin red cableada.

### B. Caja Principal / Servidor Maestro (`master`)
* **Descripción:** Este equipo actúa como la **Caja 01** y simultáneamente como el **Servidor Central de la Tienda**.
* **Responsabilidades:**
  1. Aloja la base de datos maestra cifrada con SQLCipher.
  2. Atiende las transacciones locales de su propio cajero.
  3. Abre el socket HTTP/REST en el puerto `8000` de la IP de red local para responder solicitudes de inventario, ventas y clientes desde los puestos satélites.
* **Requisito Obligatorio:** Debe configurarse con una **IP Privada Estática** (ej: `192.168.1.100`).

### C. Caja Satélite / Terminal Esclava (`satellite`)
* **Descripción:** Puesto secundario de atención (`CAJA_02`, `CAJA_03`, etc.) que no mantiene una base de datos de productos principal.
* **Responsabilidades:**
  1. Conectarse a través de la red local a la IP del Servidor Maestro (`http://<IP_MAESTRO>:8000/`).
  2. Consultar catálogo de productos y precios en tiempo real.
  3. Emitir y registrar las ventas debitando el stock centralizado.
  4. Gestionar su propia impresora térmica local y su propio cajón de dinero.

---

## 3. ⚙️ Modos de Sincronización para Cajas Satélites

El técnico instalador puede calibrar el modo de sincronización según la calidad y estabilidad de la red del local:

### 🔹 Alternativa A: Modo Directo (`direct`) — Recomendado para Red Cableada (UTP)
* **Comportamiento:** Cada lectura de código de barras y cada confirmación de pago se procesa síncronamente contra la API del Servidor Maestro.
* **Ventajas:** Máxima coherencia de stock en tiempo real. Si un producto se agota en Caja 01, la Caja 02 lo sabe en menos de 50 milisegundos.
* **Comportamiento ante Caída:** Si se corta el cable de red o cae el switch, la satélite alerta al operador inmediatamente impidiendo ventas duplicadas o desincronizadas.

### 🔹 Alternativa B: Modo Cola Local Resiliente (`queue`) — Recomendado para Wi-Fi
* **Comportamiento:** La satélite mantiene una copia local ligera en caché del catálogo de productos y una cola SQLite local de transacciones pendientes (`cola_ventas_satelite`).
* **Ventajas:** Si la señal Wi-Fi sufre micro-cortes temporales de 1 a 3 minutos, el cajero puede seguir cobrando sin interrupción visual.
* **Sincronización Atómica:** Apenas el worker en segundo plano detecta que el Servidor Maestro vuelve a responder ping, vacía la cola en orden cronológico mediante transacciones atómicas.

---

## 4. 🛠️ Protocolo de Instalación y Puesta en Marcha (Paso a Paso)

### Fase 1: Calibración de la Red Local en Windows
1. Conectar todos los equipos al mismo router o switch (preferir cable Ethernet Cat 5e/Cat 6).
2. En el equipo que será **Caja Principal (Maestro)**:
   - Presionar `Win + R`, escribir `cmd` y ejecutar `ipconfig`.
   - Identificar la IPv4 de la tarjeta de red (ejemplo: `192.168.1.100`).
   - Ir a *Configuración de Red de Windows > Cambiar opciones del adaptador > Propiedades de Ethernet > Protocolo de Internet versión 4 (TCP/IPv4)* y fijar la IP estática:
     * **Dirección IP:** `192.168.1.100`
     * **Máscara de subred:** `255.255.255.0`
     * **Puerta de enlace predeterminada:** `192.168.1.1`
     * **DNS:** `1.1.1.1` / `8.8.8.8`
3. **Regla de Firewall de Windows en Caja Principal:**
   - Abrir PowerShell como Administrador en el Maestro y ejecutar:
   ```powershell
   New-NetFirewallRule -DisplayName "BetoGraf POS Multi-Caja (Port 8000)" -Direction Inbound -LocalPort 8000 -Protocol TCP -Action Allow
   ```
   - Asegurarse de que el perfil de red de Windows esté configurado como **Red Privada** (no Pública).

---

### Fase 2: Configuración del Servidor Maestro en el Sistema
1. En la **Caja Principal**, abrir BetoGraf POS e iniciar sesión con credenciales de Administrador.
2. Ingresar a **Configuración** (`/pos/settings/`) y hacer clic en el tab **Red Multi-Caja**.
3. Seleccionar la tarjeta **Caja Principal (Servidor Maestro)**.
4. En los parámetros de red:
   - **Identificador de Terminal:** Escribir `CAJA_01_MASTER`.
   - **Puerto:** Dejar `8000`.
5. Hacer clic en **[ Guardar Configuración Multi-Caja ]**.
6. El sistema confirmará con un toast verde: *"Configuración Multi-Caja guardada exitosamente"*.

---

### Fase 3: Configuración de la Terminal Satélite
1. En el segundo computador (**Caja 02**), abrir BetoGraf POS e ingresar a **Configuración > Red Multi-Caja**.
2. Seleccionar la tarjeta **Caja Satélite (Esclava)**.
3. Completar los parámetros:
   - **Identificador de Terminal:** Escribir `CAJA_02_SATELLITE`.
   - **IP Servidor Maestro:** Escribir la IP fija del Maestro (ej: `192.168.1.100`).
   - **Puerto del Servicio POS:** `8000`.
   - **Modo de Sincronización:** Elegir `Directo` (si está cableada) o `Cola Local Resiliente` (si está por Wi-Fi).
4. Hacer clic en el botón **[ Probar Conexión ]** (Ping).
   - El sistema ejecutará una prueba inmediata vía socket TCP hacia `192.168.1.100:8000`.
   - Si la red está correcta, aparecerá el badge verde:  
     `🟢 Conexión exitosa con el Servidor Maestro (Latencia: 4ms)`.
5. Hacer clic en **[ Guardar Configuración Multi-Caja ]**.
6. Reiniciar la aplicación en la Caja Satélite para aplicar los enlaces remotos.

---

## 5. 🖨️ Impresión Térmica en Puestos Satélites

Cada caja satélite gestiona su hardware de forma **física y local**:
1. Conectar la impresora térmica USB (ej: Xprinter XP-80 / 58mm) directamente a un puerto USB de la caja satélite.
2. En Windows de la caja satélite, instalar el driver oficial del fabricante y nombrar la cola de impresión (ej: `XP-80`).
3. En BetoGraf POS de la satélite, ingresar a **Configuración > Hardware**:
   - Seleccionar ancho de rollo (`80 mm` o `58 mm`).
   - Presionar **[ Probar Rollo Activo ]** para verificar que el ticket físico salga cortado y nítido.
4. *Resultado:* Cuando un cajero vende en la Caja 02, el stock se descuenta en la base de datos de la Caja 01 (Maestro) y la boleta física se imprime en la impresora de la Caja 02.

---

## 6. 🚨 Diagnóstico y Resolución de Problemas (Troubleshooting)

### Síntoma 1: El botón "Probar Conexión" arroja `🔴 Host Inalcanzable`
* **Causa A:** El Firewall de Windows en la Caja Principal está bloqueando el puerto 8000.  
  * *Solución:* Revisar la regla de entrada de firewall en el Maestro o verificar que el perfil de red esté en *Privada*.
* **Causa B:** La IP del Maestro cambió por DHCP.  
  * *Solución:* Fijar la IP en la tarjeta de red del Maestro o crear una reserva DHCP estática en el router por dirección MAC.
* **Causa C:** Los equipos están en subredes distintas (ej: Maestro en `192.168.1.X` y Satélite en red de invitados `192.168.2.X`).  
  * *Solución:* Conectar ambos equipos a la misma red y verificar con comando `ping 192.168.1.100` desde la satélite.

### Síntoma 2: Lentitud al escanear productos en la Satélite (>1 segundo)
* **Causa:** Enlace Wi-Fi inestable o con alta pérdida de paquetes.
* **Solución:**
  1. Cambiar la satélite al **Modo Cola Local Resiliente (Con caché)** en `/pos/settings/`.
  2. Migrar la conexión a cable Ethernet o conectar a la banda Wi-Fi 5 GHz del router.

### Síntoma 3: Aparece aviso de licencia no compatible al guardar Multi-Caja
* **Causa:** El serial activo en el equipo corresponde a un plan Monogiro (`PRO_MENSUAL` o `PRO_ANUAL`).
* **Solución:** La arquitectura Multi-Caja es exclusiva del plan **`PRO_PERSONALIZADO`**. Se debe ingresar un serial con capacidad Multi-Caja y Omnicanal desde el modal de activación de licencia.

---

## 7. 📋 Hoja de Validación de Instalación en Terreno (Checklist Técnico)

Antes de entregar el local comercial al cliente, el técnico debe marcar:

- [ ] IP Estática asignada y verificada en el Servidor Maestro.
- [ ] Regla de Firewall TCP puerto 8000 activa en el Servidor Maestro.
- [ ] Prueba de Ping exitosa desde todas las Cajas Satélites (`/pos/settings/`).
- [ ] Venta de prueba emitida en Caja 02 con descuento efectivo de stock en Caja 01.
- [ ] Impresión física de boleta de prueba en la impresora térmica de cada caja.
- [ ] Apertura automática del cajón de dinero (gaveta) en cada terminal.
- [ ] Verificación de reporte de cierre de turno independiente por cajero.

---
*Manual técnico oficial generado bajo estándar Omni-Agente Ultra-Pro para la suite comercial BetoGraf.*
