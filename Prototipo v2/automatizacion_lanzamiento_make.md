# AUTOMATIZACIÓN — LANZAMIENTO DE NUEVO PRODUCTO

## Herramienta
Make + Google Sheets + módulo de IA Generativa. Make mantiene un plan Free sin límite de tiempo; su página de precios informa 1.000 créditos/mes y un intervalo mínimo de 15 minutos para escenarios programados. 

## Flujo

Google Sheets / formulario
  ↓
Validar categoría + ml
  ↓
Buscar comparables en dataset
  ↓
Calcular predicción base reproducible
  ↓
IA Generativa interpreta la predicción
  ↓
Parse JSON
  ├── Dashboard
  ├── Documento ejecutivo
  ├── Alerta / validación
  └── Decisión de marketing

## Módulos sugeridos

1. Trigger:
   - Google Sheets → Watch New Rows
   - o un formulario que escriba una fila en Google Sheets.

2. Validación:
   - categoría debe existir en la tabla de categorías.
   - ml debe ser > 0.
   - si no cumple, detener el escenario y generar error de validación.

3. Datos:
   - Google Sheets → Search Rows / Get Range Values.
   - Filtrar por categoria_nueva.

4. Predicción:
   - Tools → Set multiple variables.
   - Ordenar/seleccionar comparables.
   - Calcular precio equivalente y mediana.
   - Guardar precio, rango y nivel de confianza.

5. IA:
   - Make AI Toolkit / Gemini / otro módulo de IA disponible.
   - Insertar `prompt_prediccion_precio.txt`.
   - Mapear categoria_nueva, ml_nuevo, prediccion_base y comparables JSON.

6. Parseo:
   - JSON Parse.
   - Validar que existan prediccion, racional, evidencia, limitaciones y decision_marketing.

7. Router:
   - Dashboard → registrar predicción y comparables.
   - Documento → generar reporte ejecutivo.
   - Alerta → si confianza = BAJA, solicitar validación humana.
   - Marketing → guardar pricing, posicionamiento y promoción sugeridos.

## Dos pruebas para la entrega
Prueba 1:
- categoría: Skincare
- ml: 75

Prueba 2:
- categoría: Haircare
- ml: 250

Registrar para cada prueba:
1. Entrada.
2. Comparables seleccionados.
3. Predicción base.
4. Prompt.
5. Respuesta JSON.
6. Dashboard.
7. Recomendación final.

## Importante
La predicción numérica debe poder reproducirse sin la IA. La IA se usa para interpretar, justificar y convertir el resultado en una recomendación de marketing. Esto mejora trazabilidad y reduce el riesgo de alucinación.
