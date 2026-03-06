# Clase 07. Temas y Diseño Global (Modo Oscuro)

## 📚 Índice

1. [¿Qué es un Theme (Tema)?](#que-es-theme)
2. [Context API: Compartir sin complicarse](#context-api)
   - [¿Para qué sirve?](#para-que)
   - [Provider y Consumer](#componentes)
3. [Paleta de Colores Profesional](#colores)
4. [Implementando el Modo Oscuro global](#implementacion)
5. [Proyecto Práctico: App con Colores Inteligentes](#proyecto-practico)
6. [Buenas Prácticas](#buenas-practicas)
7. [Resumen](#resumen)

---

## 1. ¿Qué es un Theme (Tema)? {#que-es-theme}

Un **Theme** es el manual de estilo de tu app. En lugar de decir "este botón es azul" en 20 archivos diferentes, dices "el color primario de mi app es azul" en **un solo lugar**.

**Ventajas:**
- **Consistencia**: Toda la app se ve igual.
- **Fácil cambio**: Si quieres pasar de azul a verde, lo cambias en un segundo.
- **Modo Oscuro**: Es la forma correcta de intercambiar entre blanco y negro.

---

## 2. Context API: Compartir sin complicarse {#context-api}

### ¿Para qué sirve? {#para-que}
Imagina que tienes una caja con la configuración del "Modo Oscuro". Sin Context API, tendrías que pasar esa caja de mano en mano por cada pantalla de la app (**Prop Drilling**).
Con **Context API**, la caja flota sobre la app y cualquier pantalla puede tomarla cuando quiera.

### Componentes clave {#componentes}
- **Provider (Proveedor)**: Es quien tiene la información y la reparte.
- **useContext (Consumidor)**: Es el hook que usamos en cada pantalla para "leer" la información.

---

## 3. Paleta de Colores Profesional {#colores}

No uses nombres como `rojo` o `azul`. Usa nombres de **función**:
- **Primary**: Para botones principales.
- **Background**: Para el fondo de la pantalla.
- **Surface**: Para tarjetas (cards).
- **Error**: Para mensajes de alerta.

---

## 4. Implementando el Modo Oscuro global {#implementacion}

Para que tu app cambie de color en todas las pantallas al mismo tiempo, sigue este flujo:

1. **Crear el Contexto**: `const ThemeContext = createContext()`.
2. **Proveerlo**: En el archivo raíz (`_layout.tsx`), envuelve todo en `<ThemeContext.Provider value={{...}}>`.
3. **Usarlo**: En tus pantallas, usa `const { colors } = useTheme()`.

---

## 5. Proyecto Práctico: App con Colores Inteligentes {#proyecto-practico}

### Objetivo
Hacer que tu app de usuarios cambie de color automáticamente al presionar un botón de "Sol/Luna".

### Pasos
1. **Definir colores**: Crea un archivo `theme.ts` con un objeto para `light` y otro para `dark`.
2. **Contexto**: Crea el `ThemeProvider` que cambie de uno a otro.
3. **Estilos**: En tus componentes, no escribas `color: 'white'`. Escribe `color: colors.text`.

---

## ✅ Buenas Prácticas {#buenas-practicas}

- **Nunca hardcodees colores**: Si escribes `#FFFFFF` en un componente, estás rompiendo el modo oscuro. Usa siempre el theme.
- **Usa un Hook personalizado**: Crea un hook llamado `useTheme()` para que sea más fácil de usar en tus pantallas.
- **StatusBar**: Recuerda que si el fondo es negro, las letras del reloj de tu celular deben ser blancas. ¡Cambia el `StatusBar` también!

---

## 📝 Resumen {#resumen}

### Conceptos Clave Aprendidos
1. **Theming**: Estilos centralizados.
2. **Context API**: La nube de datos de tu app.
3. **Prop Drilling**: Lo que queremos evitar (pasar datos innecesariamente).

### Próximos Pasos
- ¿Ya definiste tu paleta de colores? ¡Intenta buscar paletas en [Adobe Color](https://color.adobe.com)!
- Asegúrate de que los textos tengan suficiente contraste para que se puedan leer bien.

---

**Última actualización:** Marzo 2026 - Guía para estudiantes.
