# Clase 01. Fundamentos de React y Entornos de Trabajo

## 📚 Índice

1. [Repaso de JavaScript Moderno](#repaso-de-javascript-moderno)
   - [Variables y Scope](#variables-y-scope)
   - [Arrow Functions](#arrow-functions)
   - [Template Literals](#template-literals)
   - [Destructuring](#destructuring)
   - [Array Methods](#array-methods)
   - [Promises y Async/Await](#promises)
2. [Conceptos Esenciales de React](#conceptos-esenciales-de-react)
   - [Componentes](#componentes)
   - [JSX en React](#jsx)
3. [Preparación para React Native](#preparacion-react-native)
4. [Proyecto Práctico: Mi Primer Entorno](#proyecto-practico)
5. [Buenas Prácticas](#buenas-practicas)
6. [Resumen](#resumen)

---

## 1. Repaso de JavaScript Moderno {#repaso-de-javascript-moderno}

### 🛠️ Variables y Scope {#variables-y-scope}

**Las variables son la base de cualquier programa, permitiéndonos guardar información para usarla después.**

#### ¿Qué es una Variable?

Una **variable** es como una etiqueta que le pones a una pequeña caja en la memoria de tu computadora. En esa caja guardas un valor (un número, un nombre, una lista de cosas) y usas la etiqueta para encontrarlo rápidamente.

**Para qué sirve:**
- **Organización**: No tienes que recordar números largos o textos complejos, solo usas el nombre de la variable.
- **Reutilización**: Puedes usar el mismo dato en muchas partes de tu código sin volver a escribirlo.
- **Cambio**: Permite que tu programa sea dinámico (la puntuación de un juego, el nombre de un usuario logueado).

#### ¿Qué es el Scope (Ámbito)?

El **scope** determina la "zona de visibilidad" de una variable. Es decir, en qué parte de tu código puedes usar esa etiqueta.

**Tipos de Scope:**
- **Global**: La variable se ve en todo el archivo.
- **Block (Bloque)**: La variable solo existe dentro de las llaves `{ }` donde fue creada (como dentro de un `if` o un `for`).

#### `let` vs `const`

```javascript
// ✅ Usar const para valores que NO van a cambiar (el 90% de las veces)
const nombreApp = "Mi App React";

// ✅ Usar let para valores que SÍ van a cambiar
let puntaje = 0;
puntaje = 10; // Permitido
```

**⚠️ Nota Importante:** Evita usar `var`. Es una forma antigua de declarar variables que suele causar errores inesperados debido a su scope menos restrictivo.

---

### 📚 Arrow Functions {#arrow-functions}

#### ¿Qué son las Arrow Functions?

Son una forma moderna y corta de escribir funciones en JavaScript. Se llaman así por el símbolo de la flecha `=>`.

**Para qué sirven:**
- **Código más limpio**: Menos palabras clave como `function` y `return`.
- **Contexto automático**: Mantienen mejor el sentido de `this`, lo cual es vital cuando trabajamos con componentes de React.

#### Ejemplo Comparativo

```javascript
// Forma tradicional
function saludar(nombre) {
  return "Hola " + nombre;
}

// Forma moderna (Arrow Function)
const saludar = (nombre) => `Hola ${nombre}`;
```

---

### 📝 Template Literals {#template-literals}

Permiten insertar variables dentro de un texto usando las comillas invertidas (backticks) `` ` `` y el símbolo `${variable}`.

```javascript
const usuario = "Juan";
console.log(`Bienvenido, ${usuario}!`); 
```

---

### 🔗 Destructuring {#destructuring}

#### ¿Qué es el Destructuring?

Es una técnica para "desarmar" objetos o listas y sacar solo lo que necesitamos de forma directa.

**Para qué sirve:**
- **Legibilidad**: El código se entiende mucho más rápido.
- **Efficiency**: Evita escribir `usuario.nombre`, `usuario.edad`, etc., muchas veces.

```javascript
const usuario = { nombre: "Ana", edad: 25, ciudad: "Mendoza" };

// Sin destructuring
const nombre = usuario.nombre;
const edad = usuario.edad;

// CON destructuring (Mucho mejor)
const { nombre, edad } = usuario;
```

---

### 📦 Array Methods {#array-methods}

Los métodos de arrays nos permiten manipular listas de datos de forma elegante:
- **map()**: Crea una nueva lista transformando cada elemento.
- **filter()**: Crea una lista solo con los elementos que cumplen una condición.

```javascript
const numeros = [1, 2, 3];
const dobles = numeros.map(n => n * 2); // [2, 4, 6]
```

---

### ⏳ Promises y Async/Await {#promises}

Sirven para manejar tareas que llevan tiempo (como pedir datos a internet). `await` hace que el código espere a que la tarea termine para seguir.

```javascript
const pedirDatos = async () => {
  const respuesta = await fetch('https://api.com');
  const datos = await respuesta.json();
  console.log(datos);
};
```

---

## 2. Conceptos Esenciales de React {#conceptos-esenciales-de-react}

### 🧩 Componentes {#componentes}

**React se basa en la idea de que todo en la interfaz es un componente.**

Un **componente** es como una pieza de LEGO. Cada pieza tiene su propia forma y función, y al unirlas todas, construyes una aplicación completa.

**Para qué sirven:**
- **Dividir y Vencer**: Separas la interfaz en partes pequeñas y fáciles de arreglar.
- **Reutilizar**: Creas un botón una vez y lo usas en 20 pantallas diferentes.

#### Ejemplo de Componente Botón

```javascript
const MiBoton = ({ titulo, color }) => {
  return (
    <button style={{ backgroundColor: color }}>
      {titulo}
    </button>
  );
};
```

---

### 💎 JSX en React {#jsx}

#### ¿Qué es JSX?

Es una mezcla entre JavaScript y HTML. Te permite escribir la estructura de tu app de forma visualmente similar a una página web, pero con todo el poder de la programación.

**Reglas de Oro:**
1. **Un solo padre**: Todo componente debe devolver un único elemento contenedor (o usar un Fragment `<> ... </>`).
2. **CamelCase**: En lugar de `onclick` usamos `onClick`, en lugar de `class` usamos `className`.

---

## 3. Preparación para React Native {#preparacion-react-native}

**React Native usa los mismos conceptos que React, pero con piezas diferentes.**

| En la Web usamos... | En React Native usaremos... |
|---------------------|-----------------------------|
| `<div>`             | `<View>`                    |
| `<span>` o `<p>`    | `<Text>`                    |
| `<img>`             | `<Image>`                   |
| `onclick`           | `onPress`                   |

---

## 4. Proyecto Práctico: Mi Primer Entorno {#proyecto-practico}

### Objetivo
Configurar las herramientas necesarias y crear tu primer proyecto para verificar que todo funcione correctamente.

### Componentes/Conceptos a Aplicar
- **Node.js**: Instalación del motor.
- **NPM/NPX**: Gestión de paquetes.
- **Git**: Control de versiones básico.

### Pasos Generales
1. **Instalar Node.js**: Descargar la versión LTS desde nodejs.org.
2. **Verificar Versión**: Abrir terminal y escribir `node -v` y `npm -v`.
3. **Instalar VS Code**: El editor recomendado para React Native.
4. **Instalar Extensiones**: `ES7+ React/Redux/React-Native snippets`.
5. **Crear Proyecto Demo**: Ejecutar `npx create-expo-app MiPrimerProyecto`.

---

## ✅ Buenas Prácticas {#buenas-practicas}

- **Usa const por defecto**: Si no sabes si va a cambiar, usa `const`. Si luego necesitas cambiarlo, pásalo a `let`.
- **Nombres descriptivos**: En lugar de `x`, usa `puntajeUsuario`.
- **Componentes Pequeños**: Si un componente tiene más de 100 líneas, probablemente deberías dividirlo en dos.
- **Comenta tu código**: Explica el "por qué" de las cosas complejas, no el "qué".

---

## 📝 Resumen {#resumen}

### Conceptos Clave Aprendidos
1. **JavaScript ES6+**: Variables modernas, funciones flecha y desestructuración.
2. **React DNA**: Componentes y JSX como base de la interfaz.
3. **Entorno**: Node.js y NPM son fundamentales para cualquier proyecto moderno.

### Próximos Pasos
- Asegúrate de tener Node.js instalado.
- Crea tu primer proyecto con Expo y explora las carpetas.
- ¡Prepárate para la próxima clase donde crearemos nuestra primera pantalla móvil!

---

**Última actualización:** Marzo 2026 - Guía para estudiantes React Native.
