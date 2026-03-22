# Clase 05. Conectando tu app con internet (APIs)

## 📚 Índice

1. [Introducción](#introducción)
2. [¿Qué es una API REST?](#qué-es-una-api-rest)
3. [Fetch API: La herramienta nativa](#fetch-api)
4. [Métodos HTTP (GET, POST, PUT, DELETE)](#métodos-http)
5. [Async/Await: Código Asíncrono Moderno](#uso-moderno-asyncawait)
6. [Manejo de estados: Carga y Error](#manejo-de-errores)
7. [MockAPI.io: Tu propio Backend gratis](#mockapio---api-rest-para-pruebas)
8. [Proyecto Práctico: Consumiendo una API](#proyecto-práctico-consumir-api-rest)
9. [Resumen y Buenas Prácticas](#buenas-prácticas)

---

## 1. Introducción {#introducción}

Hasta ahora nuestras apps han funcionado de forma aislada. Hoy aprenderemos a conectarlas con el mundo exterior mediante **APIs REST**, permitiendo que los datos viajen desde un servidor hasta el celular del usuario.

---

## 2. ¿Qué es una API REST? {#qué-es-una-api-rest}

Una API es como un "mozo" en un restaurante: tú (el cliente) haces un pedido, el mozo lleva el pedido a la cocina (el servidor) y te trae la comida (los datos).
- **REST** es el lenguaje estándar que usan casi todas las aplicaciones modernas.
- Los datos viajan en formato **JSON** (objetos de JavaScript).

---

## 3. Fetch API: La herramienta nativa {#fetch-api}

En React Native no necesitamos instalar nada extra para conectarnos a internet. Usamos `fetch()`, que es nativo y muy potente.

```javascript
fetch('https://api.ejemplo.com/datos')
  .then(response => response.json())
  .then(data => console.log(data));
```

---

## 4. Métodos HTTP {#métodos-http}

| Método | Acción | Descripción |
|--------|---------|-------------|
| **GET** | Leer | Pedir información al servidor. |
| **POST** | Crear | Enviar información nueva para que se guarde. |
| **PUT** | Actualizar | Modificar algo que ya existe. |
| **DELETE** | Borrar | Quitar información del servidor. |

---

## 5. Async/Await {#uso-moderno-asyncawait}

Es la forma más limpia de escribir código que "espera" a internet.

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
