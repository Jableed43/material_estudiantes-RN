# Clase 05. Conectando tu app con internet (APIs)

## 📚 Índice

1. [Introducción](#introducción)
2. [¿Qué es una API REST?](#qué-es-una-api-rest)
3. [Fetch API: La herramienta nativa](#fetch-api)
4. [Métodos HTTP (GET, POST, PUT, DELETE)](#métodos-http)
5. [Async/Await: Código Asíncrono Moderno](#uso-moderno-asyncawait)
6. [Teoría: REST y Serialización de Datos](#teoria-rest)
7. [Consumo de APIs Reales (Endpoints)](#endpoints-datos-reales)
8. [Herramientas para Testing (Postman y Axios)](#consumir-datos-reales)
9. [Manejo de estados: Carga y Error](#manejo-de-errores)
10. [MockAPI.io: Tu propio Backend gratis](#mockapio---api-rest-para-pruebas)
11. [Proyecto Práctico: Consumiendo una API](#proyecto-práctico-consumir-api-rest)
12. [Resumen y Buenas Prácticas](#buenas-prácticas)

---

## 1. Introducción {#introducción}

Hasta ahora nuestras apps han funcionado de forma aislada. Hoy aprenderemos a conectarlas con el mundo exterior mediante **APIs REST**, permitiendo que los datos viajen desde un servidor hasta el celular del usuario.

---

## 2. ¿Qué es una API REST? {#qué-es-una-api-rest}

#### ¿Qué es una API?
Es un mensajero que permite que dos aplicaciones se hablen entre sí. Imaginala como un "mozo" en un restaurante: tú (el cliente) haces un pedido, el mozo lleva el pedido a la cocina (el servidor) y te trae la comida (los datos).

#### ¿Qué es un Servidor?
Es una computadora potente encargada de guardar y procesar los datos de millones de usuarios (fotos de Instagram, chats de WhatsApp, productos de Amazon).

#### ¿Qué es el formato JSON?
Es la forma en que las aplicaciones se pasan los datos. Se parece mucho a un objeto de JavaScript `{ "nombre": "Juan" }` y es muy fácil de leer para humanos y máquinas.

---

## 3. Fetch API: La herramienta nativa {#fetch-api}

#### ¿Qué es Fetch API?
Es una función que ya viene dentro de React Native (no hay que instalar nada) y sirve para hacer pedidos a internet (descargar datos de una API).

```javascript
fetch('https://api.ejemplo.com/datos')
  .then(response => response.json())
  .then(data => console.log(data));
```

---

## 4. Métodos HTTP {#métodos-http}

#### ¿Qué son los Métodos HTTP?
Son las "etiquetas" que le ponemos a nuestro pedido para que el servidor sepa qué queremos hacer (leer, crear, borrar o editar).

| Método | Acción | Descripción |
|--------|---------|-------------|
| **GET** | Leer | Pedir información al servidor. |
| **POST** | Crear | Enviar información nueva para que se guarde. |
| **PUT** | Actualizar | Modificar algo que ya existe. |
| **DELETE** | Borrar | Quitar información del servidor. |

---

## 5. Async/Await {#uso-moderno-asyncawait}

#### ¿Qué es una Promesa?
Es un "palo en la rueda" temporal: una tarea que todavía no terminó pero prometió darnos un resultado en el futuro (éxito o error).

#### ¿Qué es Async/Await?
Es la forma moderna de escribir código que espera promesas. Hace que el código asíncrono se lea de arriba hacia abajo, igual que el código normal.

```tsx
const obtenerDatos = async () => {
  try {
    const respuesta = await fetch('https://api.ejemplo.com/users');
    const datos = await respuesta.json();
    setUsuarios(datos);
  } catch (error) {
    console.error("Hubo un error de red", error);
  }
};
```

---

## 6. Manejo de estados: Carga y Error {#manejo-de-errores}

Cuando pides datos a internet, pasan tres cosas:
1. **Cargando**: Mientras esperamos la respuesta (mostramos un `ActivityIndicator`).
2. **Éxito**: Los datos llegaron y los guardamos en un estado.
3. **Error**: El internet falló o el servidor no respondió (mostramos un mensaje al usuario).

---

## 7. MockAPI.io {#mockapio---api-rest-para-pruebas}

#### ¿Qué es un Endpoint?
Es la "dirección web" específica donde pedimos los datos (ejemplo: `https://api.com/usuarios`). Cada sección de la API tiene su propio endpoint.

Para practicar, usaremos [MockAPI.io](https://mockapi.io). Es una herramienta gratuita que te permite crear tu propia API en 2 minutos sin saber nada de servidores. ¡Perfecto para prototipos!

---

## 8. Proyecto Práctico: Consumiendo una API {#proyecto-práctico-consumir-api-rest}

Construiremos una pantalla que traiga una lista de usuarios de MockAPI:
- Usaremos `useEffect` para pedir los datos apenas abra la app.
- Mostraremos una lista con `FlatList`.
- Agregaremos un botón para "Refrescar" la lista.

---

## ✅ Buenas Prácticas

- **Check response.ok**: Siempre verifica que el servidor respondió bien antes de usar los datos.
- **Loading Spiner**: Nunca dejes la pantalla vacía; avísale al usuario que estás cargando.
- **Try/Catch**: Envuelve tus llamadas a internet en bloques try/catch para evitar que la app se cierre inesperadamente.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
