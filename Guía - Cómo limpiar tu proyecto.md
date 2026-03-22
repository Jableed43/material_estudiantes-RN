# Guía: Cómo limpiar un proyecto nuevo de Expo

## 🎯 Objetivo

#### ¿Qué es Limpiar un Proyecto (Cleanup)?
Es el proceso de borrar los archivos y el código de ejemplo que vienen por defecto al crear una app nueva. Sirve para que tu proyecto esté ordenado y solo tenga el código que tú escribiste.

#### ¿Qué es el Código de Ejemplo (Boilerplate)?
Es código listo para usar que te regalan las herramientas (como Expo) para que veas qué se puede hacer. Es muy útil al principio, pero molesta cuando quieres empezar tu propia idea desde cero.

Cuando creas un proyecto de Expo con `npx create-expo-app`, este viene con mucho código de ejemplo que puede marearte. En esta guía aprenderás a borrar lo que sobra para empezar tu propia app desde cero y con orden.

## 📚 Índice

1. [Limpiar la Pantalla Principal](#limpiar-index)
2. [Simplificar la Navegación](#limpiar-tabs)
3. [Borrar lo que no usas](#borrar-extras)
4. [Verificar que todo esté OK](#verificar)

## 1. Limpiar la Pantalla Principal {#limpiar-index}

El archivo más importante es `app/(tabs)/index.tsx`. Es lo primero que se ve al abrir la app.

**Acción:** Borra todo lo que hay en ese archivo y pega este código básico. Es como tener un lienzo en blanco pero con lo mínimo necesario para que funcione.

```tsx
import React from 'react';
import { View, Text, StyleSheet, SafeAreaView } from 'react-native';

export default function HomeScreen() {
  return (
    <SafeAreaView style={styles.container}>
      <View style={styles.content}>
        <Text style={styles.titulo}>Mi Nueva App</Text>
        <Text style={styles.subtitulo}>Proyecto limpio y listo 🚀</Text>
      </View>
    </SafeAreaView>
  );
}

const styles = StyleSheet.create({

#### ¿Qué es el StyleSheet?
Es una herramienta de React Native que nos permite escribir reglas de estilo (colores, tamaños, márgenes) de forma organizada y eficiente, muy parecido a como se usa el CSS en las páginas web.
  container: {
    flex: 1,
    backgroundColor: '#fff',
  },
  content: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    padding: 20,
  },
  titulo: {
    fontSize: 24,
    fontWeight: 'bold',
    marginBottom: 10,
  },
  subtitulo: {
    fontSize: 16,
    color: '#666',
  },
});
```

---

## 2. Simplificar la Navegación {#limpiar-tabs}

Si no quieres tener dos botones abajo (index y explore), puedes ir a `app/(tabs)/_layout.tsx` y quitar la pantalla que no necesites. 

**Tip:** Si eres principiante, deja solo la pestaña `index` para no complicarte con la navegación todavía.

---

## 3. Borrar lo que no usas (Opcional pero recomendado) {#borrar-extras}

### 📂 Carpeta `components/`
Puedes borrar archivos como `hello-wave.tsx` o `parallax-scroll-view.tsx`. Son ejemplos bonitos pero ocupan espacio y pueden confundirte.

### 📂 Carpeta `assets/images/`
Borra el logo de React (`react-logo.png`) y las imágenes de ejemplo. **¡No borres `icon.png` ni `splash-icon.png`!** Son el icono y la pantalla de carga de tu propia app.

---

## 4. Verificar que todo esté OK {#verificar}

Después de limpiar, corre estos comandos en tu terminal:

1. `npm install` (Para asegurarte de tener todo lo necesario).
2. `npx expo start` (Para arrancar el servidor).

#### ¿Qué es un Servidor de Desarrollo?
Es un programa que corre en tu computadora y "emite" tu código hacia tu celular. Permite que cada vez que guardas un cambio en el código, lo veas al instante en tu equipo sin tener que esperar.

**Si ves tu texto "Mi Nueva App" en el celular, ¡felicitaciones! Has limpiado tu proyecto con éxito.**

---

## 📝 Resumen para el Alumno
- **Limpiar nos ayuda a concentrarnos** en lo que realmente estamos construyendo.
- **`SafeAreaView`** es tu mejor amigo: evita que el texto se esconda detrás de la cámara del celular.
- **No tengas miedo de borrar**: Si algo se rompe, siempre puedes crear un proyecto nuevo de prueba para ver cómo estaba antes.

---

**Última actualización:** Marzo 2026 - Guía práctica para estudiantes.
