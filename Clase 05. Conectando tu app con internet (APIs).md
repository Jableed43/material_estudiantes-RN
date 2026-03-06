# Clase 05. Conectando tu app con internet (APIs)

## 📚 Índice

1. [¿Qué es una API REST?](#que-es-api)
2. [Métodos HTTP (Las acciones)](#metodos)
3. [MockAPI.io: Tu base de datos rápida](#mockapi)
4. [Cómo pedir datos con `fetch`](#fetch)
5. [Enviar datos (POST)](#post)
6. [Manejo de Errores (¿Qué pasa si falla?)](#errores)
7. [Proyecto Práctico: Mi Agenda Online](#proyecto-practico)
8. [Resumen](#resumen)

---

## 1. ¿Qué es una API REST? {#que-es-api}

Imagina que estás en un restaurante. Tú eres el **Cliente** (la app), la cocina es el **Servidor** (donde están los datos) y el mozo es la **API**.
Tú le pides algo al mozo, él va a la cocina y vuelve con tu comida (los datos en formato JSON).

---

## 2. Métodos HTTP (Las acciones) {#metodos}

Cuando usamos una API, le decimos qué queremos hacer con un "verbo" o método:

- **GET**: "Traeme información" (ej: ver lista de amigos).
- **POST**: "Guardá esta información nueva" (ej: crear un usuario nuevo).
- **PUT / PATCH**: "Editá esta información" (ej: cambiar tu foto de perfil).
- **DELETE**: "Borrá esto" (ej: eliminar un post).

---

## 3. MockAPI.io: Tu base de datos rápida {#mockapi}

Para esta clase usaremos [MockAPI.io](https://mockapi.io). Es una web gratuita donde puedes crear una "falsa" base de datos en 2 minutos para probar tu app.

1. Creas un proyecto.
2. Defines un recurso (ej: `usuarios`).
3. Te dan una URL (ej: `https://65ab.mockapi.io/usuarios`).

---

## 4. Cómo pedir datos con `fetch` {#fetch}

Usamos `fetch` junto con `async` y `await` para que la app no se trabe mientras espera los datos de internet.

```javascript
const obtenerDatos = async () => {
  try {
    const respuesta = await fetch('https://mi-api.com/usuarios');
    const datos = await respuesta.json(); // Convertimos la respuesta a algo que JS entienda
    console.log(datos);
  } catch (error) {
    console.log("Algo salió mal:", error);
  }
};
```

---

## 5. Enviar datos (POST) {#post}

Cuando envías datos (como al registrarse), `fetch` necesita más información:

```javascript
const enviarDatos = async (nuevoUsuario) => {
  const respuesta = await fetch('https://mi-api.com/usuarios', {
    method: 'POST', // Queremos CREAR
    headers: {
      'Content-Type': 'application/json' // Decimos que enviamos un JSON
    },
    body: JSON.stringify(nuevoUsuario) // Convertimos el objeto a texto
  });
};
```

---

## 6. Manejo de Errores {#errores}

Internet puede fallar (te quedas sin señal, el servidor se cae). Por eso siempre usamos `try { ... } catch { ... }`.

- **Error 404**: No se encontró lo que pediste.
- **Error 500**: El servidor explotó (error de ellos, no tuyo).
- **Error de Red**: No tienes wifi/datos.

---

## 7. Proyecto Práctico: Mi Agenda Online {#proyecto-practico}

### Objetivo
Hacer una app que lea una lista de contactos desde MockAPI y permita agregar uno nuevo.

### Pasos
1. **Cargar**: Crea un `useEffect` que llame a `fetch` (GET) al abrir la app.
2. **Mostrar**: Usa un `FlatList` para mostrar los nombres y teléfonos.
3. **Agregar**: Crea un formulario con `TextInput` y un botón que haga un `fetch` (POST).

---

## 📝 Resumen {#resumen}

### Conceptos Clave Aprendidos
1. **JSON**: El formato de texto universal para enviar datos.
2. **Async/Await**: Para esperar a internet sin congelar la app.
3. **Fetch**: Tu mozo que va y vuelve con los datos.

### Próximos Pasos
- Intenta agregar un botón de "Eliminar" al lado de cada contacto usando el método `DELETE`.
- ¡Cuidado con no olvidar el `await` antes del `fetch`!

---

**Última actualización:** Marzo 2026 - Guía para estudiantes.
