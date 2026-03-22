# Clase 13. Testing, builds y publicación en tiendas

## 📚 Índice

1. [Testing: ¿Cómo saber si tu app funciona?](#testing-intro)
2. [Introducción a Jest y Expo Test](#jest-expo)
3. [Tipos de Builds (APK vs AAB)](#tipos-builds)
4. [EAS Build: El constructor en la nube](#eas-build)
5. [Publicación en las Tiendas (Google Play / App Store)](#publicacion)
6. [Precios y Requisitos de las Tiendas](#requisitos)
7. [Proyecto Práctico: Mi Primera Build en Vivo](#proyecto-practico)
8. [Resumen y Pasos Finales](#resumen)

---

## 1. Testing Automatizado (`Jest`) {#testing-intro}

Hacer **Testing** es escribir código que prueba tu código. Es la única forma de no romper lo anterior al cambiar algo nuevo.
- **Jest**: El framework de testing líder en el ecosistema.
- **Expo Test**: Integración de Jest con el mundo Expo.

```javascript
it('el botón debe decir "Enviar"', () => {
  const { getByText } = render(<MiBoton title="Enviar" />);
  expect(getByText('Enviar')).toBeTruthy();
});
```

---

## 2. Builds de Producción: Generando el instalador {#tipos-builds}

Para que alguien pueda instalar tu app, necesitas un archivo instalador:
- **Android**: Un `.apk` (instalación manual) o `.aab` (formato para subir a la tienda).
- **iOS**: Un archivo `.ipa` (solo se sube a App Store Connect).

---

## 3. Expo Application Services (EAS Build) {#eas-build}

Antes necesitabas computadoras de 3000 dólares para construir apps. Hoy, **Expo lo hace por ti** en sus servidores.
1. Comando moderno: `eas build`.
2. Expo construye la app y te da un link de descarga.
3. Puedes ver el proceso desde el dashboard de Expo.

---

## 4. Publicación en las Tiendas {#publicacion}

| Tienda | Requisito Principal | Costo |
|--------|----------------------|-------|
| **Google Play (Android)** | Cuenta de Developer Google | $25 USD (Un solo pago) |
| **App Store (iOS)** | Cuenta Apple Developer | $99 USD (Cada año) |

### Pasos para publicar:
1. Crear la cuenta de desarrollador.
2. Completar la descripción, el ícono y las capturas de pantalla (screenshots).
3. Subir el archivo generado por EAS.
4. Esperar revisión (Google tarda 2-4 días, Apple 24-48 horas).

---

## 5. Configuración: `app.json` {#requisitos}

Este es el DNI de tu app. En este archivo defines:
- **Nombre**: Cómo se llama la app en el celu.
- **Versión**: Empezamos en `1.0.0`.
- **Icono**: La imagen de acceso.
- **Package name**: Identificador único global (Ej: `com.tuusuario.miapp`).

---

## 6. Proyecto Práctico: Mi Primera Build en Vivo {#proyecto-practico}

### Objetivo
Llevar la aplicación fuera de la red de desarrollo y generar un instalador real que puedas enviarle a un amigo.

### Pasos Generales
1. Configurar `app.json` con un nombre e ícono personalizados.
2. Hacer login en tu cuenta de Expo desde la terminal (`npx expo login`).
3. Instalar la herramienta EAS (`npm install -g eas-cli`).
4. Ejecutar `eas build --platform android --profile preview`.
5. Descargar el APK resultante e instalarlo en un celular físico.

### Resultado Final
Una aplicación real instalada en un dispositivo como cualquier otra app de la Play Store.

---

## ✅ Tips de Clase

- ✅ **Versiones**: Si subes una corrección, cambia siempre la versión (Ej: `1.0.1`). Las tiendas no aceptan la misma versión dos veces.
- ✅ **Permissions**: Si el proyecto pide permiso para la Cámara y no la usas, quítalo del archivo `app.json`. Apple suele rechazar apps con permisos de más.
- ✅ **Peso**: Si tu app pesa mucho, revisa las imágenes de tus assets. ¡Usa imágenes comprimidas!

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
