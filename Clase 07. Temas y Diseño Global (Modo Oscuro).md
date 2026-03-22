# Clase 07. Temas y Diseño Global (Modo Oscuro)

## 📚 Índice

1. [Introducción al Theming](#introducción)
2. [Context API: Compartir datos en toda la app](#context-api)
3. [Creando una Paleta de Colores (Claro vs Oscuro)](#paleta-de-colores)
4. [Implementación: El ThemeProvider](#implementación-de-theming-con-context-api)
5. [Consumiendo el tema en tus componentes](#consumir-el-tema-en-componentes)
6. [Organización de Archivos](#organización-de-estilos)
7. [Proyecto Práctico: App Multi-Tema](#proyecto-práctico-aplicar-theming-a-la-app-de-usuarios)
8. [Buenas Prácticas](#buenas-prácticas-con-theming)

---

## 1. Introducción al Theming {#introducción}

Un **Theme** (tema) es el ADN visual de tu aplicación. Centraliza colores, tipografías y espaciados para que no tengas que escribir `#FF5533` en cada archivo. Si decides cambiar el color principal de la marca, lo haces en un solo lugar y toda la app se actualiza.

---

## 2. Context API {#context-api}

Para que todos los componentes (botones, textos, fondos) sepan si deben ser blancos o negros, usamos **Context API**.
- **createContext**: Crea el "canal" de comunicación.
- **Provider**: El "emisor" que rodea toda la app.
- **useContext**: El "receptor" que usa cada componente para leer el tema.

---

## 3. Paleta de Colores {#paleta-de-colores}

No uses nombres como `azul` o `rojo`. Usa **nombres semánticos**:
- `primary`: El color de tus botones principales.
- `background`: El fondo de la pantalla.
- `text`: El color de las letras.
- `error`: Para mensajes de alerta.

Así, en el **Modo Oscuro**, `background` será negro y `text` será blanco, pero el nombre de la variable sigue siendo el mismo.

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
