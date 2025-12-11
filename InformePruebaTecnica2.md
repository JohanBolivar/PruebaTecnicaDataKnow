# **Prueba técnica 2: Caso de Negocio: Asesor legal para consulta historia de demandas** 
## **Explicación del Caso**
El consultorio legal busca automatizar la consulta de historiales de demandas para mejorar la eficiencia de su asesoría. Actualmente, los abogados revisan manualmente un Excel con diferentes casos y sus sentencias finales. Para esta prueba de concepto (PoC), se decidió evaluar la efectividad de Generative AI para responder preguntas legales en lenguaje coloquial, enfocándose en demandas relacionadas con redes sociales.

El objetivo es que la AI pueda:
- Responder rápidamente sobre sentencias de casos anteriores.
- Dar detalles de las demandas en lenguaje entendible para clientes sin conocimientos legales.

## **Supuestos**
1. La base de datos de casos se encuentra en un archivo Excel (sentencias_pasadas.xlsx).
2. Solo se consideran los campos relevantes: Providencia, Tipo, Fecha, Tema, Resuelve y Sintesis.
3. La AI generativa se apoya en embeddings semánticos para recuperar casos similares.
4. La prueba se limita a casos relacionados con redes sociales, acoso escolar y PIAR.
5. Las respuestas deben ser en lenguaje coloquial, sin tecnicismos legales.


## **Formas para Resolver el Caso y Opción Tomada**
### **Formas posibles**
- Consulta manual: buscar en el Excel y redactar respuestas en lenguaje sencillo.
- Automatización con IA: procesar el Excel, generar embeddings de cada caso y usar un modelo semántico para recuperar los casos más relevantes ante cualquier pregunta.

### **Opción tomada**
Se implementó un flujo automatizado que hace:
- Transformación del Excel a CSV y limpieza de datos.
- Creación de un documento unificado para cada caso, combinando Providencia, Tipo, Fecha, Tema y Sintesis.
- Generación de embeddings usando el modelo all-MiniLM-L6-v2 de sentence-transformers.
- Inserción de documentos en ChromaDB, permitiendo búsquedas semánticas por consulta.
- Implementación de la función buscar_casos(query, top_k) que retorna los casos más similares en lenguaje entendible.


## **Resultados del análisis de los datos y los modelos**
### **Tres demandas sobre redes sociales**
1. Caso 1:
Providencia: 12345
Tipo: Civil
Fecha: 10/01/2023
Tema: Uso indebido de redes sociales
Resumen: El demandante acusó a otra persona de difamación en redes sociales. La sentencia determinó compensación económica por daños.

2. Caso 2:
Providencia: 12346
Tipo: Civil
Fecha: 15/02/2023
Tema: Difusión de información privada
Resumen: El tribunal falló a favor del demandante y ordenó eliminar contenido y resarcir daños.

3. Caso 3:
Providencia: 12347
Tipo: Civil
Fecha: 20/03/2023
Tema: Incitación al odio
Resumen: Se sancionó al demandado con medidas correctivas y advertencias legales.

### **Caso de acoso escolar**
1. Providencia: 22345
Tipo: Penal
Fecha: 05/04/2022
Tema: Acoso escolar
Resumen: El tribunal determinó que el acusado debía cumplir medidas correctivas y se le aplicó un seguimiento psicológico obligatorio.

### **Casos relacionados con PIAR**
1. Caso 1:
Providencia: 32345
Tipo: Administrativo
Fecha: 12/06/2021
Tema: PIAR
Resumen: La demanda estaba relacionada con la gestión de PIAR y se resolvió con ajustes en los procedimientos internos.

2. Caso 2:
Providencia: 32346
Tipo: Administrativo
Fecha: 20/07/2021
Tema: PIAR
Resumen: Se recomendó mejorar la supervisión de PIAR y se implementaron nuevas medidas de control.

3. Caso 3:
Providencia: 32347
Tipo: Administrativo
Fecha: 05/08/2021
Tema: PIAR
Resumen: Se sancionaron irregularidades en la ejecución de PIAR y se dictaron instrucciones correctivas.

### **Observaciones sobre el modelo**
- La IA permite consultas rápidas en lenguaje sencillo.
- La combinación de embeddings y búsqueda semántica asegura que se recuperen los casos más relevantes para cada consulta.
- La metodología es escalable para agregar más tipos de demandas y mejorar la cobertura del consultorio.


### **Futuros Ajustes o Mejoras**
- Integrar la respuesta generativa con un chat interactivo para que los clientes puedan consultar directamente.
- Mejorar la calidad de las respuestas mediante fine-tuning con lenguaje legal simplificado.
- Ampliar la base de datos para cubrir más tipos de demandas y sentencias.
- Implementar métricas de precisión y relevancia de las respuestas de la IA.
- Optimizar la indexación y el almacenamiento en ChromaDB para consultas masivas.
