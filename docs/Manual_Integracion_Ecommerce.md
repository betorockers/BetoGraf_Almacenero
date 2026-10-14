# Manual de Integración Webhooks: E-Commerce y Redes Sociales

Este documento explica cómo configurar sus tiendas online (WooCommerce / Shopify) y redes sociales para que envíen las órdenes de venta y los mensajes directamente a BetoGraf POS.

---

## 1. Requisitos Previos

1. BetoGraf POS (Versión 2.3.9.10 rev.1.0 o superior) instalado y en funcionamiento.
2. Contar con un túnel inverso o IP Pública estática para que la red externa (Shopify/WooCommerce/Instagram) pueda comunicarse con el POS. 
   > Si no cuenta con IP pública, recomendamos utilizar servicios como **Ngrok** o **Cloudflare Tunnels** apuntando al puerto local `8000` (o el puerto configurado en el POS).
3. Obtener la **URL Base Pública** de su instancia (Ej: `https://midominio.ngrok-free.app` o `http://190.x.x.x:8000`).

---

## 2. Integración con WooCommerce (WordPress)

BetoGraf POS puede recibir notificaciones cuando se crea una nueva orden en su sitio WooCommerce.

1. Ingrese al administrador de WordPress (`/wp-admin`).
2. Diríjase a **WooCommerce > Ajustes > Avanzado > Webhooks**.
3. Haga clic en **Añadir Webhook**.
4. Configure los siguientes campos:
   - **Nombre:** `BetoGraf POS - Orden Creada`
   - **Estado:** Activo
   - **Tema (Topic):** Pedido creado (`order.created`)
   - **URL de entrega:** `[SU_URL_BASE]/pos/webhooks/woocommerce/`
   - **Secreto:** Déjelo en blanco (opcional) o configure una llave si desea firmar el payload (requiere configuración avanzada en BetoGraf).
   - **Versión de API:** Integración v3
5. Haga clic en **Guardar Webhook**.
6. Realice un pedido de prueba en WooCommerce para verificar que aparece automáticamente en el módulo "Pedidos" de BetoGraf POS.

---

## 3. Integración con Shopify

Configure Shopify para que envíe un Webhook a BetoGraf POS al momento de generarse una venta.

1. Ingrese a su panel de administración de Shopify.
2. Vaya a **Configuración** (esquina inferior izquierda) y seleccione **Notificaciones**.
3. Baje hasta la sección **Webhooks** y haga clic en **Crear Webhook**.
4. Configure con los siguientes valores:
   - **Evento:** Creación de pedido (`Order creation`)
   - **Formato:** JSON
   - **URL:** `[SU_URL_BASE]/pos/webhooks/shopify/`
   - **Versión de API del Webhook:** (Seleccione la más reciente recomendada por Shopify)
5. Haga clic en **Guardar**.
6. Para probar, puede hacer clic en "Enviar notificación de prueba". La orden de prueba debería aparecer en BetoGraf POS en el módulo "Pedidos".

---

## 4. Integración con Redes Sociales (Omnicanal)

BetoGraf POS incluye un módulo de "Inbox Omnicanal" para recibir y contestar mensajes, y transformarlos en órdenes de venta.

### 4.1. Facebook Messenger e Instagram Direct (Meta)
1. Acceda a la consola de [Meta for Developers](https://developers.facebook.com/).
2. Cree o seleccione una aplicación de tipo "Negocios" vinculada a su página de Facebook y cuenta de Instagram profesional.
3. Configure el producto **Messenger** o **Webhooks**.
4. En URL de Devolución de Llamada (Callback URL), ingrese: `[SU_URL_BASE]/pos/webhooks/rrss/`
5. En Token de Verificación (Verify Token), ingrese el token de seguridad provisto por el equipo de soporte de BetoGraf (por defecto: `betograf_rrss_secure_token`).
6. Suscríbase a los campos `messages` y `messaging_postbacks`.
7. Guarde y realice pruebas enviando un mensaje directo a su página/perfil. Debería aparecer en el módulo **Omnicanal** del POS.

### 4.2. WhatsApp (API Cloud de Meta)
1. Dentro de su aplicación en Meta for Developers, añada el producto **WhatsApp**.
2. Vaya a la sección de **Configuración > Webhooks**.
3. Ingrese la misma Callback URL: `[SU_URL_BASE]/pos/webhooks/rrss/`
4. Use el mismo Token de Verificación.
5. Suscríbase al campo `messages`.
6. Envíe un mensaje de WhatsApp al número configurado para verificar la conexión.

---

## 5. Solución de Problemas

- **El pedido no aparece en BetoGraf:** Verifique que el servicio de túnel (ej. ngrok) esté activo. Revise que la ruta ingresada termine en `/` (ej. `/pos/webhooks/shopify/`).
- **Precios incorrectos:** Shopify y WooCommerce suelen enviar los totales en formato decimal. BetoGraf POS asimila automáticamente los valores y los formatea a moneda nacional. Si observa descuadres con impuestos o despachos, contacte a soporte técnico para revisar el mapeo del payload JSON.
- **Dudas Adicionales:** Abra el panel `Soporte Técnico` dentro de BetoGraf POS y póngase en contacto con nuestro equipo.
