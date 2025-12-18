# Sistema Automatizado de Análisisc on IA
Sistema automatizado de análisis financiero que combina Python, Yahoo Finance y un modelo LLM para generar KPIs, análisis de volatilidad y un resumen ejecutivo avanzado. Incluye descarga de datos, benchmark, detección de días extremos y creación de prompts dinámicos.

**Descripción General**

Este proyecto implementa un sistema automatizado de análisis financiero que genera:
- KPIs completos de desempeño de un activo bursátil
- Comparación contra cualquier benchmark
- Análisis avanzado de volatilidad
- Un Resumen Ejecutivo con intención de que sea profesional generado mediante IA (LLM)

El sistema recibe parámetros simples (ticker, fechas, benchmark) y ejecuta automáticamente:
- Descarga de datos históricos (Yahoo Finance)
- Cálculo de métricas cuantitativas
- Detección de días extremos con mayor volatilidad
- Construcción de un prompt estructurado
- Generación del análisis final mediante un modelo LLM (Cohere)
- Exportación de outputs: CSV, prompt, y resumen ejecutivo

_El caso forma parte de los casos prácticos del MDA de ISDI_

**Objetivo del Proyecto**

Reducir el trabajo manual que realizan los analistas financieros generando informes semanales, automatizando:
- Descarga y procesamiento de datos
- Cálculo de KPIs y métricas de riesgo
- Benchmarking
- Redacción del análisis técnico
- Estructuración de archivos de salida
El sistema funciona con cualquier activo y cualquier benchmark, gracias a un diseño totalmente parametrizable.

**Parámetros de Entrada**

Ejemplo:
_params = {
   'ticker': 'AAPL',
   'ticker_name': 'Apple Inc.',
   'start_date': '2025-01-01',
   'end_date': '2025-06-30',
   'benchmark': '^GSPC',
   'benchmark_name': 'S&P 500',
   'analyst_role': 'Analista financiero senior de Quantum Capital Partners',
   'audience': 'Comité de Inversiones',
   'tone': 'técnico, directo y centrado en la volatilidad'_
}

**Módulos del Sistema**

1. Descarga de datos (Yahoo Finance)
Se descargan datos OHLCV para el ticker y el benchmark, normalizando índices y formatos.

2. Cálculo de Métricas

✔️ KPIs básicos: precio inicial, final, máximo, mínimo, cambio absoluto y porcentual, volumen medio y total

✔️ Análisis día a día: retornos diarios, días positivos/negativos, mejores y peores días

✔️ Comparación de rendimiento con benchmark

3. Identificación de días extremos
Se generan dos dataframes:
- Top 3 días positivos
- Top 3 días negativos
Ambos se inyectan dentro del prompt para enriquecer la interpretación del modelo IA.

4. Construcción del Prompt Avanzado
Incluye:
- Rol del analista
- Audiencia
- Tono
- KPIs calculados
- Tablas inyectadas
- Instrucciones de redacción detalladas
Archivo asociado: prompt_usado.txt

5. Generación del Análisis con IA (Cohere)
Se utiliza el modelo _command-a-03-2025_ para obtener:
- Un Resumen Ejecutivo financiero completo
- Análisis de volatilidad
- Comparación de riesgo vs benchmark
- Recomendación táctica final

**Cómo ejecutar el proyecto**

1. Instalar dependencias:
_pip install yfinance cohere pandas_

2. Añadir tu API Key de Cohere:
_API_KEY = "tu_api_key"_

3. Ejecutar el notebook desde inicio a fin.

4. Encontrar los resultados en:
_/output/YYYYMMDD_analisis_[TICKER]_
