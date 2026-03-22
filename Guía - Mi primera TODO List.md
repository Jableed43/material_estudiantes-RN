# Guía Paso a Paso: Tu primera TODO List con Modo Oscuro

## 🎯 Objetivo

#### ¿Qué es una TODO List?
Es el proyecto clásico de todo programador: una "Lista de Tareas". Sirve para practicar cómo crear, leer, editar y borrar información (CRUD) de forma interactiva.

Aprenderás a construir una aplicación real de "Lista de Tareas" (TODO List) que responde a lo que el usuario hace e incluso permite cambiar entre tema claro y oscuro, aplicando los conceptos de hooks, eventos y componentes nativos.

## 📚 Índice

1. [Paso 1: Estructura y Estados](#paso-1)
2. [Paso 2: Header y Switch de Dark Mode](#paso-2)
3. [Paso 3: Agregar Tareas](#paso-3)
4. [Paso 4: Tareas Pendientes (Valores Derivados)](#paso-4)
5. [Paso 5: Listado con FlatList](#paso-5)
6. [Paso 6: Checkbox y Eliminar](#paso-6)
7. [Checklist Final](#checklist)

---

## 🏗️ Paso 1: Estructura y Estados {#paso-1}

#### ¿Qué es un Estado en un Proyecto Real?
Es la forma en que la aplicación "siente" y "recuerda" lo que está pasando. Si no tuviéramos estados, la lista de tareas estaría siempre vacía y el input no escribiría nada.

Necesitamos que nuestra app "recuerde" tres cosas: las tareas, lo que el usuario escribe, y si el modo oscuro está activo.

```tsx
// Definimos el tipo de dato para una tarea
interface Tarea {
  id: string;
  texto: string;
  completada: boolean;
}

export default function TodoList() {
  const [tareas, setTareas] = useState<Tarea[]>([]); // Nuestra lista
  const [nuevaTarea, setNuevaTarea] = useState("");   // Lo que estamos escribiendo
  const [darkMode, setDarkMode] = useState(false);    // ¿Modo oscuro activado?
  
  // El fondo cambiará según el estado darkMode
  return (
    <SafeAreaView style={[styles.container, darkMode && styles.containerDark]}>
      {/* Contenido de la app */}
    </SafeAreaView>
  );
}
```

---

## 🌙 Paso 2: Header y Switch de Dark Mode {#paso-2}

Usaremos un `Switch` (interruptor) que cambie el estado de `darkMode`.

```tsx
<View style={styles.header}>
  <Text style={[styles.titulo, darkMode && styles.tituloDark]}>Mis Tareas</Text>
  <Switch
    value={darkMode}
    onValueChange={setDarkMode} // Al tocarlo, darkMode pasa a ser true o false
  />
</View>
```

---

## ✍️ Paso 3: Agregar Tareas {#paso-3}

#### ¿Qué es la Inmutabilidad?
Es una regla de React que dice: "No rompas lo que ya existe, crea una copia nueva con el cambio". En vez de agregar una tarea a la lista vieja, creamos una lista nueva que contiene las tareas viejas más la nueva.

#### ¿Qué es un Identificador Único (ID)?
Es un "documento de identidad" para cada elemento de tu lista. Sirve para que React no se confunda si dos tareas dicen exactamente lo mismo (ejemplo: dos tareas que digan "Comprar pan").

Usamos una función que valida que el texto no esté vacío, crea un objeto nuevo y lo agrega al array sin modificar el original (**inmutabilidad**).

```tsx
const agregarTarea = () => {
  if (nuevaTarea.trim()) { 
    const nueva = {
      id: Date.now().toString(), // ID único basado en el tiempo
      texto: nuevaTarea.trim(),
      completada: false,
    };
    
    // Spread operator (...) para copiar lo anterior y agregar la nueva
    setTareas([...tareas, nueva]); 
    setNuevaTarea(""); // Limpiamos el input
  }
};
```

Conecta esto a tu `TextInput`:
```tsx
<TextInput
  value={nuevaTarea}
  onChangeText={setNuevaTarea}
  onSubmitEditing={agregarTarea} // Agrega al presionar Enter en el teclado
  placeholder="Escribe una tarea..."
/>
```

---

## 📊 Paso 4: Tareas Pendientes {#paso-4}

#### ¿Qué es un Valor Derivado?
Es un dato que calculamos "al vuelo" usando información que ya tenemos en los estados. No hace falta crear un estado para el total de tareas si ya tenemos la lista de tareas; simplemente las contamos.

No hace falta un nuevo estado para contar. Podemos calcularlo en cada renderizado.

```tsx
const pendientes = tareas.filter(t => !t.completada).length;

// En el texto, usa comillas invertidas para evitar errores:
<Text>{`${pendientes} tareas pendientes`}</Text>
```

---

## 📜 Paso 5: Listado con FlatList {#paso-5}

`FlatList` es mucho más eficiente que un ScrollView para listas.

```tsx
<FlatList
  data={tareas}
  keyExtractor={(item) => item.id}
  renderItem={({ item }) => (
    <View style={[styles.item, darkMode && styles.itemDark]}>
      <Text style={[styles.texto, item.completada && styles.tachado]}>
        {item.texto}
      </Text>
      {/* Aquí irán los botones de Check y Eliminar (Paso 6) */}
    </View>
  )}
/>
```

---

## ✅ Paso 6: Checkbox y Eliminar {#paso-6}

Para marcar como completada o borrar, usamos métodos de array que no modifican el original:

- **Marcar/Desmarcar**: Usamos `.map()` para cambiar solo esa tarea.
- **Eliminar**: Usamos `.filter()` para quitar esa tarea.

```tsx
const toggleTarea = (id) => {
  setTareas(tareas.map(t => t.id === id ? { ...t, completada: !t.completada } : t));
};

const eliminarTarea = (id) => {
  setTareas(tareas.filter(t => t.id !== id));
};
```

---

## ✅ Checklist Final {#checklist}
- [ ] ¿El fondo cambia al tocar el Switch?
- [ ] ¿El input se limpia después de agregar una tarea?
- [ ] ¿El contador de pendientes se actualiza al tachar una tarea?
- [ ] ¿Usaste `keyExtractor` con un ID único?

---

### 💡 Tip Pro: El error del Texto
React Native no permite texto "suelto" (fuera de `<Text>`). Si ves el error *"Text strings must be rendered within a <Text> component"*, revisa que no tengas espacios vacíos o variables de texto fuera de sus etiquetas.

---

**Última actualización:** Marzo 2026 - Guía paso a paso unificada.
