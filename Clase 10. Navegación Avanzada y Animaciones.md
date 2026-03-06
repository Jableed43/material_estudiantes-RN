# Clase 10. Navegación Avanzada y Animaciones

## 📚 Índice

1. [Tabs: El menú de abajo](#tabs)
2. [Drawer: El menú lateral](#drawer)
3. [Animaciones con Framer Motion](#animaciones)
4. [Microinteracciones: Detalles que importan](#microinteracciones)
5. [Proyecto Práctico: App con Estilo Premium](#proyecto-practico)
6. [Resumen](#resumen)

---

## 1. Tabs: El menú de abajo {#tabs}

Es la forma más común de navegar en apps modernas (como Instagram o WhatsApp). Tienes 3 o 4 secciones fijas abajo.
- **Ideal para**: Secciones que el usuario usa todo el tiempo.
- **Truco**: Puedes poner "badges" (globos rojos) cuando hay notificaciones.

---

## 2. Drawer: El menú lateral {#drawer}

Es el menú que "sale" de un costado cuando tocas las 3 rayitas (hamburguesa).
- **Ideal para**: Configuración, Perfil, Cerrar Sesión, o apps con muchísimas pantallas.
- **Anidación**: Puedes tener un menú lateral y que dentro de una opción haya pestañas abajo. ¡Se pueden combinar!

---

## 3. Animaciones con Framer Motion {#animaciones}

Para que tu app no se sienta "seca" o aburrida, usamos animaciones. En React Native usamos `@legendapp/motion`.

**Estados de una animación:**
- **Initial**: Cómo empieza (ej: invisible y chiquito).
- **Animate**: Cómo termina (ej: visible y tamaño normal).
- **Transition**: Qué tan rápido o "rebotín" es el movimiento.

```javascript
<Motion.View
  initial={{ opacity: 0, scale: 0.5 }}
  animate={{ opacity: 1, scale: 1 }}
  transition={{ type: 'spring' }} // ¡Efecto rebote!
>
  <Text>¡Hola!</Text>
</Motion.View>
```

---

## 4. Microinteracciones: Detalles que importan {#microinteracciones}

Son pequeñas reacciones visuales. No cambian la app, pero la hacen sentir "viva".
- **Ejemplo**: Que el botón se achique un poquito cuando lo presionas.
- **Ejemplo**: Que un input brille de color verde cuando escribes bien tu mail.

---

## 5. Proyecto Práctico: App con Estilo Premium {#proyecto-practico}

### Objetivo
Hacer una app que use un menú de pestañas abajo y que al cambiar de pantalla, el contenido aparezca con un efecto suave de "fade in".

### Pasos
1. **Tabs**: Crea un `Tab.Navigator`.
2. **Iconos**: Usa `@expo/vector-icons` para que cada pestaña tenga un dibujo lindo.
3. **Motion**: Envuelve el contenido de tus pantallas en un `<Motion.View>` para que aparezcan suavemente.

---

## ✅ Buenas Prácticas {#buenas-practicas}

- **No exageres**: Si todo se mueve, rebota y brilla al mismo tiempo, el usuario se va a marear. Menos es más.
- **Consistencia**: Si un botón se achica al tocarlo, que todos los botones de la app hagan lo mismo.
- **Iconos claros**: No uses iconos raros. Si es "Inicio", usa una casita. Si es "Perfil", un monigote.

---

## 📝 Resumen {#resumen}

### Conceptos Clave Aprendidos
1. **Tabs**: Navegación principal rápida.
2. **Drawer**: Navegación secundaria con mucho espacio.
3. **Framer Motion**: Animaciones fáciles y potentes.
4. **Spring**: La transición que imita la física real (rebote).

### Próximos Pasos
- Intenta animar una lista para que los elementos aparezcan uno por uno con un pequeño retraso (`delay`). ¡Se ve muy profesional!

---

**Última actualización:** Marzo 2026 - Guía para estudiantes.
