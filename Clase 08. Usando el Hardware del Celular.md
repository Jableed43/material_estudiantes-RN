# Clase 08. Usando el Hardware del Celular

## 📚 Índice

1. [Introducción al acceso nativo](#introduccion)
2. [Gestión de Permisos (La llave del hardware)](#gestion-permisos)
3. [La Cámara (expo-camera)](#camara)
4. [Audio: Grabación y Reproducción (expo-av)](#audio)
5. [Ubicación GPS (expo-location)](#ubicacion)
6. [Sensores: El movimiento del celular](#sensores)
7. [Proyecto Práctico: App de Captura](#proyecto-practico)
8. [Buenas Prácticas](#resumen)

---

## 1. Introducción al acceso nativo {#introduccion}

React Native nos permite usar el hardware del teléfono (cámara, GPS, sensores) escribiendo solo JavaScript. Gracias a **Expo**, no necesitamos saber programar en Android (Java) o iOS (Swift) para encender la cámara o saber dónde está el usuario.

---

## 2. Gestión de Permisos {#gestion-permisos}

Por seguridad, Apple y Google no dejan que cualquier app use la cámara sin preguntar.
**Flujo de permisos:**
1. **Preguntar**: "Hola usuario, ¿me dejas usar la cámara?"
2. **Esperar**: El usuario acepta o rechaza.
3. **Actuar**: Si acepta, prendemos la cámara. Si rechaza, le explicamos por qué la necesitamos.

```tsx
const [status, requestPermission] = useCameraPermissions();

if (!status.granted) {
  return <Button title="Pedir Permiso" onPress={requestPermission} />
}
```

---

## 3. La Cámara (expo-camera) {#camara}

Podemos integrar una vista de cámara directamente en nuestra app.
- **`facing`**: Para elegir cámara frontal o trasera.
- **`takePictureAsync`**: Para capturar la imagen y guardarla en el celular.

---

## 4. Audio (expo-av) {#audio}

Con este módulo podemos hacer dos cosas:
1. **Grabar**: Usar el micrófono para crear archivos de audio.
2. **Reproducir**: Escuchar sonidos locales o música de internet.

---

## 5. Ubicación GPS (expo-location) {#ubicacion}

Permite obtener las coordenadas (latitud y longitud) del usuario.
- **`getCurrentPositionAsync`**: Obtener la posición una sola vez.
- **`watchPositionAsync`**: Seguir al usuario mientras camina (ideal para apps de mapas o delivery).

---

## 6. Sensores (expo-sensors) {#sensores}

Tu celular está lleno de sensores:
- **Acelerómetro**: Sabe si el teléfono se mueve o se sacude.
- **Giroscopio**: Sabe hacia dónde está rotando el celular (útil para juegos).
- **Podómetro**: Cuenta los pasos que das en el día.

---

## 7. Proyecto Práctico: App de Captura {#proyecto-practico}

Construiremos una app que:
1. Pida permiso para usar la **Cámara**.
2. Al sacar una foto, guarde también la **Ubicación GPS** de dónde se tomó.
3. Muestre en pantalla si el celular se está moviendo usando el **Acelerómetro**.

---

## ✅ Buenas Prácticas

- ✅ **Pide permiso justo a tiempo**: No pidas el GPS apenas abre la app, pídelo cuando el usuario quiera usar el mapa.
- ✅ **Explica el porqué**: Siempre pon un texto amigable: "Necesitamos tu ubicación para mostrarte los locales cercanos".
- ✅ **Limpieza**: Si activas el GPS o un sensor, asegúrate de apagarlo cuando el usuario salga de esa pantalla para no gastar batería.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
