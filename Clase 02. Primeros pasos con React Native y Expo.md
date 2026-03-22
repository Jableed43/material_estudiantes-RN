# Clase 02. Primeros pasos con React Native y Expo

## 📚 Índice

1. [Configuración Rápida (Setup Inicial)](#setup-inicial)
2. [Entendiendo Expo y su Ecosistema](#que-es-expo)
   - [¿Por qué usar Expo Router?](#expo-router)
   - [Diferencias entre React (Web) y React Native (Mobile)](#diferencias-web-mobile)
3. [Componentes Básicos de Interfaz (UI)](#componentes-basicos)
   - [View, Text e Image](#view-text-image)
   - [Interacción con Button y TouchableOpacity](#botones)
4. [Diseño y Layout con Flexbox](#estilos-flexbox)
   - [Eje Principal y Cruzado](#ejecucion-flexbox)
   - [Unidades de Medida en Móviles](#unidades-medida)
5. [Proyecto Práctico: Mi Perfil Personal](#proyecto-practico)
6. [Resumen y Consejos de Estilo](#resumen)

---

## 1. Setup Inicial {#setup-inicial}

Para empezar hoy, configuramos todo lo necesario para programar y ver los cambios al instante.
1. Comando moderno para crear apps: `npx create-expo-app MiApp`.
2. Servidor de desarrollo: `npx expo start`.
3. Ver cambios: Escanea el código QR con la app **Expo Go** (Android) o la cámara (iOS).

⚠️ **Importante**: No instales `expo-cli` globalmente (`npm install -g`), usa siempre `npx`.

---

## 2. Diferencias clave: Web vs Mobile {#diferencias-web-mobile}

React Native no usa etiquetas HTML, usa componentes de interfaz nativos:

| Web (HTML) | Mobile (React Native) | Uso |
|------------|-----------------------|-----|
| `<div>` | `<View>` | Contenedor principal |
| `<span>` / `<p>` | `<Text>` | Para TODO el texto |
| `<img>` | `<Image>` | Fotos (locales o remotas) |
| `<a>` / `<button>` | `<TouchableOpacity>` | Para botones interactivos |

---

## 3. Componentes Básicos {#componentes-basicos}

### View y Text
En React Native, **nunca** puedes poner texto suelto. Debe estar siempre dentro de un `<Text>`.

```jsx
import { View, Text } from 'react-native';

const MiComponente = () => (
  <View style={{ flex: 1, backgroundColor: 'blue' }}>
    <Text style={{ color: 'white' }}>¡Hola Mundo!</Text>
  </View>
);
```

### Image: Un detalle importante
Para mostrar una imagen de internet, debes especificar el **ancho y el alto** (width y height), o no se verá:

```jsx
<Image 
  source={{ uri: 'https://via.placeholder.com/150' }} 
  style={{ width: 100, height: 100 }} 
/>
```

---

## 4. Estilos y Layout con Flexbox {#estilos-flexbox}

En el celu, todo es **Flexbox**. Por defecto, los elementos se apilan uno abajo del otro (`flexDirection: "column"`).

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
