# Clase 03. Estados, Eventos y Ciclo de Renderizado

## 📚 Índice

1. [El Corazón de React: ¿Qué es el Estado?](#que-es-estado)
2. [useState Hook (Usar memoria en componentes)](#usestate-hook)
3. [Manejo de Eventos en Mobile](#eventos-mobile)
   - [Diferencias con React Web](#diferencias-web)
   - [onPress vs onClick](#on-press)
   - [onChangeText: Capturar el teclado](#on-change-text)
4. [Componentes Listas (FlatList)](#flatlist)
5. [SafeAreaView: Evitando el Notch](#safeareaview)
6. [Renderizado Condicional (Mostrar/Ocultar cosas)](#render-condicional)
7. [Proyecto Práctico: Mi Primera Todo List](#proyecto-practico)
8. [Resumen y Buenas Prácticas](#resumen)

---

## 1. El Estado (`useState`) {#que-es-estado}

Las apps no son estáticas. Necesitan recordar datos (texto, checks, contadores).
- El **estado** es la memoria interna del componente.
- Cada vez que el estado cambia, React vuelve a dibujar (renderizar) la pantalla.

```javascript
import { useState } from 'react';

const MiComponente = () => {
  // valor: Dato actual | setValor: Función para cambiarlo
  const [contador, setContador] = useState(0);

  return <Text>Contador: {contador}</Text>;
};
```

⚠️ **Regla de oro**: El estado es **inmutable**. Nunca hagas `contador = 5`. Debes usar `setContador(5)`.

---

## 2. Manejo de Eventos {#eventos-mobile}

En el celular **no existe el evento click**, existe el **press** (presionar con el dedo).

### Comparativa Web vs Mobile
| Evento Web | Evento React Native | Componente |
|------------|---------------------|------------|
| `onClick` | `onPress` | Button / Touchable |
| `onChange` | `onChangeText` | TextInput |
| `onSubmit` | `onPress` (en un botón) | Formulario manual |

```javascript
<TextInput 
  placeholder="Escribe algo..." 
  onChangeText={(texto) => setMitetxto(texto)} 
/>
```

---

## 3. Listas Eficientes con `FlatList` {#flatlist}

Si tienes 100 o 1000 elementos, **NO** uses un `map()`. Se volverá lento.
- ✅ **FlatList**: Solo dibuja lo que el usuario ve en pantalla. Es ultra rápido.
- Necesita: `data` (la lista) y `renderItem` (cómo se ve cada elemento).

```javascript
<FlatList
  data={misTareas}
  keyExtractor={(item) => item.id}
  renderItem={({ item }) => <Text>{item.titulo}</Text>}
/>
```

---

## 4. SafeAreaView {#safeareaview}

Los celulares modernos tienen notches (agujeros para la cámara) y barras de navegación.
- **SafeAreaView** empuja el contenido para que no quede tapado por el hardware.
- 📦 **Uso recomendado**: Usa el de `react-native-safe-area-context`.

---

## 5. Renderizado Condicional {#render-condicional}

Podemos mostrar u ocultar componentes usando lógica simple:

```javascript
{ estaLogueado ? <Perfil /> : <BotónLogin /> }
```

O si solo queremos mostrar algo si se cumple una condición:
```javascript
{ mostrarError && <Text style={{ color: 'red' }}>Algo salió mal</Text> }
```

---

## 6. Proyecto Práctico: Mi Primera Todo List {#proyecto-practico}

### Objetivo
Construir una aplicación funcional donde puedas escribir una tarea, agregarla a la lista y borrarla.

### Pasos Generales
1. Crear un estado para el texto del input (`const [tarea, setTarea] = useState("");`).
2. Crear un estado para el arreglo de tareas (`const [lista, setLista] = useState([]);`).
3. Función `agregarTarea`: Toma el texto del input y lo añade al arreglo usando el operador spread `...lista`.
4. Mostrar las tareas usando un `<FlatList>`.
5. Agregar un botón de borrar para cada tarea.

### Resultado Final
Una lista de tareas dinámica e interactiva que demuestra el ciclo completo de renderizado.

---

## ✅ Tips de Clase

- ✅ **Spread Operator (...)**: Úsalo para actualizar arreglos y objetos sin mutarlos.
- ✅ **Teclado**: Usa `keyboardType="numeric"` si solo vas a pedir números.
- ✅ **Keys**: Asegúrate de que cada item de tu lista tenga una `id` única.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
