# Clase 10. Navegación Avanzada y Animaciones

## 📚 Índice

1. [Teoría: ¿Por qué mi app se traba cuando animo? (Hilos)](#teoria-hilos)
2. [Navegación con Pestañas (Bottom Tabs)](#tabs)
3. [Navegación Lateral (Drawer)](#drawer)
4. [Navegación Anidada: Mezclando todo](#drawers-anidacion)
5. [Introducción a las Animaciones](#framer-motion)
6. [Framer Motion en React Native (@legendapp/motion)](#framer-instalacion)
7. [Microinteracciones: Feedback al usuario](#microinteracciones)
8. [Proyecto Práctico: App con Flujo Completo](#proyecto-practico)
9. [Resumen y Buenas Prácticas](#resumen)

---

## 1. Teoría: Hilo de UI vs Hilo de JS {#teoria-hilos}

#### ¿Qué es un Hilo (Thread)?
Es un "trabajador" o un camino de ejecución dentro del procesador de tu celular. Tu app no hace todo en un solo lugar; reparte las tareas entre distintos hilos.

#### ¿Qué es el Hilo de JS?
Es donde corre todo tu código lógico: los `if`, los bucles, las llamadas a APIs y el estado de tu app.

#### ¿Qué es el Hilo de UI (Interfaz)?
Es el encargado exclusivo de dibujar los píxeles en la pantalla. Es el que sabe mover un botón o pintar una imagen.

#### ¿Qué es el Renderizado a 60 FPS?
FPS significa "Cuadros por Segundo" (Frames Per Second). Para que una animación se vea fluida como el agua, el celular debe dibujar 60 imágenes distintas cada segundo.

**El problema**: Si el hilo de JS está muy ocupado, la animación se verá entrecortada. 
**La solución**: Usamos herramientas que mandan la animación al **Hilo de UI**, para que sea fluida (60 FPS) aunque tu código esté ocupado procesando datos pesados en el fondo.

---

## 1. Navegación con Pestañas (Tabs) {#navegacion-tabs}

Las **Tabs** son la forma más común de navegar en apps como Instagram o Spotify. Permiten saltar entre las secciones principales de forma instantánea.
- **Uso**: 3 a 5 secciones máximo.
- **Personalización**: Podemos agregarle iconos y hasta "badges" (globitos rojos de notificaciones).

---

## 2. Menú Lateral (Drawer) {#navegacion-drawers}

El **Drawer** es el panel que se desliza desde el costado.
- **Cuándo elegirlo**: Cuando tienes muchas pantallas o configuraciones que no caben en la barra de abajo.
- **Dato técnico**: Usa `react-native-reanimated` para que el movimiento sea fluido.

---

## 3. Navegación Anidada {#drawers-anidacion}

En una app real, sueles tener un **Drawer** para el menú general, y adentro de una de esas pantallas tienes **Tabs** para navegar sub-secciones.
- **Truco**: Cada navegación es un componente independiente que "habla" con el resto.

---

## 4. Animaciones con Framer Motion {#framer-instalacion}

#### ¿Qué es una Animación?
Es el cambio gradual de una propiedad visual (como la opacidad, la posición o el tamaño) a lo largo del tiempo. Sirve para que el usuario entienda qué ocurre en la pantalla.

#### ¿Qué es @legendapp/motion?
Es una versión ultraligera de la famosa librería **Framer Motion**, adaptada para que funcione rápido en celulares sin gastar mucha batería.

---

## 5. Microinteracciones {#microinteracciones}

#### ¿Qué es una Microinteracción?
Es una animación pequeña y sutil que sucede en respuesta a una acción directa del usuario (como tocar un botón o marcar un check). Su fin es dar "feedback" (confirmación) de que la acción fue registrada.

```tsx
<Motion.Pressable 
  whileTap={{ scale: 0.9 }} 
  onPress={hacerAlgo}
>
  <Text>Presióname</Text>
</Motion.Pressable>
```

---

## 6. Proyecto Práctico: App con Flujo Completo {#proyecto-practico}

Crearemos una app que tenga:
1. Un **Drawer** lateral.
2. Un sistema de **Tabs** para "Home" y "Perfil".
3. Animaciones de entrada en cada lista de elementos.
4. Botones con **microinteracciones** de escala al tocarlos.

---

## ✅ Buenas Prácticas

- ✅ **Menos es más**: No animes todo, o el usuario se va a marear. Anima solo lo que da información útil.
- ✅ **Performance**: Usa `Reanimated` y librerías livianas para no gastar batería de más.
- ✅ **Consistencia**: Si un botón se achica al tocarlo, que todos los botones de la app hagan lo mismo.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
