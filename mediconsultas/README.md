# MEDICONSULTAS

Orientación médica por áreas (al estilo de un buscador legal por materias), con IA de Claude.

- **Áreas médicas:** Medicina General, Broncopulmonar, Cardiología, Gastroenterología, Traumatología, Dermatología, Neurología, Otorrino, Oftalmología, Urología, Ginecología, Pediatría, Geriatría, Endocrinología, Salud Mental, Infectología, Reumatología y Odontología. Cada una tiene una ficha con señales de alarma y afecciones frecuentes.
- **Consultas puntuales:** "tengo dolor en la rodilla", "me salió un grano rojo"… La IA clasifica el área, marca el nivel de urgencia (emergencia / pronto / pedir hora / autocuidado) y orienta.
- **Fotos:** se pueden adjuntar hasta 3 imágenes por consulta (desde el celular abre la cámara).
- **Seguridad:** detección de emergencias en el servidor (dolor de pecho, ACV, ideas suicidas → 131 / *4141), aviso legal y límite de consultas por hora.

## Publicar en Render (una sola vez)

1. Entrar a https://render.com e iniciar sesión con GitHub.
2. **New + → Blueprint** → elegir el repositorio `-amazona-crm` y la rama donde está este código.
3. Render lee `render.yaml` (en la raíz del repo) y pide el valor de `ANTHROPIC_API_KEY`: pegar la clave creada en https://console.anthropic.com → API Keys.
4. **Apply**. En 2-3 minutos queda la URL pública `https://mediconsultas-xxxx.onrender.com`.

Sin la clave la app funciona en **modo demostración** (muestra las fichas y alarmas, pero sin IA).

> Plan gratuito de Render: el servicio "se duerme" tras 15 minutos sin uso y tarda ~50 s en despertar.

## Ejecutar en el computador

```bash
cd mediconsultas
npm install
ANTHROPIC_API_KEY=tu_clave npm start
# abrir http://localhost:3000
```

## Variables

| Variable | Uso |
|---|---|
| `ANTHROPIC_API_KEY` | Clave de la API de Claude (obligatoria para la IA) |
| `CLAUDE_MODEL` | Modelo (por defecto `claude-opus-5-5`) |
| `RATE_LIMIT_PER_HOUR` | Consultas por hora por IP (por defecto 30) |

## Ampliar el conocimiento

Editar `data/areas.js`: agregar áreas, afecciones, palabras clave o señales de alarma. Todo se refleja en las fichas y en lo que sabe la IA.
Usar solo contenido propio o de fuentes abiertas (MINSAL, MedlinePlus, OMS); no copiar libros con derechos de autor.

## Aviso

MEDICONSULTAS entrega orientación general y no reemplaza la consulta médica. Las imágenes no se guardan en el servidor.
