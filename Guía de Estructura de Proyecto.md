# Guía: Estructura de Proyecto en React Native (Expo)

## 📚 Índice

1. [Archivos de Configuración](#configuracion)
2. [La Carpeta `app/` (Páginas y Navegación)](#carpeta-app)
3. [Componentes y Hooks](#componentes-hooks)
4. [Recursos Estáticos (`assets/`)](#assets)
5. [Resumen de la Estructura](#resumen)

---

## 1. Archivos de Configuración {#configuracion}

Cuando creas un proyecto con Expo, verás varios archivos en la carpeta raíz. Aquí te explico para qué sirven los más importantes:

### 📄 `package.json`
Es el "DNI" de tu proyecto. Aquí están los nombres de las librerías que usas y los comandos para arrancar la app (`npm start`, `npm run android`, etc.).

### 📄 `app.json`
Es la configuración de **Expo**. Aquí defines el nombre de la app que verá el usuario, el icono que aparecerá en el celular y la versión.

### 📄 `tsconfig.json`
Si usas TypeScript (que es lo recomendado), este archivo le dice a la computadora cómo debe revisar tu código para encontrar errores antes de que la app corra.

---

## 2. La Carpeta `app/` (Páginas y Navegación) {#carpeta-app}

En Expo Router, las carpetas y archivos dentro de `app/` definen automáticamente las pantallas de tu aplicación.

- **`_layout.tsx`**: Es el "esqueleto" principal. Lo que pongas aquí se verá en todas las pantallas (como un menú o una barra superior).
- **`(tabs)/`**: Las carpetas con paréntesis no aparecen en la URL o ruta, se usan para agrupar. En este caso, agrupan las pantallas que tienen los botones de navegación abajo.
- **`index.tsx`**: Es la pantalla de inicio (la primera que se abre).

---

## 3. Componentes y Hooks {#componentes-hooks}

### 📂 `components/`
Aquí debes guardar tus piezas de LEGO personalizadas. Por ejemplo, si creas un botón especial que se usa en 5 pantallas, guárdalo aquí como `BotonEspecial.tsx`.

### 📂 `hooks/`
Aquí van funciones especiales que manejan lógica (como pedir datos a una API o manejar el modo oscuro) para que no ensucien el código de tus pantallas.

---

## 4. Recursos Estáticos (`assets/`) {#assets}

Aquí es donde guardas todo lo que no es código:
- **Imágenes y Fotos**: Dentro de `assets/images`.
- **Iconos**: El icono de la app (`icon.png`).
- **Splash Screen**: La imagen que se ve mientras la app carga (`splash-icon.png`).

---

## 5. Resumen de la Estructura {#resumen}

```text
MiApp/
├── app/            # 📱 Pantallas de la aplicación
├── assets/         # 🖼️ Imágenes e iconos
├── components/     # 🧩 Piezas reutilizables
├── constants/      # 🎨 Colores y estilos globales
├── package.json    # 📦 Listado de librerías
└── app.json        # ⚙️ Configuración de Expo
```

### 💡 Tip para Estudiantes:
Si te sientes perdido, recuerda que el **90% de tu tiempo** estarás dentro de la carpeta `app/` creando pantallas y en `components/` creando piezas para esas pantallas.

---

**Última actualización:** Marzo 2026 - Guía de estructura para estudiantes.
