# Clase 08. Usando el Hardware del Celular (Sensores, Cámara y GPS)

## 📚 Índice

1. [¿Qué es el acceso nativo?](#que-es-nativo)
2. [La regla de oro: Los Permisos](#permisos)
3. [Usando la Cámara](#camara)
4. [GPS y Ubicación](#gps)
5. [Sensores (Movimiento y Giro)](#sensores)
6. [Proyecto Práctico: App 007 - Super Herramientas](#proyecto-practico)
7. [Buenas Prácticas](#buenas-practicas)
8. [Resumen](#resumen)

---

## 1. ¿Qué es el acceso nativo? {#que-es-nativo}

Hasta ahora nuestras apps eran solo texto y botones. El **acceso nativo** significa que nuestra app puede "hablar" con el hardware del teléfono: la cámara, el chip de GPS, el micrófono o los sensores de movimiento.

Gracias a **Expo**, no necesitamos saber lenguajes complicados como Swift o Kotlin; lo hacemos todo con JavaScript.

---

## 2. La regla de oro: Los Permisos {#permisos}

Por seguridad, no puedes usar la cámara de alguien sin que él te deje. 

**Flujo de permisos:**
1. **Preguntar**: "Hola, ¿me dejas usar la cámara para tu foto de perfil?".
2. **Esperar**: El usuario dice "Sí" o "No".
3. **Actuar**: Solo si dijo que sí, abrimos el hardware.

> **Tip para estudiantes**: Si el usuario dice que no una vez, el celular suele recordar esa respuesta. Tendrás que ir a los Ajustes del celular para cambiarlo manualmente.

---

## 3. Usando la Cámara {#camara}

Usamos la librería `expo-camera`. 

```javascript
const [permiso, pedirPermiso] = useCameraPermissions();

// Para tomar la foto:
const foto = await cameraRef.current.takePictureAsync();
console.log(foto.uri); // Aquí está la ruta de la imagen guardada
```

---

## 4. GPS y Ubicación {#gps}

Con `expo-location` podemos saber exactamente dónde está el usuario (Latitud y Longitud).
- **Útil para**: Apps de mapas, clima o delivery.

```javascript
const location = await Location.getCurrentPositionAsync({});
console.log(location.coords.latitude, location.coords.longitude);
```

---

## 5. Sensores (Movimiento) {#sensores}

Tu celular tiene un **Acelerómetro**. Sabe si lo estás agitando, si está acostado o si estás caminando.
- **Dato curioso**: Así es como los juegos de carreras saben cuándo giras el teléfono como un volante.

---

## 6. Proyecto Práctico: App de Herramientas {#proyecto-practico}

### Objetivo
Crear una app con 3 botones:
1. **"Foto"**: Abre la cámara y saca una foto.
2. **"Donde estoy"**: Muestra tu dirección actual usando el GPS.
3. **"Nivel"**: Usa el acelerómetro para decirte si el teléfono está derecho.

### Pasos
- Instala las librerías necesarias con `npx expo install`.
- Crea una pantalla para cada herramienta.
- **¡No olvides pedir los permisos al entrar a cada pantalla!**

---

## ✅ Buenas Prácticas {#buenas-practicas}

- **Pide permisos solo cuando los necesites**: No pidas permiso de cámara apenas se abre la app si el usuario todavía no quería sacar una foto.
- **Explica por qué**: "Necesito el GPS para decirte dónde está el cajero más cercano".
- **Limpia los sensores**: Si usas el acelerómetro y sales de esa pantalla, apágalo. Si no, ¡la batería del celular se agotará rapidísimo!

---

## 📝 Resumen {#resumen}

### Conceptos Clave Aprendidos
1. **Módulos Expo**: Herramientas listas para usar el hardware.
2. **Async/Await**: Vital para esperar a que el hardware responda.
3. **granted/denied**: Los dos estados de un permiso.

### Próximos Pasos
- ¿Puedes hacer que el celular vibre cuando el usuario presiona un botón? (Busca `expo-haptics`).

---

**Última actualización:** Marzo 2026 - Guía para estudiantes.
