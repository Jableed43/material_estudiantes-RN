# Clase 06. Optimizando tu app (Hooks Intermedios)

## 📚 Índice

1. [¿Por qué optimizar?](#por-que)
2. [useMemo: No calcules lo mismo dos veces](#usememo)
3. [useCallback: No crees la misma función siempre](#usecallback)
4. [useRef: El valor "invisible"](#useref)
5. [Composición Lógica: Orden en tu código](#composicion)
6. [Proyecto Práctico: Filtro de Usuarios Inteligente](#proyecto-practico)
7. [Resumen](#resumen)

---

## 1. ¿Por qué optimizar? {#por-que}

Cada vez que algo cambia en tu app (un estado), React vuelve a leer todo el componente. Si tienes una lista gigante o un cálculo matemático difícil, la app se puede poner lenta o "trabada".
Para evitar esto, usamos **Hooks de Optimización**.

---

## 2. useMemo: Recordar Resultados {#usememo}

Imagina que tienes una lista de 1000 usuarios y quieres filtrarlos por nombre. No quieres que la app los filtre de nuevo cada vez que el usuario toca un botón que no tiene nada que ver.

**`useMemo`** guarda el **resultado** de una operación pesada y solo la repite si algo realmente cambió.

```javascript
const usuariosFiltrados = useMemo(() => {
  console.log("Filtrando...");
  return usuarios.filter(u => u.nombre.includes(busqueda));
}, [usuarios, busqueda]); // Solo se ejecuta si cambian los usuarios o la búsqueda
```

---

## 3. useCallback: Recordar Funciones {#usecallback}

En JavaScript, cada vez que un componente se actualiza, las funciones que creaste dentro de él se "borran" y se crean de nuevo. Esto a veces hace que componentes hijos crean que algo cambió cuando no es cierto.

**`useCallback`** guarda la **función** en memoria.

```javascript
const manejarEnvio = useCallback(() => {
  console.log("Enviando datos...");
}, []); // La función será SIEMPRE la misma referencia
```

---

## 4. useRef: El valor "invisible" {#useref}

A veces necesitas guardar un dato pero **no quieres** que la pantalla se refresque cuando ese dato cambia.
- **Diferencia**: 
  - `useState` -> Cambia el valor -> La pantalla se refresca.
  - `useRef` -> Cambia el valor -> La pantalla **NO** se refresca.

**Uso común: Enfocar un input**
```javascript
const inputRef = useRef(null);

const enfocar = () => {
  inputRef.current.focus(); // Usamos la "referencia" al input real
};

return <TextInput ref={inputRef} />;
```

---

## 5. Composición Lógica: Tu código ordenado {#composicion}

No pongas toda la lógica (filtros, pedidos a internet, validaciones) dentro de tu componente visual. 

- **Mala práctica**: Componente de 500 líneas con todo mezclado.
- **Buena práctica**: Crear funciones o hooks pequeños que se encarguen de una sola cosa.

---

## 6. Proyecto Práctico: Filtro de Usuarios Inteligente {#proyecto-practico}

### Objetivo
Cargar una lista de usuarios de una API y permitir filtrarlos con un buscador sin que la app pierda rendimiento.

### Pasos
1. **Fetch**: Pide los usuarios al iniciar.
2. **Filtro**: Usa `useMemo` para filtrar la lista basándote en un `TextInput`.
3. **Optimización**: Asegúrate de que el log "Filtrando..." solo aparezca cuando realmente escribes en el buscador, no cuando tocas otros botones.

---

## 📝 Resumen {#resumen}

### Conceptos Clave Aprendidos
1. **useMemo**: Para resultados (datos).
2. **useCallback**: Para funciones.
3. **useRef**: Para interactuar con el "mundo real" (foco, timers) sin refrescar la pantalla.

### Próximos Pasos
- ¿Tengo una operación matemática lenta? -> `useMemo`.
- ¿Tengo un componente hijo que se refresca mucho? -> `useCallback` en las props que le paso.

---

**Última actualización:** Marzo 2026 - Guía para estudiantes.
