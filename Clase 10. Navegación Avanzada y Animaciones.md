# Clase 10. Navegación Avanzada y Animaciones

## 📚 Índice

1. [Navegación con Pestañas (Tabs)](#navegacion-tabs)
2. [Menú Lateral (Drawer)](#navegacion-drawers)
3. [Navegación Anidada: Mezclando todo](#drawers-anidacion)
4. [Introducción a las Animaciones](#framer-motion)
5. [Framer Motion en React Native (@legendapp/motion)](#framer-instalacion)
6. [Microinteracciones: Feedback al usuario](#microinteracciones)
7. [Proyecto Práctico: App con Flujo Completo](#proyecto-practico)
8. [Resumen y Buenas Prácticas](#resumen)

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

¿Por qué usar animaciones?
- Hacen que la app no se sienta "dura".
- Ayudan al usuario a entender qué pasó (ej: si algo desaparece, que se desvanezca suavemente).

Usaremos **`@legendapp/motion`**, que es la versión de Framer Motion optimizada para celulares.

---

## 5. Microinteracciones {#microinteracciones}

Son las animaciones "chiquitas":
- Un botón que se achica un poquito cuando lo tocas.
- Una tarjeta que rebota al entrar a la pantalla.
- Un check que se anima cuando marcas una tarea como lista.

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
