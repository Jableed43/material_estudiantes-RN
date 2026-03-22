# Clase 09. Guardando Datos (Persistence)

## 📚 Índice

1. [Teoría: ¿Por qué los estados son volátiles?](#teoria-persistencia)
2. [¿Qué es la Persistencia de Datos?](#persistencia)
3. [Almacenamiento Local (AsyncStorage)](#asyncstorage)
4. [Almacenamiento en la Nube (Firebase)](#firebase)
5. [Configuración de Firebase Paso a Paso](#firebase-configuracion)
6. [Firestore: Base de datos en tiempo real](#firestore)
7. [Operaciones CRUD (Crear, Leer, Actualizar, Borrar)](#firestore-escritura)
8. [Proyecto Práctico: App de Notas en la Nube](#proyecto-practico)
9. [Buenas Prácticas de Almacenamiento](#resumen)

---

## 1. Teoría: La Memoria Volátil {#teoria-persistencia}

#### ¿Qué es la Memoria RAM?
Es la memoria de corto plazo de tu celular. Es súper rápida, pero "volátil": en cuanto cierras la app o apagas el equipo, todo lo que estaba ahí (como los `useState`) se borra para siempre.

#### ¿Qué es el Almacenamiento Persistente?
Es como el disco rígido o la memoria SD. Es más lenta que la RAM, pero los datos quedan guardados "para siempre" (hasta que tú decidas borrarlos), incluso si el celular se queda sin batería.

**Regla**: Si quieres que tu usuario siga con su sesión abierta mañana, el dato debe ir a la memoria de almacenamiento.

---

## 1. ¿Qué es la persistencia de datos? {#persistencia-datos}

#### ¿Qué es la Persistencia?
Es la capacidad de una aplicación para "recordar" información a largo plazo, haciendo que los datos sobrevivan a los cierres de la app o reinicios del sistema.

La **persistencia** permite que los datos de tu app sigan ahí aunque cierres la app o apagues el celular.
- **Local**: Se guarda en el teléfono (ej: configuración de tema oscuro, token de sesión).
- **Remota**: Se guarda en un servidor (ej: tus chats de WhatsApp, tus fotos de Instagram).

---

## 2. AsyncStorage (Persistencia Local) {#asyncstorage}

#### ¿Qué es AsyncStorage?
Es un sistema de almacenamiento "clave-valor" (como un diccionario) que vive dentro del celular. Sirve para guardar configuraciones simples, como el nombre del usuario o si prefiere el modo oscuro.

```tsx
// Guardar:
await AsyncStorage.setItem('@mi_app:usuario', 'Juan');

// Leer:
const nombre = await AsyncStorage.getItem('@mi_app:usuario');
```

---

## 3. Firebase (Persistencia en la Nube) {#firebase}

#### ¿Qué es Firebase?
Es una plataforma de Google que nos ofrece bases de datos, autenticación y almacenamiento en la nube sin que tengamos que programar nuestro propio servidor.

#### ¿Qué es el Tiempo Real (Realtime)?
Significa que los cambios se ven al instante en todos los dispositivos conectados, sin necesidad de que el usuario "refresque" la pantalla.

---

## 4. Configuración de Firebase {#firebase-configuracion}

1. Crea un proyecto en [console.firebase.google.com](https://console.firebase.google.com).
2. Agrega una app tipo **Web** (sí, aunque sea para celular, usamos el SDK de Web en React Native).
3. Copia las credenciales (`apiKey`, `projectId`, etc.) a un archivo `firebaseConfig.ts`.

---

## 5. Firestore: Base de datos NoSQL {#firestore}

#### ¿Qué es una Base de Datos NoSQL?
A diferencia de las bases de datos de tablas (como Excel), NoSQL guarda los datos en trozos flexibles llamados "Documentos" que se parecen a los objetos JSON de JavaScript.

#### ¿Qué es una Colección / Documento?
- **Colección**: Es una "carpeta" que agrupa cosas del mismo tipo (ej: "usuarios").
- **Documento**: Es la "ficha" individual de cada cosa (ej: los datos de Juan).

### Leer en tiempo real con `onSnapshot`
Esta función es mágica: se queda escuchando a Firebase y cada vez que alguien agrega una nota, tu app la muestra al instante.

---

## 6. Operaciones CRUD {#firestore-escritura}

#### ¿Qué es el CRUD?
Son las 4 operaciones básicas de cualquier aplicación del mundo:
- **C**reate (Crear): Agregar un dato nuevo (`addDoc`).
- **R**ead (Leer): Consultar la información (`getDocs`).
- **U**pdate (Actualizar): Editar un dato existente (`updateDoc`).
- **D**elete (Borrar): Quitar un dato (`deleteDoc`).

---

## 7. Proyecto Práctico: App de Notas en la Nube {#proyecto-practico}

Haremos una app de "Muro de Mensajes":
1. El usuario escribe su nombre y un mensaje.
2. El mensaje se guarda en Firebase.
3. Todos los que tengan la app abierta verán el nuevo mensaje aparecer automáticamente sin tocar nada.

---

## ✅ Buenas Prácticas

- ✅ **No guardes contraseñas en AsyncStorage**: Para eso se usa `expo-secure-store`.
- ✅ **Usa prefijos**: En AsyncStorage usa `@mi_app:clave` para no mezclar datos con otras apps.
- ✅ **Limpia tus Listeners**: Si usas `onSnapshot`, recuerda cerrarlo cuando el usuario salga de la pantalla para no gastar datos.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
