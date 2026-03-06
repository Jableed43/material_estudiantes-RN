# Guía Paso a Paso: Tu primera TODO List con Modo Oscuro

## 🎯 Objetivo
Aprenderás a construir una aplicación real de "Lista de Tareas" (TODO List) que responde a lo que el usuario hace e incluso permite cambiar entre tema claro y oscuro.

## 📚 Índice

1. [Estructura y Estados](#estados)
2. [Agregar Tareas](#agregar)
3. [Modo Oscuro](#dark-mode)
4. [Mostrar la Lista con FlatList](#flatlist)

---

## 🏗️ Paso 1: Estructura y Estados {#estados}

Primero, necesitamos que nuestra app "recuerde" tres cosas: las tareas, lo que el usuario escribe, y si el modo oscuro está activo.

```tsx
export default function TodoList() {
  const [tareas, setTareas] = useState([]);      // Nuestra lista
  const [nuevaTarea, setNuevaTarea] = useState(""); // Lo que estamos escribiendo
  const [darkMode, setDarkMode] = useState(false);  // ¿Modo oscuro?
  
  // ... resto del código
}
```

---

## ✍️ Paso 2: Agregar Tareas {#agregar}

Necesitamos una función que tome lo que el usuario escribió y lo meta en la lista.

```tsx
const agregarTarea = () => {
  if (nuevaTarea.trim()) { // Validamos que no esté vacío
    const nueva = {
      id: Date.now().toString(), // Un ID único
      texto: nuevaTarea.trim(),
      completada: false,
    };
    
    setTareas([...tareas, nueva]); // Copiamos lo anterior y agregamos la nueva
    setNuevaTarea(""); // Limpiamos el texto
  }
};
```

---

## 🌙 Paso 3: Implementar el Modo Oscuro {#dark-mode}

Usaremos un `Switch` (interruptor) que cambie el estado de `darkMode`.

```tsx
<Switch
  value={darkMode}
  onValueChange={setDarkMode} // Al tocarlo, darkMode pasa a ser true o false
/>
```

Y para los colores, usamos el estado en los estilos:

```tsx
<SafeAreaView style={[styles.container, darkMode && styles.containerDark]}>
  {/* El segundo estilo solo se aplica si darkMode es true */}
</SafeAreaView>
```

---

## 📜 Paso 4: Mostrar la Lista con FlatList {#flatlist}

Usamos `FlatList` para que la app no se trabe si hay muchas tareas.

```tsx
<FlatList
  data={tareas}
  keyExtractor={(item) => item.id}
  renderItem={({ item }) => (
    <View style={styles.item}>
      <Text>{item.texto}</Text>
      {/* Botón para borrar, etc. */}
    </View>
  )}
/>
```

---

## ✅ Checklist de Aprendizaje
- [ ] ¿Entiendes cómo `useState` guarda la información?
- [ ] ¿Lograste que el modo oscuro cambie el color de fondo?
- [ ] ¿Cada tarea tiene un `id` único?

---

## 💡 Tip Pro: El error del Texto
Recuerda que en React Native NO puedes hacer esto:
`{tareas.length} tareas pendientes` ❌ (Error por texto suelto)

Debes hacer esto:
`{`${tareas.length} tareas pendientes`}` ✅ (Todo dentro de comillas invertidas)

---

**Última actualización:** Marzo 2026 - Tutorial para estudiantes.
