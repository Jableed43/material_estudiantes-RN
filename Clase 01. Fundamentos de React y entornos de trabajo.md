# Clase 01. Fundamentos de React y entornos de trabajo

## 📚 Índice

1. [Repaso de JavaScript ES6+](#javascript-es6)
   - [let, const y variables móviles](#variables)
   - [Arrow Functions](#arrow-functions)
   - [Desestructuración de Objetos y Arreglos](#desestructuracion)
   - [Manejo de Promesas (Async/Await)](#async-await)
2. [Introducción a la Arquitectura de React](#react-arquitectura)
   - [Componentes y Props](#componentes)
   - [¿Cómo funciona React Native por dentro?](#arquitectura-teorica)
   - [Sintaxis JSX](#jsx)
   - [Virtual DOM en Mobile](#virtual-dom)
3. [Entornos de Trabajo: React Native vs Expo](#entornos-trabajo)
4. [Instalación del Kit de Desarrollo (SDK)](#instalacion)
5. [Proyecto Práctico: Mi Primer Entorno](#proyecto-practico)
6. [Resumen y Consejos de Clase](#resumen)

---

## 1. Repaso de JavaScript ES6+ {#javascript-es6}

React Native se basa 100% en JavaScript moderno. No podemos avanzar sin dominar estas herramientas:

### Variables y Scope (Alcance)

#### ¿Qué es una Variable?
Es un contenedor donde guardamos información que nuestra aplicación necesita usar más tarde (como un nombre, un número o un color).

#### ¿Qué es el Scope (Alcance)?
Es el "territorio" donde una variable vive y puede ser usada. Si una variable está dentro de una función, afuera no se conoce.

Olvidamos el `var`. El scope de bloque (`let` y `const`) es nuestro mejor amigo:

```javascript
// ✅ Usar const para valores que no cambian (referencia)
const COLOR_FEMA = "#FF5733";

// ✅ Usar let para variables mutables
let contador = 0;
contador = 1;
```

### Arrow Functions (Funciones de Flecha)

#### ¿Qué es una Función?
Es un bloque de código diseñado para realizar una tarea específica. Imaginala como una "máquina" a la que le das algo (entrada), hace un proceso y te devuelve un resultado (salida).

#### ¿Qué es una Arrow Function?
Es una forma moderna y corta de escribir funciones en JavaScript. Es vital para pasar acciones entre componentes.

```javascript
// ✅ Sintaxis moderna
const saludar = (nombre) => {
  return `Hola ${nombre}`;
};

// Forma simplificada (retorno implícito)
const suma = (a, b) => a + b;
```

### Desestructuración

#### ¿Qué es un Objeto?
Es una colección de datos relacionados (propiedades) que describen a algo (ej: un usuario con nombre, edad y ciudad).

#### ¿Qué es la Desestructuración?
Es un "atajo" para sacar datos de un objeto o una lista y guardarlos en variables individuales rápidamente.

```javascript
const usuario = { nombre: "Juan", edad: 25, ciudad: "Salta" };

// Extraer solo lo que necesito
const { nombre, ciudad } = usuario;
console.log(nombre); // "Juan"
```

### Async / Await (Asincronismo)

#### ¿Qué es la Asincronía?
Es cuando una tarea tarda tiempo en completarse (como pedir datos a internet). La app no se detiene; espera el resultado mientras sigue funcionando.

#### ¿Qué es Async / Await?
Son palabras clave que le dicen a JavaScript: "espera a que esta tarea termine antes de seguir con la siguiente línea", evitando que la pantalla se "congele".

```javascript
const obtenerDatos = async () => {
  try {
    const respuesta = await fetch("https://api.ejemplo.com/datos");
    const json = await respuesta.json();
    return json;
  } catch (error) {
    console.error("Error en la conexión");
  }
};
```

---

React Native no es una "página web que corre en un celu". Es código real de Android e iOS manipulado por React.

#### ¿Qué es un Componente?
Son las "piezas de Lego" de tu aplicación. Cada parte de la pantalla (un botón, una imagen, una lista) es un componente que puedes reutilizar.

#### ¿Qué es JSX?
Es una sintaxis que parece HTML pero corre dentro de JavaScript. Nos permite escribir cómo queremos que se vea la app de forma visual y sencilla.

#### ¿Qué son las Props (Propiedades)?
Son los "argumentos" o datos que le pasamos a un componente para que sepa qué mostrar. 
Ejemplo: `<Usuario nombre="Cacho" />` (la prop es `nombre`).

---

## 3. Entornos de Trabajo {#entornos-trabajo}

#### ¿Qué es Expo?
Es un conjunto de herramientas y servicios construidos sobre React Native que hace que el desarrollo sea mucho más fácil y rápido. ¡Es el estándar para aprender y crear MVPs!

#### ¿Qué es React Native CLI?
Es la forma "manual" de trabajar con React Native. Requiere instalar herramientas pesadas como Android Studio y Xcode.

| Característica | **Expo** (Recomendado) | **React Native CLI** |
|----------------|-----------------------|---------------------|
| Dificultad | ⭐ (Fácil) | ⭐⭐⭐ (Difícil) |
| Herramientas | SDK Completo, Expo Go | Herramientas nativas de Android/Apple |
| Setup | 5 minutos | 2-3 horas |
| Ideal para | MVP, Portfolio, Aprendizaje | Apps con requerimientos nativos muy oscuros |

---

## 4. Instalación del Entorno {#instalacion}

#### ¿Qué es Node.js?
Es el "motor" que permite ejecutar JavaScript en tu computadora (fuera del navegador). Es necesario para que todas nuestras herramientas de desarrollo funcionen.

Para trabajar hoy necesitamos:
1. **Node.js** (v18 o +).
2. **VS Code**.
3. **Expo Go** (App en tu celular real).

Comando para iniciar un proyecto hoy mismo:
```bash
npx create-expo-app MiGranApp
cd MiGranApp
npx expo start
```

---

## 5. Proyecto Práctico: Mi Primer Entorno {#proyecto-practico}

### Objetivo
Configurar tu equipo y visualizar tu primera pantalla en el celular físico o emulador.

### Pasos Generales
1. Verificar instalaciones previas (`node -v`).
2. Crear un proyecto usando `npx create-expo-app`.
3. Abrir la carpeta del proyecto en VS Code.
4. Ejecutar el servidor de desarrollo (`npx expo start`).
5. Abrir la app en tu celular personal escaneando el código QR.

### Resultado Final
Verás una pantalla con el texto "Open up App.js to start working on your app!".

---

## ✅ Consejos de Clase

- ✅ **Camel Case**: En React/React Native, los estilos y propiedades usan mayúsculas intermedias (`backgroundColor`).
- ✅ **Importes**: Si algo no funciona, revisa que hayas importado el componente desde `'react-native'`.
- ✅ **Consola**: Usa `console.log()` para ver qué está pasando por "detrás" de la pantalla.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
