# Radar territorial · Alcaldía de Zipaquirá

**[Abrir la aplicación](https://javier-galindobernal.github.io/radar-territorial-alcaldia-zipaquira/)** · [Guía de uso](https://javier-galindobernal.github.io/radar-territorial-alcaldia-zipaquira/guia.html)

Prototipo de análisis territorial de incidentes reportados, con identidad visual de referencia para la Alcaldía de Zipaquirá. Lema: **Zipaquirá Cree, Protege y Avanza 2024-2028**. No acredita adopción institucional ni presenta estadísticas oficiales de delitos.

Realizado por **GLOBAL ANALITIK SAS y QUANTIKA IA SAS — Javier Galindo**.

## Qué permite probar

- Mapa de comunas, barrios, centros poblados y veredas, con extensión municipal urbana y rural.
- San Miguel identificado como **centro poblado rural**, según la fuente geográfica; no se presenta como barrio urbano ni se le inventa comuna o vereda de pertenencia.
- Mapa de calor por conteo de incidentes únicos, filtros, búsqueda, ranking y controles de acercamiento.
- Simulaciones de 600, 1.200 o 2.400 hechos completamente sintéticos, con fuentes duplicadas para probar la deduplicación. Nombres geográficos reales de referencia; casos y coordenadas de ejemplo inventados.
- Registro manual o importación de CSV, validación, deduplicación por ID del incidente y exportación de los registros de trabajo.

La escala del mapa se recalcula para cada selección; no expresa tasas, predicciones ni niveles de riesgo. Los incidentes reportados no son delitos judicialmente probados.

## Datos y almacenamiento

La portada inicia con una simulación si no hay registros de trabajo. La simulación permanece separada: no se guarda ni se exporta como datos de trabajo.

Los registros de trabajo se guardan **solo en el navegador y dispositivo que los captura**, mediante una clave exclusiva de esta versión. No existe base de datos central, sincronización entre equipos ni conexión automática con Facebook o Policía. Usa la exportación para respaldarlos. El repositorio incluye únicamente la [plantilla CSV vacía](docs/plantilla-incidentes.csv).

No registrar nombres, documentos, teléfonos, perfiles o domicilios de víctimas. Ubicar únicamente el lugar del hecho sustentado en la fuente. No se infieren preferencias políticas ni se generan perfiles de personas.

## Cartografía y límites

| Capa | Contenido y limitación |
| --- | --- |
| Comunas | 5 polígonos de referencia, edición declarada 2014. |
| Barrios y sectores | 191 polígonos de referencia, edición declarada abril de 2026. No todos son jurídicamente barrios. |
| Veredas | 14 polígonos de referencia, edición declarada julio de 2013. La publicación reciente del catálogo no actualiza la geometría histórica. |
| San Miguel | Polígono adicional de centro poblado rural de IDER, datos editados en 2022; licencia CC BY 4.0 declarada por el servicio. |

Las capas de comunas, barrios y veredas son republicaciones académicas con origen municipal declarado. No constituyen una certificación vigente de la división administrativa. No se mezclan catálogos veredales discrepantes. La capa de San Miguel se conserva separada para no atribuirle una pertenencia territorial no documentada.

Consulta fuentes, URLs, fechas y limitaciones completas en [fuentes urbanas](docs/fuentes-zonas.json), [fuentes rurales](docs/fuentes-rural.json) y [catálogo territorial](docs/cartografia.json). La publicación de las fuentes sin licencia declarada no equivale a otorgar una licencia de reutilización.

Los colores verde y verde claro toman como referencia los valores observados en el [portal municipal](https://www.zipaquira-cundinamarca.gov.co/) el 18 de noviembre de 2026; no se presentan como especificaciones de un manual de identidad. Más información: [paleta](referencias/paleta-institucional.md) y [versión Alcaldía](referencias/version-alcaldia.md).

## Ejecutar y verificar

La web no necesita instalación de paquetes, claves ni servicios externos. Usa HTML, CSS, módulos JavaScript y GeoJSON locales.

```sh
python3 -m http.server 8000 --directory docs
```

Abre `http://localhost:8000`. Los módulos y las geometrías requieren HTTP; abrir el HTML como archivo puede impedir su carga.

Con Node.js instalado, ejecuta las pruebas de validación, deduplicación, filtrado, geometría, simulación y análisis rural:

```sh
node --test tests/*.test.mjs
```

## Publicación en GitHub Pages

GitHub Pages publica la carpeta **`docs/` de la rama `main`**, con `.nojekyll` para servir los archivos estáticos. Las rutas son relativas y funcionan bajo el nombre del repositorio. Los cambios publicados en esa carpeta se despliegan desde esa misma rama.

La documentación y las pruebas viven fuera de la carpeta pública. No se incluyen credenciales, correspondencia, registros de trabajo ni datos personales.
