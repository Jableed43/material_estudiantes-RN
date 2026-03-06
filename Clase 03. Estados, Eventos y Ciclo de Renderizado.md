# Clase 03. Estados, Eventos y Ciclo de Renderizado

## 📚 Índice

1. [¿Qué es el Estado?](#que-es-estado)
2. [El Hook `useState`](#usestate)
   - [Sintaxis y Uso](#sintaxis)
   - [Actualización Correcta (Inmutabilidad)](#actualizacion)
3. [Manejo de Eventos](#eventos)
   - [onPress, onChangeText y más](#eventos-comunes)
4. [Componentes para Listas e Interactividad](#componentes)
   - [FlatList: Listas Optimizadas](#flatlist)
5. [El Ciclo de Renderizado](#renderizado)
6. [Proyecto Práctico: TODO List](#proyecto-practico)
7. [Buenas Prácticas](#buenas-practicas)
8. [Resumen](#resumen)

---

## 1. ¿Qué es el Estado? {#que-es-estado}

**El estado es la "memoria" de tu componente.**

Imagina que tu aplicación es un formulario. Cuando el usuario escribe su nombre, ese nombre debe guardarse en algún lugar para que la app lo sepa. Ese "lugar" es el **estado**.

**Para qué sirve:**
- **Interactividad**: Permite que la app reaccione a lo que hace el usuario.
- **Dinamismo**: La pantalla se actualiza solita cuando el estado cambia.

---

## 2. El Hook `useState` {#usestate}

### 🛠️ Sintaxis y Uso {#sintaxis}

```javascript
import { useState } from 'react';

const [valor, setValor] = useState(inicial);
```

- **`valor`**: Es el dato guardado (como el número de un contador).
- **`setValor`**: Es la ÚNICA función autorizada para cambiar ese dato.

### ⚠️ Regla de Oro: Inmutabilidad {#actualizacion}

**¡Nunca cambies el estado directamente!**

```javascript
// ❌ INCORRECTO (La pantalla no se enterará del cambio)
usuario.nombre = "Pepe"; 

// ✅ CORRECTO (React detecta el cambio y refresca la pantalla)
setUsuario({ ...usuario, nombre: "Pepe" });
```

---

## 3. Manejo de Eventos {#eventos}

Los eventos son las acciones que ocurren en la app (un click, un texto que cambia, un scroll).

### 📋 Eventos más Comunes {#eventos-comunes}

| Evento | Cuándo ocurre |
|--------|---------------|
| `onPress` | Cuando el usuario toca un botón o elemento. |
| `onChangeText` | Cuando el usuario escribe en un campo de texto. |
| `onValueChange` | Cuando mueves un interruptor (Switch). |
| `onLongPress` | Cuando mantienes presionado un elemento por un segundo. |

---

## 4. Componentes Clave {#componentes}

### 📜 FlatList: Listas Inteligentes {#flatlist}

Si tienes 1000 items, **no uses ScrollView**. Usa **`FlatList`**.
**¿Por qué?** Porque `FlatList` solo dibuja en pantalla los elementos que el usuario está viendo en ese momento, ahorrando muchísima memoria.

```javascript
<FlatList
  data={misDatos}
  renderItem={({ item }) => <Text>{item.nombre}</Text>}
  keyExtractor={item => item.id}
/>
```

---

## 5. El Ciclo de Renderizado {#renderizado}

**¿Qué pasa cuando haces `setAlgo(...)`?**
1. React recibe el nuevo valor.
2. React vuelve a ejecutar la función de tu componente (**Re-render**).
3. React compara qué cambió y actualiza solo esa partecita en la pantalla del celular.

---

## 6. Proyecto Práctico: TODO List {#proyecto-practico}

### Objetivo
Crear una lista de tareas donde puedas agregar, tachar y borrar pendientes.

### Pasos Generales
1. **Estado de Lista**: Crea un array `const [tareas, setTareas] = useState([])`.
2. **Agregar**: Crea una función que use `setTareas([...tareas, nuevaTarea])`.
3. **Renderizar**: Usa un `FlatList` para mostrar cada tarea.
4. **Interactividad**: Usa un `Switch` o un `Pressable` para marcar como completada.

---

## ✅ Buenas Prácticas {#buenas-practicas}

- **Keys Únicas**: Siempre dale un `id` único a cada elemento de una lista. Evita usar el índice (0, 1, 2...) como ID.
- **Funciones de Actualización**: Si el nuevo valor depende del anterior (como un contador), usa `setContador(prev => prev + 1)`.
- **Validación**: Usa `.trim()` en los textos para evitar que el usuario agregue tareas vacías.

---

## 📝 Resumen {#resumen}

### Conceptos Clave Aprendidos
1. **useState**: La herramienta para que la app "recuerde" cosas.
2. **Re-render**: El proceso de actualización visual.
3. **FlatList**: La forma profesional de mostrar listas largas.

### Próximos Pasos
- Mira la **Guía de TODO List** para ver el código completo paso a paso.
- Intenta agregar un botón de "Borrar todo" a tu proyecto.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje para estudiantes.
