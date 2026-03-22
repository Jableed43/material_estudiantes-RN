# Clase 11. Arquitectura y Experiencia de Usuario (UX)

## 📚 Índice

1. [Definiendo el Alcance de tu App](#definicion-alcance)
2. [Arquitectura Modular (Organizar carpetas como un pro)](#separacion-modulos)
3. [Flujos de Navegación Profesionales](#flujos-navegacion)
4. [La importancia de la UX (User Experience)](#animaciones-clave)
5. [Microanimaciones: El detalle que marca la diferencia](#microanimaciones-ux)
6. [Transiciones entre Pantallas Personalizadas](#transiciones-pantallas)
7. [Proyecto Práctico: App Escalable y Animada](#proyecto-practico)
8. [Resumen y Consejos de Diseño](#resumen)

---

## 1. Definiendo el Alcance {#definicion-alcance}

#### ¿Qué es el Alcance (Scope) de un proyecto?
Es la lista de todas las cosas que tu aplicación **SÍ** va a hacer y, sobre todo, las que **NO** va a hacer. Definir el alcance evita que el proyecto crezca infinitamente y nunca se termine.

#### ¿Qué es un MVP (Producto Mínimo Viable)?
Es la versión más simple y básica de tu aplicación que ya puede ser usada por alguien. No tiene todas las funciones, pero la función principal (ej: mandar un mensaje) anda perfecto.

Antes de escribir la primera línea de código, debes saber **qué va a hacer tu app**.
- **Alcance**: Es el mapa de tu proyecto. ¿Tiene login? ¿Tiene perfil? ¿Funciona sin internet?
- **MVP**: No intentes hacer el próximo Facebook en un día. Haz que la función principal funcione perfecto primero.

---

## 2. Arquitectura Modular {#separacion-modulos}

#### ¿Qué es la Arquitectura Modular?
Es la forma de organizar tu código en piezas o "módulos" independientes. En vez de tener un archivo gigante con todo, separas el login en un lado, las tareas en otro y los estilos en otro.

No pongas todos tus archivos en una sola carpeta. Organízalos por "Módulos" o "Funcionalidades":
- `src/auth/`: Todo lo relacionado con el login.
- `src/tasks/`: Todo lo relacionado con las tareas.
- `src/shared/`: Componentes que usas en todos lados (botones, inputs).

Esto hace que tu código sea fácil de leer y que no te vuelvas loco buscando un archivo.

---

## 3. Flujos de Navegación {#flujos-navegacion}

#### ¿Qué es la Navegación Condicional?
Es cuando la aplicación decide qué pantalla mostrar basándose en una condición (ejemplo: si el usuario ya puso su contraseña, mostramos el Home; si no, el Login).

Una app profesional tiene flujos claros:
1. **Splash Screen**: Cargando datos...
2. **Auth Flow**: Login o Registro.
3. **Main Flow**: La app en sí (Tabs + Stacks).

**Truco**: Usa navegación condicional. Si el usuario está logueado, muéstrale el Home. Si no, mándalo al Login automáticamente.

---

## 4. Experiencia de Usuario (UX) {#animaciones-clave}

#### ¿Qué es la UI (Interfaz de Usuario)?
Es el aspecto visual de la app: los colores, los botones, las imágenes y las tipografías. Es "cómo se ve".

#### ¿Qué es la UX (Experiencia de Usuario)?
Es la sensación y facilidad con la que una persona usa tu app. No se trata solo de que sea linda, sino de que sea útil, rápida y fácil de entender. Es "cómo se siente".

---

## 5. Microanimaciones (#microanimaciones-ux)

Son los pequeños detalles:
- Un "shake" (vibración visual) si la contraseña es incorrecta.
- Un "fade in" suave cuando aparece una lista.
- Un "bounce" (rebote) cuando completas una meta.

**Duración ideal**: Entre 200ms y 500ms. Más de eso se siente lenta.

---

## 6. Proyecto Práctico: App Escalable (#proyecto-practico)

Construiremos la base de una app "Premium":
1. Estructura de carpetas por módulos.
2. Navegación compuesta (Tabs que adentro tienen Stacks).
3. Animaciones de entrada coordinadas (los elementos de la lista aparecen uno tras otro).
4. Un flujo de login real que te redirige al home.

---

## ✅ Consejos de Diseño

- ✅ **Consistencia**: Si usas bordes redondeados de 10px, úsalos en toda la app.
- ✅ **Jerarquía**: Lo más importante (ej: botón de Comprar) debe resaltar más que el resto.
- ✅ **Espaciado**: Deja que los elementos "respiren". No amontones todo.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
