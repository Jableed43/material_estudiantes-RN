# Clase 02. Primeros pasos con React Native y Expo

## 📚 Índice

1. [Setup Inicial y Comandos](#setup-inicial)
2. [Configuración de Android SDK](#android-sdk)
3. [Conceptos Fundamentales](#conceptos-fundamentales)
   - [Punto de Entrada (Entry Point)](#entry-point)
   - [React Native vs Expo](#rn-vs-expo)
4. [Componentes Básicos](#componentes-basicos)
   - [Equivalencias HTML](#equivalencias-html)
5. [Unidades de Medida](#unidades-medida)
6. [Proyecto Práctico: Mi Perfil](#proyecto-practico)
7. [Buenas Prácticas](#buenas-practicas)
8. [Resumen](#resumen)

---

## 1. Setup Inicial y Comandos {#setup-inicial}

### 🛠️ Comandos de Expo

Para empezar un proyecto moderno de React Native, usaremos **Expo**, que nos facilita enormemente la vida.

**Crear un proyecto nuevo:**
```bash
npx create-expo-app MiApp
```

**Comandos de Desarrollo:**

| Comando | Para qué sirve |
|---------|----------------|
| `npx expo start` | Inicia el servidor. Verás un código QR para escanear con la app **Expo Go**. |
| `npx expo run:android` | Ejecuta la app en un emulador o celular Android (requiere SDK). |
| `npx expo run:ios` | Ejecuta la app en un simulador iOS (solo en Mac). |
| `npx expo start --clear` | Úsalo si algo no funciona bien, limpia la "basura" temporal. |

---

## 2. Configuración de Android SDK {#android-sdk}

Si quieres probar tu app en un emulador de Android, necesitas instalar **Android Studio** y configurar las "Variables de Entorno".

### ⚠️ Nota Importante: Variables de Entorno
Debes configurar la variable `ANDROID_HOME` apuntando a donde instalaste el SDK (usualmente `C:\Users\TuUsuario\AppData\Local\Android\Sdk`). 

**¿Por qué es necesario?**
Sin esto, tu computadora no sabrá dónde están las herramientas para "hablar" con el emulador de Android.

---

## 3. Conceptos Fundamentales {#conceptos-fundamentales}

### 🔌 Punto de Entrada (Entry Point) {#entry-point}

En un proyecto de Expo Router, el archivo que "enciende" todo es `expo-router/entry`. Aunque no lo veas en tus carpetas, está ahí trabajando. Tu trabajo empieza realmente en `app/_layout.tsx`, que es el componente raíz.

### 🔄 React Native vs Expo {#rn-vs-expo}

| Característica | React Native "Puro" | Expo (Recomendado) |
|----------------|---------------------|--------------------|
| **Facilidad**  | Difícil de configurar | Muy fácil, tipo "instala y usa" |
| **Herramientas**| Manuales | Todo incluido (Expo Go, Cámara, etc.) |
| **Ideal para** | Expertos en nativo | Estudiantes y Prototipos rápidos |

---

## 4. Componentes Básicos {#componentes-basicos}

### 🔄 Equivalencias Útiles para los que vienen de la Web {#equivalencias-html}

Si sabes HTML, esto te hará clic de inmediato:

- **`<View>`** es como un `<div>`. Es el contenedor para todo.
- **`<Text>`** es como un `<span>` o `<p>`. **IMPORTANTE**: No puedes poner texto "suelto" en una View, siempre debe estar dentro de un `<Text>`.
- **`<Image>`** es como un `<img>`.
- **`<TextInput>`** es como un `<input type="text">`.

---

## 5. Unidades de Medida {#unidades-medida}

En React Native **no usamos px, em ni rem**.

- **Números directos**: `width: 100` significa "100 puntos lógicos". React Native se encarga de que se vea igual de grande en un teléfono chiquito que en uno gigante.
- **Porcentajes**: Solo funcionan para `width` y `height`. Ej: `width: '100%'`.
- **Flexbox**: Es el rey del diseño. Usamos `flex: 1` para que un elemento ocupe todo el espacio disponible.

---

## 6. Proyecto Práctico: Mi Perfil {#proyecto-practico}

### Objetivo
Crear una tarjeta de presentación digital con tu foto, nombre y una breve biografía.

### Pasos Generales
1. **Contenedor**: Usa una `View` con `flex: 1` y un `backgroundColor` suave.
2. **Imagen**: Agrega una imagen de perfil usando `require('@/assets/images/user.png')`.
3. **Texto**: Añade tu nombre con un `fontSize: 24` y `fontWeight: 'bold'`.
4. **Input**: Agrega un `TextInput` para que el usuario pueda escribir su "estado" o "frase del día".
5. **Scroll**: Envuelve todo en un `<ScrollView>` por si la biografía es muy larga.

---

## ✅ Buenas Prácticas {#buenas-practicas}

- **Usa Expo Go**: No te compliques con emuladores al principio. Usa tu propio teléfono.
- **StyleSheet**: No escribas estilos "inline" (dentro de las etiquetas). Usa `const styles = StyleSheet.create({ ... })` al final del archivo para mantener orden.
- **SafeAreaView**: Úsalo siempre para evitar que el contenido "se choque" con la cámara (notch) o la barra de batería.

---

## 📝 Resumen {#resumen}

### Conceptos Clave Aprendidos
1. **Expo**: Es nuestra plataforma de lanzamiento.
2. **Componentes Nativos**: `<View>`, `<Text>` e `<Image>` son el ABC.
3. **Puntos Lógicos**: Las medidas son inteligentes y se adaptan a cada pantalla.

### Próximos Pasos
- Experimenta cambiando colores en tu proyecto "Mi Perfil".
- Intenta agregar un `Button` que al presionarlo muestre un mensaje con `Alert.alert('Hola!')`.

---

**Última actualización:** Marzo 2026 - Guía para estudiantes React Native.
