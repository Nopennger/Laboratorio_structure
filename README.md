# Laboratorio virtual de flexión

Aplicación web educativa para estudiar la flexión de una viga prismática simplemente apoyada con una carga puntual centrada.

## Funciones

- Flujo guiado: iniciar, configurar, explorar resultados y concluir.
- Controles interactivos para la carga puntual `P`, la longitud del vano `L` y el módulo elástico `E`.
- Visualización de la deformada cualitativa, diagramas de cortante y momento, y resultados numéricos con unidades.
- Guía de uso, modelo físico, variables, ecuaciones y limitaciones.
- Diseño adaptable a teléfonos y computadores. No necesita cuenta ni servidor.

## Abrir la aplicación

No requiere compilación ni instalación de dependencias.

1. Descarga el proyecto y conserva `assets` junto a `index.html`.
2. Abre `index.html` en un navegador moderno.
3. Ten conexión a internet para que se carguen Tailwind CSS y Chart.js desde sus CDN.

Opcionalmente, inicia un servidor local en la carpeta del proyecto:

```powershell
py -m http.server 8000
```

Abre <http://localhost:8000>. Si Python no está instalado, puedes abrir `index.html` directamente.

## Uso del laboratorio

1. Pulsa **Iniciar experimento**.
2. Cambia uno o más parámetros: carga `P`, longitud `L` y material.
3. Compara los gráficos y resultados actualizados.
4. Pulsa **Finalizar y ver conclusión**.
5. Pulsa **Reiniciar experimento** para probar otra configuración.
6. Consulta **Guía y modelo** para revisar el procedimiento y las ecuaciones.

## Modelo físico

Se asume una viga prismática, simplemente apoyada, con carga puntual centrada, sección rectangular constante y comportamiento elástico lineal.

- Cortante máximo: `V_máx = P / 2`
- Momento flector máximo: `M_máx = P L / 4`
- Deflexión central: `δ = P L³ / (48 E I)`
- Momento de inercia: `I = b h³ / 12`
- Sección: `b = 0,10 m`, `h = 0,20 m`, `I ≈ 6,67 × 10⁻⁵ m⁴`

La aplicación acepta `P` en kN, `L` en m y `E` en GPa; convierte las cantidades a unidades SI para el cálculo y presenta la deflexión en mm, el cortante en kN y el momento en kN·m. Los módulos elásticos didácticos son: acero 200 GPa, aluminio 70 GPa, madera 12 GPa y concreto 25 GPa.

## Arquitectura

```text
Controles P, L y E
        ↓
Cálculo del modelo en JavaScript dentro del navegador
        ↓
Resultados teóricos: deflexión, cortante y momento
        ↓
Canvas: deformada ─── Chart.js: diagramas ─── Tabla y conclusión
```

- HTML5 y JavaScript: interfaz, navegación y cálculos.
- Tailwind CSS (CDN): estilos adaptables.
- Canvas 2D: representación visual magnificada de la deformada.
- Chart.js (CDN): gráficos con ejes y unidades.
- No usa sensores, backend ni base de datos. No guarda ni envía resultados.

Es un modelo educativo y no verifica resistencia, pandeo, fisuración ni condiciones reales de diseño; no reemplaza un análisis estructural.

## Archivos principales

- `index.html`: aplicación web.
- `assets/logo-universidad-mayor.webp`: logo institucional.

El logo se obtuvo del [sitio oficial de la Universidad Mayor](https://www.umayor.cl/um/bundles/umayor/images/header-logo.webp). Respeta sus directrices de marca y confirma que su uso esté autorizado.
