# Clase 04. Navegación y Estilo Material Design

## 📚 Índice

1. [¿Qué es la Navegación?](#navegacion)
2. [Tipos de Navegadores](#tipos)
   - [Stack (Pila)](#stack)
   - [Tabs (Pestañas)](#tabs)
   - [Drawer (Cajón)](#drawer)
3. [Instalación de Librerías](#instalacion)
4. [Material Design: El diseño profesional](#material-design)
   - [¿Qué es?](#que-es-md)
   - [React Native Paper](#paper)
5. [Proyecto Práctico: App con Menú](#proyecto-practico)
6. [Buenas Prácticas](#buenas-practicas)
7. [Resumen](#resumen)

---

## 1. ¿Qué es la Navegación? {#navegacion}

En una app, no todo sucede en una sola pantalla. La **navegación** es el sistema que nos permite movernos de una pantalla a otra (por ejemplo, de la lista de productos al detalle de uno).

Usaremos la librería estándar: **React Navigation**.

---

## 2. Tipos de Navegadores {#tipos}

### 📚 Stack Navigator (Pila) {#stack}
Es el más común. Las pantallas se ponen una encima de otra.
- **Uso**: Para ir a "Detalles" o "Configuración". Cuando vas atrás, quitas la de arriba y ves la anterior.

### 📱 Tab Navigator (Pestañas) {#tabs}
Los botones que ves abajo en apps como Instagram o WhatsApp.
- **Uso**: Para las secciones principales de la app que quieres tener siempre a mano.

### 🗄️ Drawer Navigator (Cajón lateral) {#drawer}
Un menú que sale de un costado.
- **Uso**: Para opciones secundarias que no caben abajo o que no usas todo el tiempo.

---

## 3. Instalación {#instalacion}

Para que la navegación funcione, necesitamos varias piezas. Ejecuta este comando (todo junto):

```bash
npx expo install @react-navigation/native @react-navigation/native-stack @react-navigation/bottom-tabs react-native-screens react-native-gesture-handler react-native-safe-area-context react-native-reanimated react-native-paper @expo/vector-icons
```

---

## 4. Material Design: El diseño profesional {#material-design}

### ✨ ¿Qué es? {#que-es-md}
Es un conjunto de reglas creado por Google para que las aplicaciones se vean limpias, usen sombras realistas y colores que combinan bien. Ayuda a que el usuario sepa qué es un botón y qué es solo texto.

### 🧩 React Native Paper {#paper}
Es una librería de componentes que ya siguen las reglas de Material Design. En lugar de crear un botón desde cero, usas un `<Button>` de Paper que se ve profesional de inmediato.

| Componente | Para qué sirve |
|------------|----------------|
| **Card**   | Para mostrar información en "tarjetas" con sombra. |
| **FAB**    | El botón flotante redondo (como el de "Nuevo Mensaje"). |
| **Appbar** | La barra de arriba con el título de la app. |

---

## 5. Proyecto Práctico: App con Menú {#proyecto-practico}

### Objetivo
Crear una app que tenga una pantalla de Inicio y una de Perfil, navegables mediante botones abajo (Tabs).

### Pasos Generales
1. **Configurar el Layout**: En `_layout.tsx`, define qué pantallas tendrá tu menú.
2. **Crear Pantallas**: Haz dos archivos, `index.tsx` (Inicio) y `profile.tsx` (Perfil).
3. **Usar Paper**: Agrega una `Card` en Inicio para mostrar una bienvenida.
4. **Navegar**: Agrega un botón que use `navigation.navigate('Profile')` para saltar de una a otra.

---

## ✅ Buenas Prácticas {#buenas-practicas}

- **No anides demasiado**: No metas un Stack dentro de un Stack dentro de un Tab. Trata de que la navegación sea simple para el usuario.
- **Iconos claros**: Usa iconos de `@expo/vector-icons` que el usuario reconozca fácilmente (una casita para inicio, un engranaje para ajustes).
- **Espaciado Mágico**: En Material Design se usa mucho el múltiplo de 8. Si necesitas margen, usa 8, 16, 24 o 32. Evita números "raros" como 13 o 17.

---

## 📝 Resumen {#resumen}

### Conceptos Clave Aprendidos
1. **React Navigation**: El motor que mueve las pantallas.
2. **Tabs y Stacks**: Las formas de organizar nuestras pantallas.
3. **Material Design**: La guía para que nuestra app se vea increíble.

### Próximos Pasos
- Experimenta cambiando los iconos de tus pestañas abajo.
- Intenta crear una pantalla de "Detalles" que se abra encima de la actual usando un Stack.

---

**Última actualización:** Marzo 2026 - Guía para estudiantes.
