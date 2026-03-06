# Clase 11. Arquitectura y Experiencia de Usuario (UX)

## 📚 Índice

1. [El Plano de tu App: Definir el alcance](#alcance)
2. [Ordenando la casa: Arquitectura de carpetas](#arquitectura)
3. [El Mapa de Navegación: ¿A dónde voy ahora?](#navegacion)
4. [UX: Animaciones con propósito](#ux)
5. [Proyecto Práctico: Tu App como un Pro](#proyecto-practico)
6. [Resumen](#resumen)

---

## 1. El Plano de tu App: Definir el alcance {#alcance}

Antes de poner la primera línea de código, un programador profesional define el **Alcance**. 
- **¿Qué es?**: Una lista de qué pantallas tendrá la app y qué podrá hacer el usuario.
- **¿Para qué sirve?**: Para no perderse en el camino y terminar la app a tiempo.

**Ejemplo**: "Mi app tendrá 3 pantallas principales, login y modo oscuro. No tendrá pagos ni chat (por ahora)".

---

## 2. El Orden: Arquitectura de carpetas {#arquitectura}

A medida que tu app crece, tener todo en un solo lugar es un caos. Aprendemos a separar por **Módulos**:
- `auth/`: Todo lo referente a login y registro.
- `tasks/`: Todo lo referente a las tareas o funciones principales.
- `components/`: Botones y tarjetas que se usan en toda la app.

---

## 3. El Mapa de Navegación {#navegacion}

Aprendemos a combinar navegadores. Por ejemplo:
- Un **Stack** para el Login.
- Unas **Tabs** para el interior de la app.
- Otro **Stack** dentro de cada Tab para ver detalles.

Esto se llama **Navegación Compuesta**.

---

## 4. UX: Animaciones con propósito {#ux}

En UX (User Experience), las animaciones no son "adornos", son **mensajes**:
- **Éxito**: Un pequeño rebote en el botón cuando guardas algo.
- **Error**: El formulario vibra si pusiste mal la contraseña.
- **Espera**: Un círculo que gira suavemente.

> **Regla de oro**: Una buena animación debe durar entre 200ms y 500ms. Más lento aburre, más rápido no se ve.

---

## 5. Proyecto Práctico: Tu App como un Pro {#proyecto-practico}

### Objetivo
Tomar el proyecto de las clases anteriores y reorganizarlo con carpetas profesionales y agregarle las animaciones de "feedback" (éxito/error).

### Pasos
1. **Carpetas**: Mueve tus pantallas a carpetas como `/screens` y `/components`.
2. **Navegación**: Crea el flujo real: `Splash -> Login -> Home`.
3. **Detalles**: Agrega un efecto de "Shake" (vibración) si el login falla.

---

## ✅ Buenas Prácticas {#buenas-practicas}

- **Pantalla de Carga (Splash)**: Siempre ten una pantalla de carga mientras tu app revisa si el usuario ya inició sesión.
- **Nombres Claros**: Llama a tus rutas con constantes. En vez de escribir `"DetalleUser"`, usa `ROUTES.USER_DETAIL`.
- **Menos es más**: Si una pantalla tiene 20 animaciones, el usuario se va a confundir.

---

## 📝 Resumen {#resumen}

### Conceptos Clave Aprendidos
1. **Arquitectura Modular**: Código fácil de mantener.
2. **Navegación Compuesta**: Combinar Stacks y Tabs.
3. **Feedback Visual**: Hablarle al usuario con movimientos.

### Próximos Pasos
- Mira las apps que más usas (Instagram, TikTok). ¿Cómo se mueven cuando tocas algo? ¡Intenta imitarlo!

---

**Última actualización:** Marzo 2026 - Guía para estudiantes.
