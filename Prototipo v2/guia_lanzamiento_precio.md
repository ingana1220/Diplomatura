# GUÍA DE IMPLEMENTACIÓN Y PRUEBA

## 1. Prototipo local
Abrir `lanzamiento_precio.html` en Chrome o Edge.
El selector de categoría se construye automáticamente a partir del campo `categoria` del JSON de datos.

Para la demo actual aparecen:
- Haircare
- Limpieza
- Skincare
- Solar

IMPORTANTE: estas son las categorías del dataset DEMO incluido en este paquete, no una afirmación sobre el dataset académico original. Al reemplazar `datos_demo.json` por el dataset real, el selector debe reflejar las categorías reales.

## 2. Ejecutar una predicción
1. Seleccionar categoría.
2. Ingresar ml.
3. Pulsar “Estimar precio”.
4. Revisar precio sugerido y rango.
5. Revisar comparables.
6. Copiar el prompt generado a la herramienta de IA.
7. Pegar la respuesta JSON en el registro de pruebas.

## 3. Cómo funciona el modelo
Se usa un modelo de vecinos por tamaño de envase:
- misma categoría;
- productos con precio y ml válidos;
- cercanía logarítmica del tamaño;
- hasta cinco comparables;
- precio equivalente para el nuevo tamaño;
- mediana como estimación;
- ±10% como rango orientativo.

Esto es un baseline explicable. No debe presentarse como un modelo econométrico ni como una garantía de precio.

## 4. IA Generativa
La IA recibe la predicción base y los comparables. No calcula el precio desde cero. Su función es:
- explicar;
- identificar evidencia;
- señalar limitaciones;
- proponer validaciones;
- generar decisión de marketing.

## 5. Evidencia para Consigna 2
La consigna pide un prototipo interactivo y, para Opción A, el prompt exacto y al menos dos ejemplos; para Opción B, trigger y acciones; y para Opción C, explicar el uso de visión por computadora. La propuesta combina las tres capas sin confundir sus roles.

Guardar capturas de las dos pruebas:
A) Skincare + 75 ml.
B) Haircare + 250 ml.

## 6. Métrica sugerida
Métrica única: error porcentual absoluto medio (MAPE) entre la predicción y el precio real de lanzamientos comparables, medido retrospectivamente sobre un conjunto de validación.

## 7. Limitaciones
- dataset pequeño en la demo;
- precios nominales y sensibles al momento de captura;
- no incorpora automáticamente inflación, canal, promociones ni elasticidad;
- Computer Vision depende de la calidad de las fotografías;
- la IA no debe reemplazar la validación humana.
