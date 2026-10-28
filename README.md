# NoGhost

**NoGhost** es un sistema de gestión de reservas para establecimientos del sector servicios, concretamente peluquerías y centros de estética. Su objetivo es reducir las citas a las que el cliente no se presenta sin avisar (*no-shows* o "ghosting"), recuperar los ingresos que se pierden por ellas y centralizar la gestión diaria del local.

Proyecto de la asignatura **Ingeniería del Software (INSO)**, Grado en Ingeniería Informática, Universidad de León. Grupo G20.

## ¿Qué hace?

- **Bot de Telegram para clientes:** registro, inicio de sesión (`/login`), consulta de disponibilidad, reserva y cancelación de citas, y recordatorios automáticos 24 h y 1 h antes.
- **Aplicación de escritorio Java (JavaFX, MVC) para el local:** agenda y calendario, catálogo de servicios, horarios de empleados, marcado de asistencias e inasistencias, cobros y caja, informes y auditoría.
- **Sistema Anti-Ghosting:** cancelar con 24 h o más de antelación no tiene coste, cancelar con menos de 24 h supone un recargo del 50 % y no presentarse, un 75 %. La deuda se acumula en el perfil del cliente y se cobra en el local.
- **Pago opcional:** se configura con la variable `PAYMENT_MODE`:
  - `off` (por defecto): sin pasarela, todo se cobra en el local.
  - `mock`: pasarela simulada, para pruebas y demostraciones.
  - `real`: Stripe (Sandbox). La tarjeta nunca se escribe en la app ni en Telegram, sino en la página segura de Stripe, y registrarla no conlleva ningún cargo.

El sistema no incluye ninguna página web propia. Funciona entero sin la pasarela de pago.

Roles: **Administrador**, **Empleado** y **Cliente**.

## ¿Qué haremos en este repositorio?

1. **Especificación de requisitos (ERS)** según IEEE 830.
2. **Modelo de casos de uso:** diagramas, casos de uso en formato completo y diagramas de secuencia del sistema.
3. **Diseño:** diagramas de clases, de secuencia y modelo de datos.
4. **Entorno Docker:** `docker-compose.yml` con la base de datos MariaDB (con datos de prueba) y el bot de Telegram, que se levanta con `docker compose up -d`.
5. **Implementación** en Java con Maven: aplicación de escritorio JavaFX y bot de Telegram.
6. **Pruebas** y documentación de puesta en marcha.

## Tecnologías

Java, JavaFX, Maven, MariaDB, Telegram Bot API, Docker / Docker Compose y Stripe (opcional).

## Estructura

```
docs/   Documentación del proyecto (ERS, casos de uso…)
```

La configuración sensible (token del bot, credenciales de la base de datos, `PAYMENT_MODE`, claves de Stripe) irá en un fichero `.env` no versionado, a partir de la plantilla `.env.example`.

## Equipo

| Integrante | Responsabilidades |
|---|---|
| Erik Missere Baumann | Reservas, motor Anti-Ghosting e integración con Telegram |
| Fernando Javier Manzano Pinto | Catálogo de servicios, calendario, paginación e informes |
| Jonatan Yepes Carvalho | Autenticación, seguridad, clientes, roles y auditoría |
