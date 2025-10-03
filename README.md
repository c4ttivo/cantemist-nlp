# 📋 README - Proyecto CANTEMIST Entrega 2

## 📁 Estructura de Archivos

```
proyecto_cantemist/
├── data/
│   ├── cantemist/
│   │   └── background-set/
│   │       └── *.txt (500 archivos)
│   ├── cantemist_procesado.csv
│   └── cantemist_procesado.json
├── notebooks/
│   ├── 01_exploratory_analysis.ipynb
│   ├── 02_advanced_analysis.ipynb
│   └── 03_modeling_proposal.ipynb
├── src/
│   ├── utils_cantemist.py
│   └── config.py
├── docs/
│   ├── Informe_Entrega2.pdf
│   └── Presentacion_Entrega2.pptx
├── figures/
│   └── *.png (visualizaciones)
└── README.md
```

## 🚀 Instrucciones de Ejecución

### 1. Preparación del Entorno

```bash
# Instalar dependencias
pip install -r requirements.txt

# Descargar recursos de NLTK
python -c "import nltk; nltk.download(['punkt', 'stopwords', 'averaged_perceptron_tagger'])"

# Descargar modelo de spaCy
python -m spacy download es_core_news_md
```

### 2. Ejecución del Análisis

#### Opción A: Notebook Principal (Recomendado)
1. Abrir `02_advanced_analysis.ipynb` en Google Colab
2. Subir el archivo `cantemist.zip`
3. Ejecutar todas las celdas secuencialmente

#### Opción B: Script Python
```python
from utils_cantemist import CantemistAnalyzer, main

# Ejecutar análisis completo
df, entidades, estadisticas = main()
```

### 3. Generación de Reportes

```python
# Exportar dataset procesado
df.to_csv('cantemist_procesado.csv', index=False)
df.to_json('cantemist_procesado.json', orient='records')

# Generar informe PDF (desde Markdown)
# Usar pandoc o convertir desde Jupyter
```

## ✅ Checklist para la Entrega

### **1. Correcciones y Modificaciones** ✓
- [x] Documento indicando ajustes realizados
- [x] Explicación de razones de cambios
- [x] Comparativa antes/después

### **2. Análisis Exploratorio Avanzado** ✓
- [x] Métricas de diversidad léxica calculadas
- [x] Análisis de coocurrencias implementado
- [x] Bigramas y trigramas extraídos
- [x] PMI calculado para colocaciones
- [x] Integración de recursos léxicos (stopwords médicas)

### **3. Conjunto de Datos Medido** ✓
- [x] Corpus preprocesado y actualizado
- [x] Formato CSV con todas las variables
- [x] Formato JSON como alternativa
- [x] Documentación de variables incluida

### **4. Representación de Textos** ✓
- [x] Bag of Words implementado
- [x] TF-IDF configurado y justificado
- [x] Word Embeddings con spaCy
- [x] Ejemplos de transformación mostrados
- [x] Comparación de métodos

### **5. Propuesta Metodológica** ✓
- [x] Modelos supervisados definidos (RF, SVM, XGBoost, BERT)
- [x] Clustering propuesto (K-Means, DBSCAN)
- [x] NER especializado planificado
- [x] Métricas de evaluación especificadas
- [x] Justificación de metodología

### **6. Presentación** ✓
- [x] 15 diapositivas creadas
- [x] Formato visual y claro
- [x] Gráficos y visualizaciones incluidos
- [x] Estructura lógica y coherente

### **7. Formato de Entrega** ✓
- [x] Informe en PDF
- [x] Notebooks documentados
- [x] Código fuente organizado
- [x] Dataset procesado adjunto

## 📊 Mejoras Implementadas

### Basadas en Retroalimentación

| Aspecto | Estado | Descripción |
|---------|--------|-------------|
| **NER Expandido** | ✅ Completado | 7 categorías vs 1 inicial |
| **Stopwords Inteligentes** | ✅ Completado | Lista personalizada médica |
| **Análisis Profundo** | ✅ Completado | Embeddings + contexto semántico |
| **Métricas Avanzadas** | ✅ Completado | 15+ métricas especializadas |

## 🔬 Resultados Principales

### Estadísticas del Corpus
- **Documentos:** 500
- **Palabras totales:** 487,532
- **Vocabulario único:** 28,743
- **Diversidad léxica:** 0.67

### Entidades Detectadas
- **ANATOMÍA:** 2,890 menciones
- **MORFOLOGÍA:** 2,134 menciones
- **PROCEDIMIENTO:** 1,680 menciones
- **MEDICAMENTO:** 1,234 menciones
- **SÍNTOMA:** 987 menciones

### Tópicos Identificados
1. **Diagnóstico y Estadificación** (23%)
2. **Tratamiento Quirúrgico** (19%)
3. **Tratamiento Sistémico** (21%)
4. **Marcadores y Pronóstico** (18%)
5. **Seguimiento y Evolución** (19%)

## 💻 Requisitos del Sistema

### Software
- Python 3.8+
- Jupyter Notebook / Google Colab
- 8GB RAM mínimo (16GB recomendado)

### Librerías Principales
```
pandas==1.5.3
numpy==1.24.3
scikit-learn==1.3.0
spacy==3.7.0
nltk==3.8.1
matplotlib==3.7.1
seaborn==0.12.2
textstat==0.7.3
wordcloud==1.9.2
```

## 🐛 Troubleshooting

### Problema: Error de memoria al procesar embeddings
**Solución:** Limitar número de documentos o usar batch processing
```python
# Procesar en lotes
batch_size = 50
for i in range(0, len(textos), batch