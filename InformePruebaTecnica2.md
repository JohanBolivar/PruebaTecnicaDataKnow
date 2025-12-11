# **Prueba técnica 2: Caso de Negocio: Asesor legal para consulta historia de demandas** 
## **Explicación del Caso**
El consultorio jurídico desea automatizar la consulta de historiales de demandas para mejorar la rapidez y claridad de las asesorías a clientes. Actualmente, los abogados revisan manualmente un archivo Excel con múltiples casos y sentencias.
El objetivo de esta prueba era evaluar si una IA podía:
- Buscar casos similares a una consulta legal.
- Extraer campos relevantes de cada sentencia.
- Explicar cada caso en lenguaje coloquial, sin tecnicismos, para facilitar su comprensión por parte de clientes.
La prueba se enfocó en tres temas principales:
- Demandas relacionadas con redes sociales
- Casos de acoso escolar
- Casos relacionados con PIAR

## **Supuestos**
- Para la solución se asumió lo siguiente:
- Los datos originales provienen de un archivo Excel.
- Los campos relevantes por caso son:
  - Providencia, Tipo, FechaSentencia, Tema, Resumen/Síntesis.
- El sistema usa:
  - SentenceTransformers (all-MiniLM-L6-v2) para generar embeddings.
  - ChromaDB como base de datos vectorial.
- Las explicaciones coloquiales se generan usando un modelo de IA (Mistral 7B).
- Las respuestas debían ser:
  - Cortas
  - Claras
  - Sin vocabulario jurídico complejo

## **Formas para Resolver el Caso y Opción Tomada**
### **Formas posibles: Revisión manual**
Buscar en el Excel caso por caso y redactar explicaciones claras.
- Poco eficiente, lento y no escalable.

### **Opción tomada: Automatización con IA**
Se implementó un flujo completo:
1. Carga y limpieza de datos desde Excel.
2. Construcción de un texto unificado para cada caso.
3. Generación de embeddings con SentenceTransformers.
4. Indexación en ChromaDB para permitir búsquedas semánticas.
5. Función buscar_casos() para recuperar los casos más similares.
6. Función a_lenguaje_coloquial() para explicar cada caso en lenguaje sencillo.

## **Resultados del análisis de los datos y los modelos**
A continuación se presentan los resultados exactos generados por el sistema, según cada categoría solicitada.

### **Tres demandas sobre redes sociales**
1. Caso 1 (Lenguaje coloquial)
(Extracto del resultado generado)
Periodistas denunciaron ataques misóginos en Twitter. Alegaron que la Dirección Nacional Electoral no actuó para detener la violencia ni sancionar responsables. También cuestionaron que partidos políticos alentaran o toleraran las agresiones. Se analiza violencia en línea, libertad de expresión y sanciones a actores políticos.

2. Caso 2 (Lenguaje coloquial)
Una mujer pidió protección por ataques en redes sociales, pero la Corte negó la acción por no cumplir requisitos. Determinó que ella no había intentado previamente otras alternativas para resolver el problema. Además, las plataformas no son responsables del contenido publicado por usuarios.

3. Caso 3 (Lenguaje coloquial)
Un ciudadano presentó una tutela porque alguien publicó su foto en Facebook con un texto falso e incitador de odio. La Corte declaró la tutela improcedente porque había otros mecanismos para resolver la situación antes de acudir al juez.

### **Caso de acoso escolar**
Un estudiante compartió imágenes íntimas de una menor. La escuela lo suspendió indefinidamente. Aunque el estudiante dijo que no tenía mala intención, la institución argumentó que la conducta era acoso escolar. La Corte analizó el debido proceso disciplinario en colegios.

### **Casos relacionados con PIAR**
1. Caso 1 (Lenguaje coloquial)
Una madre demandó a la escuela porque no atendieron adecuadamente el acoso sufrido por su hija, quien desarrolló depresión y ansiedad. La institución tampoco aplicó un PIAR adecuado, afectando su rendimiento y promoviendo la violación de sus derechos.

2. Caso 2 (Lenguaje coloquial)
Un recurso fue rechazado porque el demandante no corrigió los errores iniciales. La Corte concluyó que no aportó argumentos suficientes para subsanar las deficiencias legales señaladas en la inadmisión.

3. Caso 3:
Caso 3 (Lenguaje coloquial)
Se presentó un conflicto entre dos juzgados sobre cuál debía conocer una demanda relacionada con pagos de servicios médicos no incluidos en el plan de beneficios. Ambos juzgados reclamaron competencia, generando la controversia.

### **Observaciones sobre el modelo**
- La IA permite consultas rápidas en lenguaje sencillo.
- La combinación de embeddings y búsqueda semántica asegura que se recuperen los casos más relevantes para cada consulta.
- La metodología es escalable para agregar más tipos de demandas y mejorar la cobertura del consultorio.


## **Futuros Ajustes o Mejoras**
- Conectar el sistema a un chat interactivo para consultas en tiempo real.
- Optimizar el modelo generativo con fine-tuning para lenguaje legal simple.
- Mejorar el manejo de textos extensos para evitar recortes.
- Expandir la base de datos con más casos y categorías.
- Crear métricas de evaluación de:
  - Precisión de búsqueda
  - Relevancia de resultados
  - Calidad del lenguaje coloquial
