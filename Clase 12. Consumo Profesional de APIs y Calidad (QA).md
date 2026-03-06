# Clase 12. Consumo Profesional de APIs y Calidad (QA)

## 📚 Índice

1. [Endpoints: Direcciones con propósito](#endpoints)
2. [Fetch vs Axios: ¿Cuál elegir?](#herramientas)
3. [Iteración: El arte de mejorar](#iteracion)
4. [QA: Que nada se rompa](#qa)
5. [Proyecto Práctico: App de Tareas con API Real](#proyecto-practico)
6. [Resumen](#resumen)

---

## 1. Endpoints: Direcciones con propósito {#endpoints}

Un **Endpoint** es una dirección web que nos da acceso a una función específica.
- `GET /productos`: Trae la lista.
- `DELETE /productos/5`: Borra el producto con ID 5.

**Dato clave**: Nunca pongas estas direcciones "a mano" en cada botón. Guárdalas en una variable central (como una URL base) para que sea fácil cambiarlas si el servidor se muda.

---

## 2. Fetch vs Axios: ¿Cuál elegir? {#herramientas}

- **Fetch**: Viene gratis con JavaScript. Es simple y liviano.
- **Axios**: Se instala con `npm`. Es más inteligente: ya sabe que lo que recibe es un JSON y te deja manejar errores de forma más cómoda.

**Recomendación**: Para proyectos grandes o que necesiten seguridad (tokens), **Axios** suele ser mejor porque te permite usar "Interceptores" (código que se corre antes de cada pedido).

---

## 3. Iteración: El arte de mejorar {#iteracion}

Hacer una app no es un camino recto. Es un **círculo**:
1. Programas una función.
2. La pruebas.
3. Te das cuenta de que al usuario le falta un botón o un mensaje de error.
4. Vuelves al paso 1 y lo mejoras.

Esto se llama **Iterar**. Las mejores apps del mundo (como WhatsApp) se actualizan todo el tiempo para ser mejores que ayer.

---

## 4. QA: Que nada se rompa {#qa}

**QA (Quality Assurance)** significa "Aseguramiento de Calidad". Es probar tu app como si fueras un usuario que quiere romper todo.

**Tu Checklist de QA personal:**
- [ ] ¿Qué pasa si apago el Wifi mientras la app carga?
- [ ] ¿Qué pasa si dejo un campo vacío en el registro?
- [ ] ¿Se ve bien en un celular chiquito y en uno gigante?
- [ ] ¿Hay un circulito girando (loader) mientras espero a internet?

---

## 5. Proyecto Práctico: App de Tareas con API Real {#proyecto-practico}

### Objetivo
Conectar tu app a una API real, manejar los errores profesionalmente y asegurarte de que la experiencia sea fluida.

### Pasos
1. **Servicio**: Crea un archivo `api.js` donde centralices todos tus pedidos.
2. **Loading**: Asegúrate de que aparezca un `ActivityIndicator` cada vez que pidas datos.
3. **Refinement**: Mejora el diseño de tu lista basándote en el feedback de tus compañeros.

---

## ✅ Buenas Prácticas {#buenas-practicas}

- **No silencies los errores**: No hagas `catch (e) { }`. Al menos pon un `alert("Algo salió mal")` para que el usuario no crea que la app se trabó.
- **Variables de Entorno**: Usa archivos `.env` para guardar las direcciones de tus APIs. Nunca las subas a GitHub directamente si son secretas.
- **Commits Pequeños**: Guarda tus cambios de a poquito. No guardes "toda la app" en un solo paso.

---

## 📝 Resumen {#resumen}

### Conceptos Clave Aprendidos
1. **Endpoint**: La puerta a los datos.
2. **Axios/Fetch**: Tus herramientas de comunicación.
3. **QA**: Tu filtro de calidad antes del lanzamiento.

### Próximos Pasos
- Intenta usar una herramienta como [Postman](https://www.postman.com/) para probar tus APIs antes de escribirlas en el código. ¡Ahorra mucho tiempo!

---

**Última actualización:** Marzo 2026 - Guía para estudiantes.
