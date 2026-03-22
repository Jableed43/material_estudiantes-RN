# Clase 09. Guardando Datos (Persistence)

## 📚 Índice

1. [¿Qué es la persistencia de datos?](#persistencia-datos)
2. [Almacenamiento Local (AsyncStorage)](#asyncstorage)
3. [Almacenamiento en la Nube (Firebase)](#firebase)
4. [Configuración de Firebase Paso a Paso](#firebase-configuracion)
5. [Firestore: Base de datos en tiempo real](#firestore)
6. [Operaciones CRUD (Crear, Leer, Actualizar, Borrar)](#firestore-escritura)
7. [Proyecto Práctico: App de Notas en la Nube](#proyecto-practico)
8. [Buenas Prácticas de Almacenamiento](#resumen)

---

## 1. ¿Qué es la persistencia de datos? {#persistencia-datos}

La **persistencia** permite que los datos de tu app sigan ahí aunque cierres la app o apagues el celular.
- **Local**: Se guarda en el teléfono (ej: configuración de tema oscuro, token de sesión).
- **Remota**: Se guarda en un servidor (ej: tus chats de WhatsApp, tus fotos de Instagram).

---

## 2. AsyncStorage (Persistencia Local) {#asyncstorage}

Es como el `localStorage` de la web pero para React Native. Sirve para guardar cosas pequeñas.

```tsx
// Guardar:
await AsyncStorage.setItem('@mi_app:usuario', 'Juan');

// Leer:
const nombre = await AsyncStorage.getItem('@mi_app:usuario');
```

---

## 3. Firebase (Persistencia en la Nube) {#firebase}

**Firebase** es una plataforma de Google que nos da un "Backend" completo sin tener que programar un servidor.
- **Ventaja**: ¡Es en tiempo real! Si cambias algo en la base de datos, el celular se actualiza solo sin que el usuario tenga que refrescar.

---

## 4. Configuración de Firebase {#firebase-configuracion}

1. Crea un proyecto en [console.firebase.google.com](https://console.firebase.google.com).
2. Agrega una app tipo **Web** (sí, aunque sea para celular, usamos el SDK de Web en React Native).
3. Copia las credenciales (`apiKey`, `projectId`, etc.) a un archivo `firebaseConfig.ts`.

---

## 5. Firestore: Base de datos NoSQL {#firestore}

Firestore organiza los datos en **Colecciones** y **Documentos**.
- **Colección**: "usuarios"
- **Documento**: Cada usuario individual con su nombre, mail, etc.

### Leer en tiempo real con `onSnapshot`
Esta función es mágica: se queda escuchando a Firebase y cada vez que alguien agrega una nota, tu app la muestra al instante.

---

## 6. Operaciones CRUD {#firestore-escritura}

- **Create**: `addDoc` (Agregar documento).
- **Read**: `getDocs` o `onSnapshot`.
- **Update**: `updateDoc` (Modificar un campo).
- **Delete**: `deleteDoc` (Quitar un documento).

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
