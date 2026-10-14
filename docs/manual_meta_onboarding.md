# 📘 Manual de Onboarding: Meta Omnichannel (WhatsApp Business & Instagram)
**BetoGraf Almacenero POS — Versión 2.3.9.10 rev.1.0**

Este manual técnico y operativo detalla los pasos requeridos para vincular **BetoGraf POS** con la suite de comercio conversacional de Meta (**WhatsApp Business Cloud API**, **Instagram Messaging API** y **Meta Commerce Manager**).

---

## 🎯 1. Prerrequisitos en Meta

Antes de comenzar la integración técnica, el comercio debe contar con los siguientes activos aprobados en la plataforma de Meta:

1. **Meta Business Manager verificado:**
   - Accede a [business.facebook.com](https://business.facebook.com) con una cuenta empresarial.
   - Completa la verificación de la empresa con los documentos legales (RUT empresa, constitución o boleta de servicio).
2. **Página de Facebook & Perfil de Instagram Business:**
   - La cuenta de Instagram debe ser de tipo **Profesional / Empresa** y estar conectada a la Fanpage de Facebook del negocio.
3. **Cuenta de WhatsApp Business (WABA):**
   - Un número de teléfono dedicado que **no esté registrado** en la app móvil convencional de WhatsApp o WhatsApp Business personal.
   - Nombre para mostrar (*Display Name*) aprobado por Meta.
4. **Túnel HTTPS / Dominio Público:**
   - Meta requiere que la URL de callback del Webhook opere sobre **HTTPS** con un certificado TLS válido. Si el POS corre localmente, se debe emplear **Cloudflare Tunnels**, **Ngrok** o un dominio propio apuntando al puerto local.

---

## 🔑 2. Creación de System User y Token Permanente

Para evitar que los tokens de acceso caduquen cada 60 días, es indispensable generar un **System User Access Token**:

1. Ve a **Meta Business Manager → Configuración del negocio → Usuarios → Usuarios del sistema**.
2. Haz clic en **Agregar** y crea un usuario (ej: `BetoGraf-POS-Bot`) con rol de *Empleado*.
3. En **Activos asignados**, otórgale acceso con control total a:
   - Tu cuenta de WhatsApp Business (WABA).
   - Tu Catálogo de Productos.
   - Tu Página de Facebook e Instagram.
4. Haz clic en **Generar nuevo token**:
   - Selecciona tu aplicación de Meta Developers.
   - Vigencia del token: **Nunca caduca** (*Never expires*).
   - Marca obligatoriamente los siguientes permisos:
     - `whatsapp_business_messaging`
     - `whatsapp_business_management`
     - `catalog_management`
     - `instagram_basic`
     - `instagram_manage_messages`
     - `pages_manage_metadata`
5. Copia el token resultante y guárdalo en **BetoGraf POS → Configuración → Redes y Web → Meta Omnichannel → System User Access Token**.

---

## 🛍️ 3. Catálogo de Productos en Meta Commerce Manager

Para que los clientes puedan ver los productos y enviar carritos por WhatsApp e Instagram:

1. Ingresa a [commerce.facebook.com](https://commerce.facebook.com) y selecciona tu negocio.
2. Dirígete a **Catálogos → Crear catálogo** (Tipo: *Comercio electrónico / Productos*).
3. Vincula el catálogo a tu WhatsApp Business Account y a tu tienda de Instagram.
4. Copia el **Catalog ID** numérico e ingrésalo en **BetoGraf POS** en el campo `Meta Catalog ID`.
5. **Carga de Productos:**
   - **Opción A (Feed Programado RSS):** En *Orígenes de datos del catálogo*, añade un *Feed de datos* con programación diaria y coloca la URL proporcionada por BetoGraf POS:  
     `https://tu-dominio.cl/webhooks/meta/catalog/feed.xml`
   - **Opción B (Sincronización Inmediata):** En el panel de configuración de BetoGraf POS, haz clic en el botón **"Sincronizar Catálogo Ahora"** para subir los productos vía Graph API `items_batch`.

---

## ⚡ 4. Configuración del Webhook en Meta Developers

1. Ve a [developers.facebook.com](https://developers.facebook.com) y abre tu aplicación.
2. Agrega el producto **Webhooks**:
   - Selecciona **WhatsApp Business Account** (y/o **Instagram**).
   - **URL de devolución de llamada (Callback URL):**  
     `https://tu-dominio.cl/webhooks/meta/`
   - **Token de verificación:**  
     Ingresa una clave segura inventada por ti (ej: `betograf_token_seguro_2026`) y asegúrate de colocar exactamente la misma en el campo `Verify Token` de BetoGraf POS.
   - Haz clic en **Verificar y Guardar**.
3. **Suscripción de Campos:**
   - En WhatsApp: suscríbete al campo `messages`.
   - En Instagram: suscríbete al campo `messages`.
4. **App Secret:**
   - En tu app de Meta, ve a **Configuración básica → Secreto de la aplicación** (*App Secret*), haz clic en mostrar y copia el valor.
   - Pégalo en BetoGraf POS en `App Secret` para activar la validación criptográfica **HMAC SHA-256** (`X-Hub-Signature-256`).

---

## 💳 5. Flujo de Pedidos y Cobro en el POS

Una vez completada la configuración:

1. **Navegación del Cliente:** El cliente abre tu WhatsApp o Instagram, entra al catálogo y arma un carrito con sus productos.
2. **Envío de Orden:** Al enviar el pedido por chat, Meta dispara un webhook firmado a BetoGraf POS.
3. **Validación Atómica:** El POS valida el stock local, reserva las unidades y genera un `Pedido` en el módulo de caja.
4. **Cobro Automatizado:** El POS genera dinámicamente un link de pago con **Mercado Pago** o **Flow** y lo envía de inmediato al chat del cliente con un botón de pago interactivo.
5. **Cierre de Venta:** Cuando el cliente paga en su teléfono, la pasarela notifica al POS, la orden se marca como pagada y el stock se descuenta en el Kardex local.

---

*Desarrollado con arquitectura industrial para BetoGraf Almacenero POS.*
