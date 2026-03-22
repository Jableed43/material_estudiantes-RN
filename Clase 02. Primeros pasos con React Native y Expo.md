# Clase 02. Primeros pasos con React Native y Expo

## 📚 Índice

1. [Teoría: UI Declarativa (Programar el "Qué")](#teoria-declarativa)
2. [Setup Inicial (Configuración rápida)](#setup-inicial)
3. [¿Qué es Expo? (Y por qué lo usamos)](#que-es-expo)
   - [¿Por qué usar Expo Router?](#expo-router)
   - [Diferencias entre React (Web) y React Native (Mobile)](#diferencias-web-mobile)
4. [Componentes Básicos de Interfaz (UI)](#componentes-basicos)
   - [View, Text e Image](#view-text-image)
   - [Interacción con Button y TouchableOpacity](#botones)
5. [Diseño y Layout con Flexbox](#estilos-flexbox)
   - [Eje Principal y Cruzado](#ejecucion-flexbox)
   - [Unidades de Medida en Móviles](#unidades-medida)
6. [Proyecto Práctico: Mi Perfil Personal](#proyecto-practico)
7. [Resumen y Consejos de Estilo](#resumen)

---

## 1. Teoría: UI Declarativa (Programar el "Qué") {#teoria-declarativa}

#### ¿Qué es la Programación Imperativa?
Es cuando le das órdenes paso a paso a la computadora: "Buscá el botón, cambiale el color, mostrá este texto". Es como darle direcciones a un taxista.

#### ¿Qué es la UI Declarativa? (React)
Es cuando simplemente describes **cómo quieres que se vea** la pantalla según el estado actual: "Si el usuario está logueado, mostrá su foto". React se encarga de hacer los cambios por ti. Es como pedir un menú por nombre en un restaurante.

---

## 2. Setup Inicial (Configuración rápida) {#setup-inicial}

Para empezar hoy, configuramos todo lo necesario para programar y ver los cambios al instante.
1. Comando moderno para crear apps: `npx create-expo-app MiApp`.
2. Servidor de desarrollo: `npx expo start`.
3. Ver cambios: Escanea el código QR con la app **Expo Go** (Android) o la cámara (iOS).

⚠️ **Importante**: No instales `expo-cli` globalmente (`npm install -g`), usa siempre `npx`.

---

## 3. Diferencias clave: Web vs Mobile {#diferencias-web-mobile}

#### ¿Qué es un Componente Nativo?
Es una pieza de interfaz (botón, texto, vista) que no es un dibujo, sino un elemento real del sistema operativo (Android o iOS) que React Native controla por nosotros.

React Native no usa etiquetas HTML, usa componentes de interfaz nativos:

| Web (HTML) | Mobile (React Native) | Uso |
|------------|-----------------------|-----|
| `<div>` | `<View>` | Contenedor principal |
| `<span>` / `<p>` | `<Text>` | Para TODO el texto |
| `<img>` | `<Image>` | Fotos (locales o remotas) |
| `<a>` / `<button>` | `<TouchableOpacity>` | Para botones interactivos |

---

## 4. Componentes Básicos {#componentes-basicos}

#### ¿Qué es un <View>?
Es el bloque de construcción más básico. Imaginalo como una "caja" o un contenedor donde metes otros elementos para agruparlos y darles estilo. (Es el equivalente al `<div>` en la web).

#### ¿Qué es un <Text>?
Es el componente único para mostrar texto. En React Native, **nada** que sea texto puede estar fuera de esta etiqueta.

#### ¿Qué es un <Image>?
Es el componente para mostrar fotos o ilustraciones, ya sean de internet o guardadas en tu proyecto.

```jsx
import { View, Text } from 'react-native';

const MiComponente = () => (
  <View style={{ flex: 1, backgroundColor: 'blue' }}>
    <Text style={{ color: 'white' }}>¡Hola Mundo!</Text>
  </View>
);
```

### Interacción: TouchableOpacity

#### ¿Qué es un <TouchableOpacity>?
Es un componente que hace que cualquier cosa dentro de él sea "clickeable" (presionable). Al tocarlo, se vuelve un poco transparente para avisarle al usuario que lo presionó correctamente.
Para mostrar una imagen de internet, debes especificar el **ancho y el alto** (width y height), o no se verá:

```jsx
<Image 
  source={{ uri: 'https://via.placeholder.com/150' }} 
  style={{ width: 100, height: 100 }} 
/>
```

---

## 5. Estilos y Layout con Flexbox {#estilos-flexbox}

#### ¿Qué es Flexbox?
Es el sistema de diseño que usa React Native para acomodar los elementos en la pantalla de forma automática y ordenada, sin importar el tamaño del celular.

#### ¿Qué es justifyContent?
Es una propiedad que alinea los elementos a lo largo del **eje principal** (por defecto, de arriba hacia abajo).

#### ¿Qué es alignItems?
Es una propiedad que alinea los elementos a lo largo del **eje secundario** (de izquierda a derecha).

- **flex**: Si pones `flex: 1`, el componente ocupará todo el espacio que pueda.
- **justifyContent**: Centra en el eje principal (Arriba/Abajo por defecto).
- **alignItems**: Centra en el eje secundario (Izquierda/Derecha por defecto).

### Unidades de Medida
En móviles **no usamos px**. Usamos "unidades de densidad".
- `fontSize: 18` (Sin unidades).
- `margin: 10` (Sin unidades).

---

## 5. Proyecto Práctico: Mi Perfil Personal {#proyecto-practico}

### Objetivo
Crear una pantalla que muestre tu foto, tu nombre, una descripción corta y un botón interactivo.

### Pasos Generales
1. Crear un contenedor `<View>` que ocupe toda la pantalla con `flex: 1`.
2. Centrar todo con `justifyContent` y `alignItems`.
3. Agregar una `<Image>` con bordes redondeados (Ej: `borderRadius: 50`).
4. Añadir tu nombre en un `<Text>` con estilo negrita (`fontWeight: "bold"`).
5. Crear un botón usando `<TouchableOpacity>` que muestre una alerta (`Alert.alert()`) al tocarlo.

### Resultado Final
Una tarjeta de perfil profesional visible desde tu celular.

---

## ✅ Tips de Clase

- ✅ **Camel Case**: Los estilos se escriben como `backgroundColor`, no como `background-color`.
- ✅ **Bordes**: Los bordes redondeados no necesitan "%". Usa números para mayor precisión.
- ✅ **SafeAreaView**: Evita que el texto quede debajo de la cámara o la batería.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
