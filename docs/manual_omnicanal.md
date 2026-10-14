# 🌐 Guía de Conexión: Ventas Online y Redes Sociales (Omnicanal)

¡Bienvenido! Esta guía te ayudará a conectar tu tienda virtual (**Shopify** o **WooCommerce**) y tus chats de redes sociales (**WhatsApp** o **Instagram**) con tu punto de venta **BetoGraf POS**.

Hemos dividido esta guía en dos partes:
1. **Guía Rápida para el Dueño del Negocio:** Pasos sencillos, visuales y sin tecnicismos.
2. **Guía Avanzada para Soporte Técnico:** Detalles de código y base de datos para tu programador o asistente técnico.

---

# 🛒 PARTE 1: Guía para el Dueño de Tienda (Sin conocimientos técnicos)

Para recibir tus pedidos online en tu pantalla de BetoGraf POS, solo debes realizar dos sencillos pasos: **obtener el enlace de conexión en tu sistema** y **pegarlo en tu plataforma de ventas**.

## 📌 Paso 1: Obtener tu Enlace de Conexión en BetoGraf
1. Abre la aplicación de **BetoGraf POS** en tu computador.
2. Ingresa al panel de **Administración / Configuración**.
3. Busca la pestaña **Configuración de Nube/Omnicanal**.
4. Verás un campo de texto llamado **"Enlace Webhook de Ingesta"**.
5. Haz clic en el botón **"Copiar Enlace"**. (El enlace se guardará en tu portapapeles y se verá similar a `https://tu-proyecto.supabase.co/functions/...`).

---

## 📌 Paso 2: Conectar tu Plataforma de Ventas

### Opción A: Si usas WooCommerce (Tu sitio web WordPress)
1. Entra al panel administrador de tu página web de WordPress.
2. En el menú de la izquierda, ve a **WooCommerce** y luego presiona **Ajustes**.
3. Arriba a la derecha, haz clic en la pestaña **Avanzado** y luego en las letras azules que dicen **Webhooks**.
4. Haz clic en el botón **Añadir Webhook** y escribe lo siguiente:
   * **Nombre:** `BetoGraf POS`
   * **Estado:** Cambia a **Activo**.
   * **Tema:** Selecciona **Pedido creado**.
   * **URL de entrega:** Pega aquí el enlace que copiaste en el **Paso 1**.
   * **Versión de la API:** Selecciona la que dice **v3** (es la recomendada).
5. Haz clic en el botón azul **Guardar Webhook** al final de la página. ¡Listo!

### Opción B: Si usas Shopify
1. Entra al panel de administración de tu tienda Shopify.
2. Abajo a la izquierda, haz clic en **Configuración** (icono de engranaje).
3. En la lista, ve a **Notificaciones** y desplázate hasta el final de la pantalla donde dice **Webhooks**.
4. Haz clic en **Crear Webhook** y selecciona:
   * **Evento:** Selecciona **Creación de pedido** (o `order/create`).
   * **Formato:** Selecciona **JSON**.
   * **URL:** Pega aquí el enlace que copiaste en el **Paso 1**.
5. Haz clic en **Guardar**. ¡Listo!

---

## 💬 Conectar WhatsApp o Instagram
Para recibir pedidos automáticos desde chats de clientes:
* **Si usas un Bot de WhatsApp o Instagram:** Pídele a la persona que te configuró el bot que configure el envío de las ventas al enlace copiado en el **Paso 1**.
* El bot enviará los datos del cliente, el teléfono y los productos directamente a tu pantalla de ventas de BetoGraf POS.

> [!WARNING]
> **Regla de Oro:** Para que los pedidos se carguen correctamente, los **Códigos de Barras** (o **SKU**) que tienes puestos en tus productos de Shopify o WooCommerce **deben ser idénticos** a los registrados dentro de tu sistema BetoGraf POS.

---

## ⚡ ¿Cómo ver y cobrar los pedidos online en caja?
Una vez conectados:
1. Cuando entre un pedido por internet, verás una notificación en la pantalla de **Ventas** del POS.
2. En el panel lateral derecho verás un apartado llamado **"Pedidos Online"**.
3. Haz **doble clic** sobre el pedido pendiente para cargarlo al carrito de compras.
4. El cajero podrá modificar el pedido (si el cliente lo pide) o presionar directamente **"Cobrar/Imprimir Boleta"** para entregar el recibo de venta y rebajar el inventario automáticamente.

---

# 💻 PARTE 2: Guía de Configuración Técnica (Para Soporte Técnico o Desarrolladores)

Si eres el encargado de soporte, programador o estás integrando un bot conversacional a medida, esta sección describe el flujo API, el modelo de datos y el formato esperado.

## ⚙️ Flujo API de Ingesta
BetoGraf POS utiliza un backend en la nube basado en **Supabase** que expone un endpoint HTTP (`orders-intake`). La app local realiza un polling ordenado (`sync_from_cloud`) y un acuse de recibo (`ack_online_orders`) para marcar las órdenes como procesadas:

```
[Canal WooCommerce/Shopify/Wsp]
               │
               ▼ (POST Webhook JSON)
  [Supabase: orders-intake]
               │
               ▼ (Guarda en tabla 'pedidos_online')
     [BetoGraf POS Local]
               │
               ▼ (Deduplica vía 'webhook_ref' y procesa)
    (PATCH ack_online_orders a Supabase con estado 'importado')
```

## 📋 Estructura de Payload Aceptada
El endpoint de ingesta procesa y normaliza payloads del integrador conversacional o e-commerce. La estructura de datos estándar que debes enviar en el cuerpo de la petición (body JSON) es la siguiente:

```json
{
  "origen": "whatsapp",
  "webhook_ref": "identificador_unico_de_orden_o_mensaje",
  "customer_name": "Nombre de Cliente",
  "customer_phone": "+56912345678",
  "customer_address": "Av. Principal 123, Depto 40",
  "message_text": "Texto opcional enviado por el usuario",
  "items": [
    {
      "codigo_barras": "7801234567890",
      "cantidad": 2,
      "precio_unitario": 1200
    }
  ],
  "total": 2400,
  "notes": "Notas adicionales del despacho o preparación"
}
```

### Mapeo de Parámetros Clave
* `webhook_ref`: Cadena de texto única utilizada por el POS para prevenir la ingesta de pedidos duplicados.
* `origen` / `channel`: Valores aceptados: `whatsapp`, `instagram`, `shopify`, `woocommerce`, `web`.
* `items`: Array de ítems. El POS busca la coincidencia del producto primero por `codigo_barras` (o `sku`). Si no se encuentra, realiza una búsqueda secundaria por el nombre exacto de producto en la base de datos local SQLite.
* **Fusión de Borradores (WhatsApp/Instagram):** Si un cliente envía mensajes sucesivos en el mismo chat, el sistema BetoGraf POS no creará pedidos nuevos. En su lugar, concatenará las notas en el pedido borrador existente (`"Hola, quiero pan || Agrega también leche"`) basándose en `conversation_ref`.
