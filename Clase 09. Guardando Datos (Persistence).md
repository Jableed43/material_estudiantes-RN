# Clase 09. Guardando Datos (AsyncStorage y Firebase)

## 📚 Índice

1. [¿Qué es la persistencia?](#que-es-persistencia)
2. [AsyncStorage: El cuaderno de notas del celular](#asyncstorage)
3. [Firebase: Tu base de datos en la nube](#firebase)
4. [Firestore: Datos en tiempo real](#firestore)
5. [Proyecto Práctico: App de Notas Sincronizadas](#proyecto-practico)
6. [Resumen](#resumen)

---

## 1. ¿Qué es la persistencia? {#que-es-persistencia}

Hasta ahora, si cerrabas tu app, todo lo que habías hecho se borraba. La **persistencia** es la capacidad de guardar datos para que sigan ahí la próxima vez que abras la app.

**Hay dos formas principales:**
- **Local (AsyncStorage)**: Solo en tu teléfono. Útil para "Recordar mi usuario" o configuraciones.
- **Nube (Firebase)**: En internet. Útil para que tus datos estén en cualquier teléfono donde abras tu cuenta.

---

## 2. AsyncStorage: El cuaderno local {#asyncstorage}

Es como una pequeña lista de "Clave" y "Valor". 

**Operaciones básicas:**
- **Guardar**: `await AsyncStorage.setItem('nombre', 'Juan')`
- **Leer**: `const valor = await AsyncStorage.getItem('nombre')`
- **Borrar**: `await AsyncStorage.removeItem('nombre')`

> **Importante**: Solo guarda texto. Si quieres guardar un objeto (como un usuario con nombre y edad), tienes que convertirlo a texto con `JSON.stringify()`.

---

## 3. Firebase: Tu base de datos profesional {#firebase}

Firebase es una plataforma de Google que nos da todo el backend "gratis" para empezar. 
No necesitas crear un servidor propio; Firebase ya lo hizo por ti.

**Lo que vamos a usar:**
- **Console**: La web donde configuramos todo.
- **Firestore**: La base de datos donde guardaremos las notas.

---

## 4. Firestore: Datos en tiempo real {#firestore}

Firestore es una base de datos **NoSQL**. En lugar de tablas, usa **Colecciones** (carpetas) y **Documentos** (archivos).

**Lo mejor de Firestore**: Si alguien cambia un dato en la base de datos, tu app se actualiza **automáticamente** sin que tengas que refrescar nada (**onSnapshot**).

---

## 5. Proyecto Práctico: App de Notas Sincronizadas {#proyecto-practico}

### Objetivo
Crear una app donde puedas escribir notas, se guarden en Firebase y si abres la app en otro teléfono (o en la web), ¡las notas aparezcan ahí mágicamente!

### Pasos
1. **Configurar Firebase**: Crea un proyecto en [console.firebase.google.com](https://console.firebase.google.com).
2. **Conectar**: Copia las claves (`apiKey`, `projectId`, etc.) a tu código.
3. **Guardar**: Usa la función `addDoc` para enviar la nota a la nube.
4. **Escuchar**: Usa `onSnapshot` para mostrar la lista de notas que vienen de internet.

---

## ✅ Buenas Prácticas {#buenas-practicas}

- **No guardes contraseñas en AsyncStorage**: Cualquiera con acceso al teléfono podría leerlas. Usa herramientas más seguras para eso.
- **Usa prefijos**: Llama a tus claves `@MiApp:usuario` para no mezclarte con otras apps.
- **Reglas de seguridad**: En Firebase, recuerda configurar quién puede leer y borrar datos para que extraños no borren tus notas.

---

## 📝 Resumen {#resumen}

### Conceptos Clave Aprendidos
1. **Persistencia**: Datos que no mueren al cerrar la app.
2. **JSON.stringify / parse**: El puente entre objetos y texto.
3. **Firestore**: La base de datos mágica de Google que se actualiza sola.

### Próximos Pasos
- ¿Puedes hacer que la app guarde el nombre del usuario al iniciar sesión para no pedírselo nunca más? (Usa `AsyncStorage`).

---

**Última actualización:** Marzo 2026 - Guía para estudiantes.
