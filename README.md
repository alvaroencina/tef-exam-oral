# TEF Oral Simulator

Simulador web para practicar la **Expresión Oral del TEF Canada** con enfoque en estudiantes hispanohablantes nivel **B1 → B2**.

## Qué incluye

- Flujo completo de 3 partes:
  1. **Monólogo** (preparación + exposición)
  2. **Diálogo** (rol/interacción)
  3. **Comprensión oral** (respuesta a preguntas)
- Grabación de audio local con `MediaRecorder` (o modo simulación sin micrófono).
- Temporizadores por fase.
- Toolkit lingüístico (conectores, vocabulario, frases y expresiones B2/C1).
- Pantalla final de análisis con criterios TEF, feedback bilingüe y vocabulario sugerido.
- Modo fallback/demo cuando falla la generación IA.

## Arquitectura actual (post-refactor)

El proyecto **ya no es monolítico**. Está dividido en capas claras:

- `tef-oral-simulator.html`: estructura de pantallas y markup.
- `styles.css`: estilos y responsive.
- `app.js`: lógica de flujo (timers, grabación, toolkit, análisis, navegación).

## Estructura del proyecto

```text
.
├── tef-oral-simulator.html   # Estructura y vistas HTML
├── styles.css                # Estilos globales
├── app.js                    # Lógica de negocio/UI
└── README.md                 # Documentación
```

## Ejecución local

No requiere build ni dependencias.

```bash
# Opción 1
open tef-oral-simulator.html

# Opción 2 (recomendada para permisos/micrófono)
python3 -m http.server 8080
# luego abrir http://localhost:8080/tef-oral-simulator.html
```

## Funcionamiento general

1. Seleccionas una o más categorías de temas.
2. Comienza la preparación del monólogo.
3. Grabas monólogo, luego diálogo y comprensión.
4. El sistema intenta generar:
   - toolkit temático
   - análisis y puntuación final
5. Si la IA falla, la app usa datos fallback/mock para mantener la experiencia.

## Limitaciones actuales

- Es una app **100% front-end** (sin backend).
- Las llamadas a IA están en cliente (no ideal para producción).
- Para producción real, se recomienda backend intermedio para gestionar API keys y validación de respuestas.

## Recomendaciones técnicas para producción

- Mover llamadas IA a un backend (`/api/toolkit`, `/api/analyze`).
- Guardar API keys en variables de entorno del servidor.
- Agregar validación fuerte del JSON de respuesta (schema).
- Como siguiente paso, dividir `app.js` en submódulos (`data/`, `services/`, `ui/`, `state/`).

## Idiomas

- Interfaz mixta **francés + español**.
- Feedback y recomendaciones en ambos idiomas según sección.

## Licencia

Sin licencia definida actualmente.
