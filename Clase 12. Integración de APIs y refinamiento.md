# Clase 12. Integración de APIs y refinamiento

## 📚 Índice

1. [Consumo Profesional de APIs (Axios vs Fetch)](#apis-pro)
2. [¿Qué es un Endpoint? (URLs con propósito)](#endpoints)
3. [El Ciclo de Iteración (Mejorar sin cesar)](#iteracion)
4. [QA básico: Mi primera auditoría de calidad](#qa)
5. [Checklist antes de lanzar el MVP](#checklist)
6. [Variables de Entorno (.env)](#dotenv)
7. [Proyecto Práctico: Perfeccionando mi App](#proyecto-practico)
8. [Resumen y Consejos Finales](#resumen)

---

## 1. Consumo Profesional de APIs {#apis-pro}

Para que tu app no se rompa al buscar datos, usaremos **Axios** o **Fetch** con inteligencia:

| Herramienta | Cuándo usarla | Beneficio |
|-------------|---------------|-----------|
| **Fetch** | Apps simples | Nativo en JS, sin instalar nada. |
| **Axios** | Apps reales | Maneja JSON solo, intercepta solicitudes, cancela pedidos. |

### Axios Interceptors
Podemos decirle a Axios que haga algo **siempre** antes de una llamada (ej: inyectar el token de usuario):

```javascript
axios.interceptors.request.use(config => {
  config.headers.Authorization = `Bearer ${token}`;
  return config;
});
```

---

## 2. Endpoints y URLs con propósito {#endpoints}

No pongas la URL entera a mano en cada archivo. Centralízala:

```javascript
// ✅ En un archivo central baseAPI.js
export const API_BASE = "https://api.tu-servidor.com";
```

- **GET /tasks**: Pido lista.
- **POST /tasks**: Envío nueva.
- **DELETE /tasks/5**: Borro específica.

---

## 3. Iteración y Refinamiento {#iteracion}

Programar es un proceso circular:
1. **Andar**: Que la función básica funcione.
2. **Ajustar**: ¿Se ve bien? ¿Es intuitivo?
3. **Refinar**: Agregamos un mensaje de "No hay conexión" o un error de validación.

---

## 4. Control de Calidad (QA) {#qa}

El **QA** no es opcional. Debes probar tu app como si fueras un usuario que no sabe nada:
- **Smoke test**: ¿Se abre la app o crashea?
- **Happy Path**: ¿Funciona el flujo principal del punto A al B?
- **Manejo de errores**: ¿Qué pasa si el servidor devuelve un error 500?

---

## 5. Checklist antes de lanzar {#checklist}

Antes de mandarle el link a un cliente:
- [ ] ¿Tiene un ícono (no el de Expo por defecto)?
- [ ] ¿Tiene Splash Screen (pantalla de inicio)?
- [ ] ¿Tiene un loader (circulito girando)?
- [ ] ¿Las variables delicadas están en un `.env`?

---

## 6. Proyecto Práctico: Perfeccionando mi App {#proyecto-practico}

### Objetivo
Llevar tu proyecto final al segundo nivel: conectar con datos reales, manejar errores profesionalmente y asegurar la calidad.

### Pasos Generales
1. Configurar una URL base para tu API.
2. Implementar un interceptor para manejar errores globales (ej: "Error de red").
3. Realizar un ciclo de QA: detectar 3 bugs visuales y arreglarlos.
4. Mover todas las claves de API a un archivo `.env`.

### Resultado Final
Una aplicación robusta, segura y lista para ser mostrada en un portfolio.

---

## ✅ Tips de Clase

- ✅ **Try/Catch**: Siempre rodea tus llamadas a la API con bloques de error.
- ✅ **Loader**: Si tarda 1 segundo en cargar, pon un `ActivityIndicator`. El usuario agradece saber que algo está pasando.
- ✅ **AsyncStorage local**: Guarda lo que pediste a la API para que la próxima vez abra más rápido.

---

**Última actualización:** Marzo 2026 - Guía de aprendizaje unificada.
