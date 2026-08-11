# Prototipo integral — Pricing Intelligence

## Qué se entrega
1. `dashboard_prototipo.html`: dashboard interactivo local con KPIs, tabla de pricing, insights, documento ejecutivo y prompt.
2. `datos_demo.json`: datos sintéticos para probar el flujo sin inventar datos del proyecto.
3. `prompt_ia_generativa.txt`: prompt listo para usar en un módulo de IA.
4. `automatizacion_make.md`: pasos para montar el escenario en Make.

## Herramienta recomendada
Para la demostración no-code, usar Make + Google Sheets. Make tiene plan Free sin límite de tiempo y actualmente indica 1.000 créditos/mes, constructor visual, routers/filtros e integraciones; además dispone de herramientas de IA y agentes. El flujo puede conectarse con Google Sheets, un módulo de IA, y servicios de salida.

## Paso a paso del prototipo
### A. Preparar Google Sheets
Crear una hoja `productos_consolidados` con las columnas:
producto, marca, categoria, precio, ml, precio_ml, competidor_precio, posicion_gondola, packaging, discrepancia_pct, alerta, visual_score.

Pegar el CSV real del proyecto cuando esté disponible. Durante la prueba se puede usar `datos_demo.json`.

### B. Crear el escenario en Make
1. Crear cuenta gratuita.
2. Crear un nuevo Scenario.
3. Trigger: Google Sheets → Watch Rows.
4. Tools → JSON / Text aggregator para reunir los registros que se van a analizar.
5. AI: utilizar Make AI Toolkit o Make AI Agent con el prompt de `prompt_ia_generativa.txt`.
6. Reemplazar `{{JSON_DE_DATOS_CONSOLIDADOS}}` por el array JSON generado en el paso anterior.
7. Parsear la respuesta JSON.
8. Router con tres ramas:
   - Dashboard: escribir KPIs/hallazgos en una hoja `dashboard`.
   - Documento ejecutivo: crear un documento/archivo con el resumen y recomendaciones.
   - Alertas: filtrar `prioridad = ALTA` y enviar una notificación.
9. Rama final: guardar `decisiones_marketing` en una hoja `decisiones`.
10. Ejecutar una prueba con 3–6 productos.
11. Revisar el historial de ejecución y verificar que cada módulo reciba la salida esperada.

### C. Computer Vision
Las fotos reales de góndola deben producir primero variables estructuradas, por ejemplo:
- producto detectado
- posición
- precio visible
- packaging
- presencia de marca
- competidores

Esas variables se incorporan a `productos_consolidados`. La IA generativa no debe "adivinar" lo que aparece en una foto: debe trabajar sobre las variables detectadas por Computer Vision o sobre una salida validada.

### D. Salidas
Dashboard:
- productos analizados
- precio medio/ml
- alertas
- oportunidades
- ranking de discrepancias
- comparación competitiva

Documento ejecutivo:
- resumen
- principales hallazgos
- alertas prioritarias
- recomendaciones
- decisiones sugeridas

Alertas:
- prioridad alta
- producto
- evidencia
- impacto
- acción

Decisiones:
- pricing
- posicionamiento
- promociones

## Prueba mínima para la entrega
Usar 2 ejemplos diferentes, tal como pide la consigna, y conservar capturas de:
1. Datos de entrada.
2. Prompt + datos enviados a la IA.
3. Respuesta estructurada.
4. Resultado en dashboard.
5. Documento ejecutivo.
6. Alerta generada.
7. Decisión de marketing.

## Criterio de validación humana
La IA propone. El responsable de marketing valida antes de modificar precios o ejecutar promociones.

## Nota
El dashboard HTML incluido es una demostración local y usa datos sintéticos. Para la entrega académica, reemplazar esos datos por el dataset real y conservar evidencia de las pruebas.
