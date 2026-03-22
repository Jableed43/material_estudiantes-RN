# Clase 04. Navegación y Lineamientos de Material Design

## 📚 Índice

1. [Introducción](#introducción)
2. [React Navigation: El Estándar](#react-navigation)
   - [Teoría: La Pila (Stack) de Pantallas](#teoria-stack)
   - [Introducción a la Navegación (React Navigation)](#react-navigation)
   - [Tipos de Navegadores (Stack, Tabs, Drawer)](#tipos-navegadores)
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

## 1. Teoría: La Navegación y la Pila (Stack) {#teoria-stack}

#### ¿Qué es la Navegación?
Es el sistema que permite al usuario moverse entre diferentes pantallas de la aplicación de forma fluida y organizada.

#### ¿Qué es la Pila (Stack) de Pantallas?
A diferencia de las pestañas de un navegador web, las apps funcionan como una **Pila de platos**.
- `Push` (Empujar): Cuando presionas un botón para ir a "Detalle", pones un plato nuevo encima del anterior.
- `Pop` (Sacar): Cuando presionas "Volver", quitas el plato de arriba y el anterior vuelve a ser visible.

**Concepto Clave**: Si pusheas 5 veces la misma pantalla, tendrás 5 copias en memoria. ¡Cuidado con no llenar la pila innecesariamente!

---

## 1. Introducción {#introducción}

En esta clase aprenderemos a implementar navegación profesional y a aplicar los principios de **Material Design 3** para que nuestras apps se vean modernas y coherentes.

---

## 2. React Navigation: El Estándar {#react-navigation}

#### ¿Qué es React Navigation?
Es la biblioteca oficial y más usada para manejar la navegación en React Native. Nos permite crear flujos de pantallas, menús y pestañas de forma sencilla.

### Tipos de Navegadores

#### ¿Qué es un Stack Navigator? (Pila)
Es el que usamos para ir "hacia adelante" y "hacia atrás". Ejemplo: De una lista de productos al detalle de uno.

#### ¿Qué es un Tab Navigator? (Pestañas)
Es la barra (usualmente abajo) que tiene varios botones para saltar entre las secciones principales de la app (Inicio, Buscar, Perfil).

#### ¿Qué es un Drawer Navigator? (Lateral)
Es el menú que sale del costado cuando deslizas el dedo o tocas un ícono de "hamburguesa".

---

## 3. Instalación de Dependencias {#instalación-de-dependencias}

#### ¿Qué es una Dependencia?
Es un paquete de código escrito por otros desarrolladores que añadimos a nuestro proyecto para no tener que programar todo desde cero (ejemplo: el sistema de navegación).

```bash
npx expo install @react-navigation/native @react-navigation/native-stack @react-navigation/bottom-tabs react-native-screens react-native-gesture-handler react-native-safe-area-context react-native-reanimated react-native-paper @expo/vector-icons expo-status-bar
```

---

## 4. Configuración con Expo Router {#configuración-expo-router}

**⚠️ MUY IMPORTANTE:** Si usas Expo Router (la carpeta `app/`), **NO** agregues el componente `<NavigationContainer>`. Expo ya lo trae puesto "por detrás". Si lo pones tú, la app dará un error de "nested NavigationContainer".

---

## 5. Material Design 3 {#material-design}

#### ¿Qué es Material Design?
Es un sistema de diseño creado por Google que propone reglas visuales (colores, sombras, animaciones) para que las apps sean intuitivas y estéticamente agradables en cualquier dispositivo.

#### ¿Qué es React Native Paper?
Es una librería de componentes que ya vienen diseñados siguiendo las reglas de Material Design. Nos permite usar botones, tarjetas y diálogos "lindos" con una sola línea de código.
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

#### ¿Qué es Context API?
Es una herramienta de React que permite compartir información (como si la app está en modo oscuro o claro) entre todos los componentes, sin tener que pasarla "mano a mano" de padre a hijo.

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
