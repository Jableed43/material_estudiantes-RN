# Clase 03. Estados, Eventos y Ciclo de Renderizado

## 📚 Índice

1. [Conceptos Fundamentales de Estado](#concepto-general)
2. [El Corazón de React: ¿Qué es el Estado?](#que-es-estado)
3. [Teoría: Reconciliación y Batching](#teoria-reconciliacion)
4. [useState Hook (Usar memoria en componentes)](#usestate-hook)
5. [Manejo de Eventos en Mobile](#eventos-mobile)
   - [Diferencias con React Web](#diferencias-web)
   - [onPress vs onClick](#on-press)
   - [onChangeText: Capturar el teclado](#on-change-text)
6. [Componentes Listas (FlatList)](#flatlist)
7. [SafeAreaView: Evitando el Notch](#safeareaview)
8. [Renderizado Condicional (Mostrar/Ocultar cosas)](#render-condicional)
9. [Ciclo de Renderizado: Re-render vs Re-mount](#ciclo-renderizado)
10. [Proyecto Práctico: Mi Primera Todo List](#proyecto-practico)
11. [Resumen y Buenas Prácticas](#resumen)

---

## 1. Conceptos Fundamentales de Estado {#concepto-general}

### ¿Qué es un Estado?
Un **Estado** es una situación o condición sobre algo en un momento determinado. No es algo estático; puede cambiar.

#### Tipos de Estados en la vida real:

- **Duales (Solo dos opciones):**
  - Prendido / Apagado
  - Iluminado / Oscuro
  - Dulce / Salado
  - Día / Noche

- **Relativos (Valores que varían en una escala):**
  - **Volumen** -> 100ml / 5l
  - **Longitud** -> 50m / 10cm
  - **Capacidad** -> 50%
  - **Contenido** -> Una lista de 10 invitados de una fiesta / 20 invitados a una fiesta

---

## 2. El Estado en React {#que-es-estado}

### ¿Qué es el Estado en React?
Es la "memoria" de un componente. Permite que la aplicación recuerde información que el usuario ingresa o acciones que realiza.

**Características de los estados en React:**
- **Determina el Renderizado Condicional**: Decide si se muestra o no un componente.
- **Determina la Apariencia**: Ejemplo: cambiar entre modo oscuro y modo claro.
- **Funciones Especiales**: Solo se cambia con funciones específicas (`setState` o el retorno de `useState`).
- **Independencia**: Cada componente tiene sus propios estados, independientes de los demás.
- **Memoria Temporal**: Es una forma de persistencia mientras la app está abierta.

### ¿Por qué es importante el estado?
- **Guardar datos**: Almacena lo que el usuario escribe o elige.
- **Control Visual**: Controla qué se está viendo en la pantalla en cada momento.
- **Persistencia entre renders**: Mantiene la información aunque el código del componente vuelva a ejecutarse.
- **Interactividad**: Permite que las aplicaciones no sean simples páginas estáticas, sino herramientas dinámicas.

### Estado vs Variable
| Característica | Variable Común | Estado (`useState`) |
| :--- | :--- | :--- |
| **¿Qué es?** | Un contenedor de datos temporal. | Una "memoria" rastreada por React. |
| **Renderizado** | Se reinicia en cada renderizado. | Persiste entre renderizados. |
| **Notificación** | No avisa a React de los cambios. | Notifica a React para actualizar la pantalla. |
| **Efecto Visual** | Si cambia, la pantalla no se actualiza sola. | Si cambia, la pantalla se actualiza automáticamente. |
| **Uso Ideal** | Cálculos temporales internos. | Guardar valores que el usuario ve o usa. |

---

## 3. Teoría: Reconciliación y Batching {#teoria-reconciliacion}

### ¿Qué es la Reconciliación?
Es el proceso por el cual React compara lo que tenía antes con lo que tiene ahora para decidir qué cambiar.
- **Eficiencia**: React no redibuja toda la pantalla cada vez que cambia un número. Solo modifica el píxel o el elemento que realmente cambió (gracias al Virtual DOM).

### ¿Qué es el Batching?
Es la capacidad de React de agrupar varios cambios de estado en una sola actualización. Si cambias 5 cosas a la vez, React hace un solo "viaje" de actualización para ahorrar batería y CPU.

---

## 4. useState Hook {#usestate-hook}

### ¿Qué es un Hook?
Un **Hook** es una función especial que nos permite "engancharnos" a las funcionalidades de React (como el estado o el ciclo de vida) en componentes funcionales.

### Sintaxis de useState
```javascript
const [estado, setEstado] = useState(valorInicial);
```
- **valorInicial**: Es el primer valor que tendrá el estado al cargarse por primera vez.
- **estado**: Es la constante que guarda el valor actual (solo lectura).
- **setEstado**: Es el método (función) que permite asignar un nuevo valor al estado y avisar a React.

#### Valores iniciales típicos según el tipo de dato:
- **Boolean** (Verdad/Falso) -> `false`
- **String** (Texto) -> `""` (vacio)
- **Number** (Número) -> `0`
- **Object** (Objeto) -> `null` o `{}`
- **Array** (Lista) -> `[]`

⚠️ **Regla de oro**: El estado es **inmutable**. Nunca hagas `contador = 5`. Debes usar siempre la función `setEstado(5)`.

---

## 5. Manejo de Eventos en Mobile {#eventos-mobile}

### ¿Qué es un Evento?
Es una acción que sucede en la aplicación, generalmente disparada por el usuario (tocar, escribir, deslizar).

En el celular **no existe el evento click**, existe el **press** (presionar con el dedo).

### Comparativa Web vs Mobile
| Evento Web | Evento React Native | Componente | ¿Qué hace? |
| :--- | :--- | :--- | :--- |
| `onClick` | `onPress` | Button / Touchable | Se activa al presionar el elemento. |
| `onChange` | `onChangeText` | TextInput | Se activa cada vez que el texto cambia. |
| `onSubmit` | `onPress` | Button | Se usa para procesar el formulario manualmente. |

```javascript
<TextInput 
  placeholder="Escribe algo..." 
  onChangeText={(texto) => setMitetxto(texto)} 
/>
```

---

## 6. Listas Eficientes con `FlatList` {#flatlist}

### ¿Qué es FlatList?
Es un componente optimizado para mostrar listas de datos de forma eficiente.
- **Renderizado Virtual**: Solo dibuja lo que el usuario ve en pantalla. Si tienes 10,000 elementos, el celular no se tildará.

#### ¿Qué necesita un FlatList?
- **data**: La lista de información (el arreglo).
- **renderItem**: Una función que describe cómo se ve cada elemento individual de la lista.

```javascript
<FlatList
  data={misTareas}
  keyExtractor={(item) => item.id}
  renderItem={({ item }) => <Text>{item.titulo}</Text>}
/>
```

---

## 7. SafeAreaView {#safeareaview}

### ¿Qué es SafeAreaView?
Es un componente que asegura que el contenido de tu app se vea correctamente en dispositivos con muescas (notches), esquinas redondeadas o barras de estado.
- **Propósito**: Evita que el texto o los botones queden tapados por el hardware del teléfono.

---

## 8. Renderizado Condicional {#render-condicional}

Es la técnica de mostrar u ocultar partes de la pantalla según se cumpla o no una condición.

### If Ternario
Es una forma corta de escribir un `if-else`.
```javascript
condicion ? resultado1 : resultado2
```
**Equivale a:**
```javascript
if(condicion) {
  return resultado1;
} else {
  return resultado2;
}
```

**Ejemplo en React:**
```javascript
{ estaLogueado ? <Perfil /> : <BotónLogin /> }
```

### Operador lógico &&
Se usa cuando solo queremos mostrar algo si se cumple la condición (sin el "si no").
```javascript
{ mostrarError && <Text style={{ color: 'red' }}>Algo salió mal</Text> }
```

---

## 9. Ciclo de Renderizado {#ciclo-renderizado}

### ¿Qué es el Renderizado?
Es el proceso donde React convierte tu código en elementos visuales reales en la pantalla.

### Re-render vs Re-mount

#### Re-render
- **¿Qué es?**: El componente vuelve a ejecutar su código interno.
- **Eficiencia**: Es muy eficiente; el componente no se va de la pantalla.
- **Estado**: Mantiene el árbol de componentes (Virtual DOM).
- **Efectos**: Los efectos (`useEffect`) pueden o no volver a ejecutarse según sus dependencias.
- **Objetivo**: Actualizar partes específicas del componente.

#### Re-mount
- **¿Qué es?**: El componente se quita por completo de la pantalla (se desmonta) y se vuelve a crear desde cero.
- **Eficiencia**: Es menos eficiente; consume más recursos.
- **Estado**: **Se pierde el estado local**. Todo vuelve a su valor inicial.
- **Efectos**: Los efectos se ejecutan desde el principio (montaje).

---

## 10. Proyecto Práctico: Mi Primera Todo List {#proyecto-practico}

### Objetivo
Construir una aplicación funcional donde puedas escribir una tarea, agregarla a la lista y borrarla.

### Pasos Generales
1. Crear un estado para el texto del input (`const [tarea, setTarea] = useState("");`).
2. Crear un estado para el arreglo de tareas (`const [lista, setLista] = useState([]);`).
3. Función `agregarTarea`: Toma el texto del input y lo añade al arreglo usando el operador spread `...lista`.
4. Mostrar las tareas usando un `<FlatList>`.
5. Agregar un botón de borrar para cada tarea.

---

## ✅ Tips de Clase

- **Spread Operator (...)**: Úsalo para actualizar arreglos y objetos sin mutarlos (creando una copia).
- **Teclado**: Usa `keyboardType="numeric"` si solo vas a pedir números.
- **Keys**: Asegúrate de que cada item de tu lista tenga una `id` única y estable.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
