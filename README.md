# Evaluador de Ideas de Innovación

Sistema web para registrar, visualizar y priorizar ideas de innovación de forma automática.

## 🔗 Links

- **Repositorio:** https://github.com/RichardCode1997/evaluador-ideas
- **Aplicación desplegada:** https://evaluador-ideas.vercel.app

---

## 🚀 ¿Qué hace la aplicación?

- Registrar ideas de innovación con: título, descripción, área, beneficio esperado, esfuerzo estimado e impacto estimado.
- Calcular automáticamente la prioridad (**Alta / Media / Baja**) según la relación impacto/esfuerzo.
- Listar todas las ideas registradas con colores indicadores de prioridad.
- Eliminar ideas del listado.
- Persistencia de datos en `localStorage` (sin backend).

## 🧮 Lógica de Prioridad

| Impacto | Esfuerzo | Prioridad |
|---------|----------|-----------|
| Alto    | Bajo     | Alta      |
| Alto    | Medio    | Alta      |
| Alto    | Alto     | Media     |
| Medio   | Bajo     | Media     |
| Medio   | Medio    | Media     |
| Medio   | Alto     | Baja      |
| Bajo    | Bajo     | Media     |
| Bajo    | Medio    | Baja      |
| Bajo    | Alto     | Baja      |

> El impacto tiene mayor peso que el esfuerzo en la priorización.

---

## 🛠️ Tecnologías

- Vue.js 3 (Composition API)
- Vue Router
- localStorage
- CSS personalizado

## ▶️ Instalación local

```bash
git clone https://github.com/RichardCode1997/evaluador-ideas
cd evaluador-ideas
npm install
npm run dev
```

---

## 🤖 Uso de IA durante el desarrollo

Se utilizó **Claude (Anthropic)** como asistente principal durante todo el desarrollo:

- Generación de la estructura inicial del proyecto y componentes Vue.
- Definición y ajuste de la lógica de cálculo de prioridad.
- Sugerencia de estilos CSS y mejoras de UX (colores por prioridad, tabla responsiva).
- Resolución de errores en tiempo real (capitalización, validaciones, localStorage).
- Redacción de este README.

---

## 🔧 ¿Qué mejoraría con más tiempo?

1. **Editar ideas** — botón para modificar una idea existente con formulario pre-cargado.
2. **Filtrar y ordenar** — por prioridad, impacto o esfuerzo.
3. **Confirmación al eliminar** — evitar borrados accidentales con un `confirm()`.
4. **Validación completa** — marcar impacto y esfuerzo como campos obligatorios.
5. **Fecha de registro** — guardar cuándo fue creada cada idea.
6. **Contador por prioridad** — resumen tipo `Alta: 3 | Media: 5 | Baja: 2`.
7. **Exportar a CSV** — para compartir el listado sin acceso a la app.