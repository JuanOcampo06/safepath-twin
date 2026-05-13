# SafePath Twin · Gemelo Digital de Riesgo Vial

Prototipo web del proyecto **SafePath Twin** — Hackatón **SafeMotion 26**, Universidad EAN · Sitt & Cía.

Convierte la base abierta del **Anuario de Siniestralidad 2024** de la Secretaría Distrital de Movilidad de Bogotá en un gemelo digital geotemporal que prioriza la prevención sobre micromovilidad (bicicletas y patinetas eléctricas).

## Stack

- HTML5 semántico
- CSS3 (Flexbox / Grid, glassmorphism, animaciones)
- JavaScript ES6+ (sin framework)
- [Leaflet 1.9.4](https://leafletjs.com) + [leaflet.heat](https://github.com/Leaflet/Leaflet.heat) — mapa de calor
- [Chart.js 4.4.1](https://www.chartjs.org) — gráficos
- Tipografías: `Outfit` (display) + `Space Mono` (UI técnica)

## Estructura

```
safepath-twin/
├── index.html      # estructura semántica + carga de librerías
├── style.css       # diseño cyber-tech dark
├── script.js       # lógica, datos embebidos del Excel, mapa y gráficos
└── README.md
```

## Datos

Las agregaciones (totales, hora, mes, localidad, gravedad, clase, factores) y **2.042 coordenadas GPS reales de siniestros con bicicleta** se pre-procesaron desde `Base_Anuario_de_Siniestralidad_2024.xlsx` (filtrando `AA_Acc == 2024`) y se **inyectaron como constante `DATA`** en `script.js`. Esto permite que el prototipo sea estático y se despliegue en Vercel sin backend.

Las secciones del archivo `script.js` están comentadas indicando dónde se inyectan los datos del Excel.

## Despliegue local

Abrir `index.html` directamente en el navegador funciona (Leaflet y Chart.js se cargan vía CDN). Para evitar restricciones de CORS al ampliar el prototipo, lanzar un servidor estático:

```bash
python3 -m http.server 8080
# luego visitar http://localhost:8080
```

## Despliegue en Vercel

1. Subir el repositorio a GitHub.
2. En Vercel: **Import Project** → seleccionar el repo.
3. Framework Preset: **Other** (sitio estático).
4. Build Command: *vacío*. Output Directory: `./` (raíz).
5. Deploy.

No requiere variables de entorno ni build step.

## Fuente

Secretaría Distrital de Movilidad (2025). *Base Anuario de Siniestralidad 2024*. [datos.gov.co](https://datos.gov.co)

---

**Hackatón SafeMotion 26 · Mayo 2026 · Fase 1 — Diagnóstico**
