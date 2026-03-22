# Clase 01. Fundamentos de React y entornos de trabajo

## 📚 Índice

1. [Repaso de JavaScript ES6+](#javascript-es6)
   - [let, const y variables móviles](#variables)
   - [Arrow Functions](#arrow-functions)
   - [Desestructuración de Objetos y Arreglos](#desestructuracion)
   - [Manejo de Promesas (Async/Await)](#async-await)
2. [Introducción a la Arquitectura de React](#react-arquitectura)
   - [Componentes y Props](#componentes)
   - [Sintaxis JSX](#jsx)
   - [Virtual DOM en Mobile](#virtual-dom)
3. [Entornos de Trabajo: React Native vs Expo](#entornos-trabajo)
4. [Instalación del Kit de Desarrollo (SDK)](#instalacion)
5. [Proyecto Práctico: Mi Primer Entorno](#proyecto-practico)
6. [Resumen y Consejos de Clase](#resumen)

---

## 1. Repaso de JavaScript ES6+ {#javascript-es6}

React Native se basa 100% en JavaScript moderno. No podemos avanzar sin dominar estas herramientas:

### Variables y Scope
Olvidamos el `var`. El scope (alcance) de bloque es nuestro mejor amigo:

```javascript
// ✅ Usar const para valores que no cambian (referencia)
const COLOR_FEMA = "#FF5733";

// ✅ Usar let para variables mutables
let contador = 0;
contador = 1;
```

### Arrow Functions
Son vitales para pasar funciones como props:

```javascript
// ✅ Sintaxis moderna
const saludar = (nombre) => {
  return `Hola ${nombre}`;
};

// Forma simplificada (retorno implícito)
const suma = (a, b) => a + b;
```

### Desestructuración
Manejaremos muchos objetos de configuración y estilos. Esta sintaxis es clave:

```javascript
const usuario = { nombre: "Juan", edad: 25, ciudad: "Salta" };

// Extraer solo lo que necesito
const { nombre, ciudad } = usuario;
console.log(nombre); // "Juan"
```

### Async / Await
Para conectarnos a APIs (Clase 05 en adelante), entenderemos cómo esperar datos sin "congelar" la pantalla:

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

## 2. Arquitectura de React {#react-arquitectura}

React Native no es una "página web que corre en un celu". Es código real de Android e iOS manipulado por React.

- **JSX**: Escribimos algo que parece HTML pero se convierte en botones reales de Android/iOS.
- **Props**: Son los atributos que enviamos. Ej: `<Usuario nombre="Cacho" />`.
- **Componentes**: Son las piezas de Lego de tu app.

---

## 3. Entornos de Trabajo {#entornos-trabajo}

| Característica | **Expo** (Recomendado) | **React Native CLI** |
|----------------|-----------------------|---------------------|
| Dificultad | ⭐ (Fácil) | ⭐⭐⭐ (Difícil) |
| Herramientas | SDK Completo, Expo Go | Herramientas nativas de Android/Apple |
| Setup | 5 minutos | 2-3 horas |
| Ideal para | MVP, Portfolio, Aprendizaje | Apps con requerimientos nativos muy oscuros |

---

## 4. Instalación del Entorno {#instalacion}

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
