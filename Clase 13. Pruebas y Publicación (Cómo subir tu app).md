# Clase 13. Pruebas y Publicación (Cómo subir tu app)

## 📚 Índice

1. [Testing: Que la app se pruebe sola](#testing)
2. [¿Qué es un Build?](#build)
3. [EAS: Tu fábrica de apps en la nube](#eas)
4. [Subiendo a las tiendas (Play Store y App Store)](#tiendas)
5. [Versiones y Permisos](#versiones)
6. [Resumen](#resumen)

---

## 1. Testing: Que la app se pruebe sola {#testing}

No puedes probar cada botón de tu app manualmente cada vez que cambias algo. Para eso existe el **Testing Automático**.
Usamos una herramienta llamada **Jest**.

**¿Qué probamos?**
- Que al tocar el botón de "Login", se llame a la función correcta.
- Que si el usuario no pone su nombre, aparezca un mensaje de error.
- Que las cuentas matemáticas de la app den el resultado correcto.

---

## 2. ¿Qué es un Build? {#build}

Hasta ahora, tu app corre dentro de "Expo Go". Un **Build** es convertir tu código en un archivo real que se puede instalar en cualquier teléfono:
- **Android**: Se genera un archivo `.apk` o `.aab`.
- **iOS**: Se genera un archivo `.ipa`.

---

## 3. EAS: Tu fábrica en la nube {#eas}

Generar el archivo para iPhone solía requerir una computadora Mac carísima. Con **EAS (Expo Application Services)**, le enviamos nuestro código a las computadoras de Expo y ellos nos devuelven la app lista para usar.

**Comando mágico:**
`eas build --platform android` (Crea tu app para Android en 10 minutos).

---

## 4. Subiendo a las tiendas {#tiendas}

Para que el mundo vea tu app, debes subirla a las tiendas oficiales.

- **Google Play Store**: 
  - Cuesta **$25 USD** una sola vez.
  - Es más permisiva con lo que subes.
- **App Store (Apple)**: 
  - Cuesta **$99 USD** CADA año.
  - Son muy estrictos: tu app debe ser perfecta y útil para que la acepten.

---

## 5. Versiones y Permisos {#versiones}

- **Versionado**: Empiezas en la `1.0.0`. Si arreglas un error, subes a la `1.0.1`. Si agregas una función nueva, vas a la `1.1.0`.
- **Permisos**: Antes de publicar, revisa que no estés pidiendo permisos que no usas. Si pides permiso de GPS y tu app es una calculadora, ¡Google te la puede rechazar!

---

## ✅ Últimos consejos antes de lanzar {#consejos}

1. **Prueba en un celular real**: Los simuladores de la PC mienten. Prueba en tu propio teléfono.
2. **Icono y Splash**: Asegúrate de tener un lindo logo y una pantalla de bienvenida que no se vea pixelada.
3. **Privacidad**: Hoy en día es obligatorio tener un link a tus "Políticas de Privacidad" para poder publicar.

---

## 📝 Resumen {#resumen}

### Conceptos Clave Aprendidos
1. **Jest**: Tu robot de pruebas.
2. **EAS Build**: Crear el archivo instalable.
3. **Stores**: El paso final para ser un desarrollador profesional.

### Próximos Pasos
- ¿Ya tienes tu cuenta de desarrollador? ¡Es el primer paso para convertir tu hobby en un trabajo real!

---

**Última actualización:** Marzo 2026 - Guía para estudiantes.
