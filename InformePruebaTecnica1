# **Prueba técnica 1: ** 
## **Explicación del Caso**
La empresa constructora se encuentra en la fase de planificación de un proyecto con duración de 36 meses y necesita estimar los costos de dos equipos esenciales para la ejecución del proyecto. Los costos de los equipos son variables según los proveedores, pero se pueden aproximar en función del costo de sus materias primas:
- Equipo 1: 20% materia prima X y 80% materia prima Y.
- Equipo 2: partes iguales de las materias primas X, Y y Z.
El objetivo principal es obtener estimaciones precisas de los costos para permitir una mejor planificación financiera y seleccionar proveedores con la mejor relación costo-beneficio.

## **Supuestos**
1. Para la estimación se realizaron los siguientes supuestos:
2. Los precios de las materias primas X, Y y Z se toman de archivos CSV proporcionados.
3. Los datos pueden contener caracteres no numéricos, comas como separadores decimales y espacios, por lo que se requiere limpieza previa.
4. No se consideran variaciones de costos por transporte, impuestos o descuentos por volumen; solo se usan los precios base de las materias primas.
5. Cada fila de los CSV representa un registro temporal del precio de la materia prima.

## **Formas para Resolver el Caso y Opción Tomada**
### **Formas posibles**
- Método Manual: calcular los costos usando hojas de cálculo, combinando los porcentajes de las materias primas.
- Automatización con Python/Pandas: procesar los archivos CSV, limpiar los datos, calcular los costos y generar un DataFrame con resultados finales.

### **Opción tomada**
Se optó por la automatización con Python, usando Pandas, lo que permitió:
- Lectura de archivos CSV (X.csv, Y.csv, Z.csv).
- Limpieza de la columna de precios para convertirlos a valores numéricos válidos.
- Cálculo de los costos de los equipos mediante fórmulas ponderadas:

```
# Equipo 1: 20% X + 80% Y
df_equipo1 = 0.20 * dfx['Price'] + 0.80 * dfy['Price']

# Equipo 2: promedio de X, Y, Z
df_equipo2 = (dfx['Price'] + dfy['Price'] + dfz['Price']) / 3
```
- Generación de un DataFrame final con precios originales y costos estimados de cada equipo.

## **Resultados del análisis de los datos y los modelos **
![Visualización de la tabla](image.png)

### **Observaciones**
- El Equipo 1 se ve más influenciado por la materia prima Y, dado que representa el 80% del costo.
- El Equipo 2 refleja un costo promedio equitativo de las tres materias primas.
- La limpieza de datos fue fundamental para evitar errores en los cálculos debido a formatos inconsistentes en los CSV.

## **Futuros Ajustes o Mejoras**
- Incluir variaciones temporales de precios para estimar costos futuros con mayor precisión.
- Considerar costos adicionales, como transporte, impuestos o descuentos por volumen.
- Integrar un método de optimización de proveedores para seleccionar los más convenientes según precio y calidad.
- Automatizar la lectura de múltiples proyectos y consolidar los resultados en un solo reporte.

## **Apreciaciones y Comentarios del Caso**
- La automatización permite ahorrar tiempo y reducir errores en comparación con cálculos manuales.
- La metodología es escalable y puede adaptarse a más equipos o más materias primas.
