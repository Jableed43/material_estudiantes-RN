# Clase 06. Optimizando tu app (Hooks Intermedios)

## 📚 Índice

1. [Teoría: ¿Por qué React re-renderiza tanto?](#teoria-render)
2. [Repaso de useEffect (Ciclo de Vida)](#repaso-useeffect)
3. [useMemo: Memorizar Valores](#usememo-memorizacion-valores)
4. [useCallback: Memorizar Funciones](#usecallback-memorizacion-funciones)
5. [useRef: Referencias Mutables](#useref-referencias-mutables)
6. [Composición Lógica (Separar UI de Datos)](#composicion-logica)
7. [Proyecto Práctico: Buscador Optimizado](#proyecto-practico)
8. [Resumen y Buenas Prácticas](#resumen-buenas-practicas)

---

## 1. Teoría: La "Igualdad Referencial" e hilos {#teoria-render}

#### ¿Qué es un Re-renderizado?
Es cuando React vuelve a dibujar tu componente para mostrar cambios en la pantalla. Si no tenemos cuidado, esto puede pasar cientos de veces por segundo sin necesidad.

#### ¿Qué es la "Igualdad Referencial"?
Es la forma en que el celular compara si dos cosas son iguales.
- React **no mira** lo que hay dentro de una función cada vez que se redibuja. Solo mira si es la **misma dirección de memoria**.
- En JavaScript, si creas una función dos veces idénticamente, ¡son distintas para React! `(()=>5) === (()=>5)` es `FALSE`.

**Conclusión**: Si pasas una función "nueva" a un componente hijo, el hijo pensará que algo cambió y se volverá a dibujar, aunque el código sea el mismo. Por eso usamos estos hooks avanzados: para **congelar** las funciones y que React vea que son iguales.

---

## 1. Introducción a la Optimización {#introducción}

#### ¿Qué es la Optimización?
Es el proceso de hacer que nuestra aplicación use menos recursos (batería, procesador) para que se sienta más rápida y fluida al tacto del usuario.

A medida que nuestras apps creen, React Native tiene que hacer más trabajo para mantener la pantalla actualizada. Si no tenemos cuidado, la app puede empezar a ir lenta o "trabarse". Los **Hooks Intermedios** nos ayudan a evitar que React haga trabajo innecesario.

---

## 2. useMemo: Memorizar Valores {#usememo-memorizacion-valores}

#### ¿Qué es useMemo?
Es un hook que sirve para "recordar" el resultado de un cálculo difícil (como filtrar una lista gigante). Evita que el celular tenga que hacer la misma cuenta cada vez que la pantalla se actualiza por otra razón.

```tsx
const productosFiltrados = useMemo(() => {
  console.log("Filtrando productos..."); // Solo se verá cuando CAMBIE la búsqueda
  return productos.filter(p => p.nombre.includes(busqueda));
}, [productos, busqueda]); // Solo se ejecuta si cambian estos dos
```

---

## 3. useCallback: Memorizar Funciones {#usecallback-memorizacion-funciones}

#### ¿Qué es useCallback?
Es un hook que sirve para "congelar" una función en la memoria de la app. Evita que la función se cree de nuevo en cada renderizado, lo que previene que los componentes hijos se vuelvan a dibujar innecesariamente.

```tsx
const manejarPresion = useCallback((id) => {
  console.log("Presionaste el id:", id);
}, []); // La función se crea UNA SOLA VEZ y nunca más
```

---

## 4. useRef: Referencias Mutables {#useref-referencias-mutables}

#### ¿Qué es useRef?
Es como una "caja negra" o una "notita" pegada al componente. Nos permite guardar un valor que no queremos mostrar en pantalla, pero que necesitamos recordar (como el foco de un input o un temporizador).

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

#### ¿Qué son las Dependencias?
Son las variables que el hook vigila. Si alguna de ellas cambia, el hook se "descongela" y vuelve a ejecutarse para actualizarse.
- ✅ **React.memo**: Usa este componente para envolver hijos que no necesitan re-renderizarse si sus props no cambiaron.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
