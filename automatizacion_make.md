# Automatización Make — esquema para construir

```text
[Google Sheets: Watch Rows]
             |
             v
[Google Sheets: Get range / consolidar datos]
             |
             v
[Tools: preparar JSON]
             |
             v
[Make AI Toolkit / AI Agent]
             |
             v
[JSON Parse]
       /       |        \
      /        |         \
     v         v          v
[Dashboard] [Documento] [Alertas]
     \         |          /
      \        |         /
       v       v        v
        [Decisiones Marketing]
```

## Trigger
Google Sheets → Watch Rows.

## Prompt
Copiar el contenido completo de `prompt_ia_generativa.txt`.

## Variable principal
Enviar al módulo IA un JSON con los registros consolidados.

## Router
- Ruta 1: siempre → actualizar hoja `dashboard`.
- Ruta 2: siempre → generar documento ejecutivo.
- Ruta 3: filtro `prioridad = ALTA` → alerta.
- Ruta 4: siempre → guardar decisiones de marketing.

## Prueba
Primero ejecutar manualmente con pocos registros. Confirmar que la respuesta sea JSON válido antes de conectar las salidas.

## Automatización periódica
En el plan Free, Make informa un intervalo mínimo de 15 minutos entre ejecuciones programadas. Para la demo académica conviene usar ejecución manual y luego mostrar la lógica programada.
