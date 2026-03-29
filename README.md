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

## Estructura del proyecto

```text
.
├── tef-oral-simulator.html   # App completa: HTML + CSS + JS
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

- Es una app **100% front-end** en un solo archivo.
- Las llamadas a IA están en cliente (no ideal para producción).
- Para producción real, se recomienda backend intermedio para gestionar API keys y validación de respuestas.

## Recomendaciones técnicas para producción

- Mover llamadas IA a un backend (`/api/toolkit`, `/api/analyze`).
- Guardar API keys en variables de entorno del servidor.
- Agregar validación fuerte del JSON de respuesta (schema).
- Separar en módulos (`styles.css`, `app.js`, `data/*.js`).

## Idiomas

- Interfaz mixta **francés + español**.
- Feedback y recomendaciones en ambos idiomas según sección.

## Licencia

Sin licencia definida actualmente.
