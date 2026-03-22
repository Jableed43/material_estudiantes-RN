# Clase 06. Optimizando tu app (Hooks Intermedios)

## 📚 Índice

1. [Introducción a la Optimización](#introducción)
2. [Repaso Profundo: useEffect](#repaso-useeffect)
3. [useMemo: Memorizar Valores](#usememo-memorizacion-valores)
4. [useCallback: Memorizar Funciones](#usecallback-memorizacion-funciones)
5. [useRef: Referencias Mutables](#useref-referencias-mutables)
6. [Composición Lógica (Separar UI de Datos)](#composicion-logica)
7. [Proyecto Práctico: Buscador Optimizado](#proyecto-practico)
8. [Resumen y Buenas Prácticas](#resumen-buenas-practicas)

---

## 1. Introducción a la Optimización {#introducción}

A medida que nuestras apps crecen, React Native tiene que hacer más trabajo para mantener la pantalla actualizada. Si no tenemos cuidado, la app puede empezar a ir lenta o "trabarse". Los **Hooks Intermedios** nos ayudan a evitar que React haga trabajo innecesario.

---

## 2. useMemo: Memorizar Valores {#usememo-memorizacion-valores}

Imagina que tienes una lista de 1000 productos y quieres filtrarlos. Si filtras la lista en cada renderizado, el celular trabajará de más.

**`useMemo`** guarda el resultado de un cálculo para no repetirlo salvo que algo cambie.

```tsx
const productosFiltrados = useMemo(() => {
  console.log("Filtrando productos..."); // Solo se verá cuando CAMBIE la búsqueda
  return productos.filter(p => p.nombre.includes(busqueda));
}, [productos, busqueda]); // Solo se ejecuta si cambian estos dos
```

---

## 3. useCallback: Memorizar Funciones {#usecallback-memorizacion-funciones}

En JavaScript, cada vez que un componente se renderiza, las funciones de adentro se "crean de nuevo". Esto puede causar que componentes hijos se vuelvan a dibujar sin necesidad.

**`useCallback`** mantiene la misma función en memoria. Es vital cuando pasas funciones a componentes pesados o listas.

```tsx
const manejarPresion = useCallback((id) => {
  console.log("Presionaste el id:", id);
}, []); // La función se crea UNA SOLA VEZ y nunca más
```

---

## 4. useRef: Referencias Mutables {#useref-referencias-mutables}

`useRef` es como una "caja" donde puedes guardar algo sin que React se entere (sin provocar re-render).

**Usos comunes:**
1. **Acceso al hardware**: Como enfocar un `TextInput` automáticamente.
2. **Guardar valores anteriores**: Saber qué texto había antes de que el usuario lo borrara.
3. **Timers**: Guardar el ID de un `setInterval`.

```tsx
const inputRef = useRef(null);

const enfocar = () => {
  inputRef.current.focus(); // Enfocamos el teclado programáticamente
};

<TextInput ref={inputRef} />
```

---

## 5. Composición Lógica {#composicion-logica}

La regla de oro de un buen desarrollador es: **"No mezcles la lógica con los botones"**.
- Crea **Custom Hooks** para manejar los datos (Clase 5).
- Usa el componente solo para mostrar esos datos.
- Así tu código será más fácil de leer y arreglar.

---

## 6. Proyecto Práctico: Buscador con Filtros {#proyecto-practico}

Crearemos una app de "Buscador de Personajes":
- Traeremos datos de una API.
- Usaremos **`useMemo`** para filtrar por nombre sin lag.
- Usaremos **`useCallback`** para la función de "Favoritos".
- Veremos cómo el rendimiento mejora cuando aplicamos estos hooks.

---

## ✅ Buenas Prácticas

- ✅ **No optimices por optimizar**: Si tu cálculo es sumar `1 + 1`, no uses `useMemo`. Úsalo para listas largas u objetos complejos.
- ✅ **Dependencias Correctas**: Asegúrate de poner todas las variables que usas dentro del array `[]` del hook.
- ✅ **React.memo**: Usa este componente para envolver hijos que no necesitan re-renderizarse si sus props no cambiaron.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
