# Conclusiones 
Se realizara una comparacion final y una reflexion critica acerca de los resultados y ambos metodos 

## Tabla de comparacion 

Se crea la tabla de comparacion entre los mejores modelos, en pyspark y sklearn siendo el gridsearch elegido

| Aspecto                     | scikit-learn                          | PySpark ML                          | Comentarios |
|----------------------------|----------------------------------------|-------------------------------------|-------------|
| Modelo                     | MLP  | MLP| Modelos equivalentes usados |
| Dataset                    | Avazu (subset)             | Avazu (completo)                    | el subset fue de 1 millon de datos |
| Número de muestras         | 1M                                    | 40M                                 | PySpark escala mejor |
| Número de features         | 13                                    | 23                                  | se utilizo una muestra de variables relevantes en sklearn |
| ROC-AUC                    | 0.656                                 | 0.673                               | Diferencias marginales |
| Precision                  | 0.24                                  | 0.27                                | Threshold optimizado en mejores modelos |
| Recall                     | 0.70                                  | 0.62                                | Las metricas evaluadas en mejores modelos |
| F1-score                   | 0.36                                  | 0.37                                | Métrica objetivo en mejores modelos |
| Threshold usado            | 0.15                                  | 0.54                                | Maximiza F1 |
| Tiempo de entrenamiento    | 119 min                                | 208.4 min                               | En sklearn el gridsearch completo y en pyspark el grid  |
| Tiempo de validacion       | 0.01 s                                  | 0.1 s                                | En mejores modelos |
| Facilidad de implementación| Alta                                  | Baja                            | PySpark necesito de mas instalaciones para funcionar, las cuales pueden ser delicadas  |


En general pyspark logro resultados mas rapidos en cuanto a metricas las cuales son ligeramente mayores en comparacion a sklearn a pesar de haber sido optimizado mediante el uso de haber usado una muestra representativa de la poblacion y un conjunto de variables reducido. Demostrando como pyspark es mas eficiente para datasets mas grandes, sin embargo sklearn es mas rapido y subceptible a experimentacion comparado con pyspark que debe ser tratado con mas cuidado.

## Reflexión final

Considerando los resultados finales, se pueden extraer conclusiones más matizadas sobre el uso de scikit-learn y PySpark ML en el entrenamiento de modelos MLP sobre el dataset Avazu.

### ¿Qué entorno fue más rápido?

Al considerar el **tiempo total del grid search completo**, **scikit-learn resultó ser más rápido** que PySpark ML. El grid completo en scikit-learn tomó aproximadamente **119 minutos** utilizando un subset de 1 millón de registros, mientras que el grid search en PySpark, entrenado sobre el dataset completo de 40 millones de muestras, requirió alrededor de **208 minutos**.

Esto evidencia que, aunque PySpark ofrece paralelización, el **overhead propio del entorno distribuido**, junto con la mayor complejidad del pipeline y el tamaño del dataset, puede resultar en tiempos de entrenamiento más altos cuando se consideran búsquedas exhaustivas de hiperparámetros.

### ¿Cuál fue más preciso?

En términos de desempeño predictivo, **PySpark obtuvo métricas ligeramente superiores**, con un ROC-AUC de 0.673 y un F1-score de 0.37, frente a 0.656 y 0.36 en scikit-learn. No obstante, estas diferencias son **marginales** y deben interpretarse a la luz de las condiciones experimentales:
- PySpark fue entrenado sobre el **dataset completo** y con un mayor número de features.
- scikit-learn utilizó un **subset reducido** y una selección más acotada de variables.

Por tanto, ambos enfoques logran resultados comparables en términos de calidad del modelo.

### ¿Cuándo es útil PySpark?

PySpark demuestra su utilidad principalmente cuando:
- El volumen de datos excede la capacidad de procesamiento local,
- Se requiere entrenar modelos sobre el **dataset completo sin muestreo**,
- El objetivo es escalar el flujo de trabajo a entornos productivos distribuidos.

Sin embargo, estos beneficios vienen acompañados de:
- **Mayores tiempos de entrenamiento** al ejecutar grid searches completos,
- **Mayor complejidad de instalación y configuración**,
- Una curva de aprendizaje más pronunciada frente a scikit-learn.

### Conclusión general

Los resultados muestran que la elección entre scikit-learn y PySpark ML depende del **contexto del problema** más que de una superioridad absoluta:

- **scikit-learn** es más eficiente para experimentación rápida, prototipado y búsquedas de hiperparámetros sobre datasets de tamaño moderado.
- **PySpark ML** es una alternativa robusta cuando se prioriza la escalabilidad y el uso del dataset completo, incluso a costa de mayor tiempo computacional y complejidad operativa.

En consecuencia, una estrategia híbrida —prototipar en scikit-learn y escalar en PySpark— puede ser la opción más efectiva en escenarios reales.


