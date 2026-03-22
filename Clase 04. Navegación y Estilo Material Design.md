# Clase 04. Navegación y Lineamientos de Material Design

## 📚 Índice

1. [Introducción](#introducción)
2. [React Navigation: El Estándar](#react-navigation)
   - [¿Qué es React Navigation?](#qué-es-react-navigation)
   - [Tipos de Navegadores y Cuándo Usarlos](#tipos-de-navegadores)
3. [Instalación de Dependencias](#instalación-de-dependencias)
4. [Configuración con Expo Router](#configuración-expo-router)
5. [Material Design 3](#material-design)
   - [Principios de Diseño](#principios-de-material-design)
   - [React Native Paper](#react-native-paper)
6. [Estructura de Proyecto Recomendada](#estructura-de-carpetas)
7. [Manejo de Temas (Context API)](#context-api-para-tema)
8. [Áreas Seguras (SafeAreaView)](#safeareaview-y-statusbar)
9. [Proyecto Práctico: App con Navegación](#proyecto-práctico-app-con-navegación)
10. [Buenas Prácticas](#buenas-prácticas)

---

## 1. Introducción {#introducción}

En esta clase aprenderemos a implementar navegación profesional y a aplicar los principios de **Material Design 3** para que nuestras apps se vean modernas y coherentes.

---

## 2. React Navigation: El Estándar {#react-navigation}

**React Navigation** es la biblioteca oficial/estándar para movernos entre pantallas en React Native.

### Tipos de Navegadores {#tipos-de-navegadores}

| Navegador | Uso | Ejemplo |
|-----------|-----|---------|
| **Stack** | Pila de pantallas (LIFO) | Lista → Detalle |
| **Tabs** | Barra inferior/superior | Inicio, Perfil, Ajustes |
| **Drawer** | Menú lateral deslizable | Configuraciones avanzadas |

---

## 3. Instalación de Dependencias {#instalación-de-dependencias}

Para que todo funcione (gestos, animaciones, áreas seguras), necesitamos varios paquetes:

```bash
npx expo install @react-navigation/native @react-navigation/native-stack @react-navigation/bottom-tabs react-native-screens react-native-gesture-handler react-native-safe-area-context react-native-reanimated react-native-paper @expo/vector-icons expo-status-bar
```

---

## 4. Configuración con Expo Router {#configuración-expo-router}

**⚠️ MUY IMPORTANTE:** Si usas Expo Router (la carpeta `app/`), **NO** agregues el componente `<NavigationContainer>`. Expo ya lo trae puesto "por detrás". Si lo pones tú, la app dará un error de "nested NavigationContainer".

---

## 5. Material Design 3 {#material-design}

Es el sistema de diseño de Google. Buscamos:
- **Jerarquía**: Que lo importante resalte.
- **Elevación**: Sombras para separar elementos.
- **Feedback**: Que el botón reaccione al tocarlo.

### React Native Paper
Es la librería que ya trae los botones, cards y menús de Material Design listos para usar:
```tsx
import { Button, Card, Text } from 'react-native-paper';

<Card>
  <Card.Content>
    <Text variant="titleLarge">Producto</Text>
    <Button mode="contained">Comprar</Button>
  </Card.Content>
</Card>
```

---

## 6. Estructura de Proyecto Recomendada {#estructura-de-carpetas}

Organiza tu código para que no sea un caos:
```text
app/
  ├── context/    # Estado global (ej: Tema oscuro)
  ├── navigation/ # Configuración de Stacks/Tabs
  ├── screens/    # Tus pantallas (Home, Login, etc.)
  ├── styles/     # Colores y fuentes compartidas
  └── theme/      # Definición de colores Material
```

---

## 7. Manejo de Temas (Context API) {#context-api-para-tema}

Usamos **Context API** para que toda la app sepa si estamos en modo oscuro o claro sin tener que pasar "props" de pantalla en pantalla.

---

## 8. Áreas Seguras (SafeAreaView) {#safeareaview-y-statusbar}

Los teléfonos modernos tienen "notches" (agujeros de cámara) y barras de navegación en la parte inferior.
- Usa **`SafeAreaView`** para que tu contenido no quede tapado por el reloj o la cámara.
- **StatusBar**: Configúralo para que sea blanco en modo oscuro y negro en modo claro.

---

## 9. Proyecto Práctico: App con Navegación {#proyecto-práctico-app-con-navegación}

Crearemos una app que tenga:
1. Una barra inferior (**Tabs**) para "Inicio" y "Perfil".
2. Dentro de "Inicio", un **Stack** para ir de una lista de productos a los detalles de cada uno.
3. Componentes de **React Native Paper** (Cards para los productos).

---

## ✍️ Buenas Prácticas

- ✅ **Múltiplos de 8**: Usa márgenes y paddings de 8, 16, 24, 32... así todo se ve alineado.
- ✅ **Tipo de Navegador**: No uses Drawer si solo tienes 2 pantallas; mejor usa Tabs.
- ✅ **Feedback**: Siempre usa `TouchableOpacity` o botones de Paper para que el usuario sepa que "clickeó" correctamente.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
