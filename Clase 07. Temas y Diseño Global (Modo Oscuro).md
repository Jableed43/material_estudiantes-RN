# Clase 07. Temas y Diseño Global (Modo Oscuro)

## 📚 Índice

1. [Teoría: Design Tokens (Átomos del estilo)](#design-tokens)
2. [Teoría: Context API (Pase libre de información)](#context-api-teoria)
3. [¿Qué es un Tema Global?](#introducción)
4. [Creando una Paleta de Colores (Claro vs Oscuro)](#paleta-de-colores)
5. [Implementación: El ThemeProvider](#implementación-de-theming-con-context-api)
6. [Consumiendo el tema en tus componentes](#consumir-el-tema-en-componentes)
7. [Organización de Archivos](#organización-de-estilos)
8. [Proyecto Práctico: App Multi-Tema](#proyecto-práctico-aplicar-theming-a-la-app-de-usuarios)
9. [Buenas Prácticas](#buenas-prácticas-con-theming)

---

## 1. Teoría: Design Tokens {#design-tokens}

#### ¿Qué es un Design Token?
Son los "átomos" o las piezas irreductibles de tu diseño (como un color específico o un tamaño de letra). En vez de decir "usa el color rojo", dices "usa el token `error`".

Imagina que tu app tiene 100 pantallas y el cliente quiere cambiar el color "Primario". 
- **Mala práctica**: Ir archivo por archivo cambiando el código del color `#FF5733`.
- **Buena práctica (Tokens)**: Creamos una variable llamada `primary` y la usamos en toda la app. Si el color cambia, solo tocamos **un archivo** y la magia sucede en las 100 pantallas. Esto es el corazón de un **Design System**.

## 2. Teoría: Context API {#context-api-teoria}

#### ¿Qué es el Prop Drilling?
Es el problema de pasar información a través de muchos componentes que no la necesitan, solo para que llegue a un componente que está muy al fondo del árbol.

#### ¿Qué es Context API?
Es como un **túnel directo** o un canal de radio. El Emisor (Provider) manda la información y CUALQUIER componente, por más lejos que esté, puede "sintonizar" ese canal y recibir los datos sin molestar a los componentes del medio.

---

## 1. Introducción al Theming {#introducción}

Un **Theme** (tema) es el ADN visual de tu aplicación. Centraliza colores, tipografías y espaciados para que no tengas que escribir `#FF5533` en cada archivo. Si decides cambiar el color principal de la marca, lo haces en un solo lugar y toda la app se actualiza.

---

## 2. Context API {#context-api}

#### ¿Qué es un Provider (Proveedor)?
Es el componente que "envuelve" a los demás y les permite acceder a la información compartida. Es quien tiene la autoridad sobre los datos.

#### ¿Qué es un Hook de Contexto (useContext)?
Es la herramienta que usa cada componente para "pedir" permiso y leer la información que el Provider está emitiendo.

---

## 3. Paleta de Colores {#paleta-de-colores}

#### ¿Qué es el Modo Oscuro (Dark Mode)?
Es una versión de tu diseño donde se usan colores oscuros para el fondo y claros para el texto, lo que cansa menos la vista y ahorra batería en pantallas OLED.

---

## 4. El ThemeProvider {#implementación-de-theming-con-context-api}

Es el componente "padre" que maneja el estado.
```tsx
export function ThemeProvider({ children }) {
  const [isDark, setIsDark] = useState(false);
  const colors = isDark ? darkColors : lightColors;

  return (
    <ThemeContext.Provider value={{ isDark, colors, toggleTheme: () => setIsDark(!isDark) }}>
      {children}
    </ThemeContext.Provider>
  );
}
```

---

## 5. Consumiendo el tema {#consumir-el-tema-en-componentes}

En cualquier pantalla de tu app, usas el hook **`useTheme`**:
```tsx
const { colors } = useTheme();

return (
  <View style={{ backgroundColor: colors.background }}>
    <Text style={{ color: colors.text }}>Hola!</Text>
  </View>
);
```

---

## 6. Organización de Archivos {#organización-de-estilos}

Recomendamos esta estructura:
- `constants/theme.ts`: Solo los códigos de colores.
- `context/ThemeContext.tsx`: La lógica del Provider y el Hook.
- `app/_layout.tsx`: Donde envuelves toda la navegación con el Provider.

---

## 7. Proyecto Práctico: App Multi-Tema {#proyecto-práctico-aplicar-theming-a-la-app-de-usuarios}

Tomaremos la app de la clase anterior y:
1. Crearemos el sistema de temas.
2. Agregaremos un botón de 🌙/☀️ en el encabezado.
3. Configuraremos el **StatusBar** para que cambie de color automáticamente.

---

## ✅ Buenas Prácticas

- ✅ **No hardcodees colores**: Si usas `#000` directamente, el modo oscuro no funcionará.
- ✅ **Nombres Claros**: Usa `textSecondary` para grises que deben verse en ambos temas.
- ✅ **StatusBar**: Recuerda que si el fondo es oscuro, los iconos de batería/hora deben ser blancos (`light`).

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
