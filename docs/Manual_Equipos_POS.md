# Manual de Configuración de Terminales POS y Pasarelas de Pago

Este documento explica cómo configurar sus equipos físicos de venta (Transbank, MercadoPago Point, SumUp) y pasarelas de pago (Flow) dentro del sistema BetoGraf POS.

---

## 1. MercadoPago Point

Para conectar su terminal físico (Point Smart, Point Pro 2, Point Plus) y enviar los cobros automáticamente desde el sistema, siga estos pasos:

1. Ingrese a la web de **MercadoPago Developers** y vaya a **Tus Aplicaciones**.
2. Cree una nueva aplicación o seleccione una existente.
3. Vaya a **Credenciales de Producción** y copie el **Access Token** (`APP_USR-...`).
4. En BetoGraf POS, ingrese a **Panel Admin > Configuración > Pagos**.
5. Active MercadoPago y pegue el **Access Token** en el campo correspondiente.
6. Haga clic en **"Escanear"**. El sistema buscará todos los dispositivos Point asociados a su cuenta.
7. Se listarán los IDs de los terminales (ej. `GERI12345`). Cópielo y péguelo en la casilla **ID Terminal Point (Device ID)**.
8. Haga clic en **Guardar Configuración**.
9. Puede usar el botón **"Probar Conexión de Terminal"** para asegurarse de que el equipo reacciona y se conecta correctamente.

---

## 2. SumUp

BetoGraf POS permite enviar cobros a los dispositivos SumUp (Air, Solo, 3G).

1. Ingrese a su cuenta en [SumUp Developers](https://developer.sumup.com/).
2. Cree credenciales **OAuth (Client Credentials)** para obtener su Token.
3. Copie el **Access Token** generado.
4. Necesitará su **Merchant Code** (se encuentra en su perfil de SumUp).
5. En BetoGraf POS, diríjase a **Configuración > Pagos**, seleccione SumUp y complete los datos solicitados (Token, Merchant Code).
6. **MAC Terminal:** En algunos equipos SumUp es necesario ingresar la dirección MAC Bluetooth o de Red. Puede encontrarla en los ajustes del propio equipo.
7. Guarde los cambios y realice una prueba de conexión.

---

## 3. Transbank

La integración de Transbank en BetoGraf POS (para terminales POS integrados clásicos) funciona a través del puerto Serial (COM) o de red (WebPOS/REST).

- Para terminales locales por USB/Bluetooth, nuestro instalador incluye los drivers genéricos de Transbank POS.
- Diríjase a **Configuración > Hardware** en la aplicación y seleccione **Puerto COM** en el cual está conectado el equipo de Transbank.
- Para integración vía Webpay REST (cobros remotos), complete el **Commerce Code** (Código de Comercio) y **API Key** (secreta) otorgada por Transbank en el apartado de **Pagos**.

---

## 4. Flow (Pasarela de Pagos / Códigos QR)

Flow.cl permite recibir pagos a través de códigos QR o links de pago.

1. Ingrese a su cuenta en [Flow.cl](https://www.flow.cl).
2. Diríjase a **Configuración > Mis Datos > Integración API**.
3. Copie su **API Key** y su **Secret Key**.
4. Vaya a **Panel Admin > Configuración > Pagos** en BetoGraf POS.
5. Seleccione la opción Flow, y pegue ambas credenciales en sus respectivas casillas.
6. Haga clic en **Guardar Configuración**.
7. Ahora podrá seleccionar "Flow" como método de pago en la caja. El sistema generará una solicitud de cobro automáticamente.

---

*Si presenta algún problema de vinculación, recuerde verificar su conexión a internet y asegurarse de que el Token ingresado pertenezca a un entorno de **Producción** y no de Sandbox.*
