# Postulacion-Xepelin

En este repositorio se encuentra la solución a la prueba de postulación a Xepelin de Benjamín Fuentes.

Para el desarrollo de la prueba se utilizaron dos cuadernillos Jupyter con lenguaje Python (estos fueron ejecutados utilizando Google Colab). Ambos cuadernillos tienen breves descripciones con los pasos y tareas que se realizaron.

El primer cuadernillo contiene una exploración de la base de datos, en donde se analizan diversos aspectos de la base de datos mediante tablas y gráficos. El segundo cuadernillo contiene el desarrollo de los modelos propuesto para realizar la predicción pedida. En este se evaluan dos enfoques para llegar al resultado:

- El primer enfoque considera cada factura como un dato y se utiliza la columna 'amountfinancedByXepelin' como la variable objetivo. Los modelos definidos buscan predecir el valor de esta variable dado el Id de un pagador, el Id de un recibidor y el monto de la factura. Se utilizaron dos algoritmos de machine learning que son estado del arte cuando se utilizan datos estructurados. Estos fueron un Random Forest y un XGBoost.
- El segundo enfoque se consideraró un modelo de series de tiempo, para el cual se agruparon las facturas de acuerdo al mes en el cual fueron pagadas, obteniendo el monto total mensual. Se utilizó un modelo ARIMA, el cual predecía que proporción del total de las facturas mensuales serían financiadas por Xepelin. Se decidió utilizar esta variable para el modelo, ya que se comprobó que era estacionaria en el tiempo.

Para ambos casos se considerarón los siguientes supuestos.
- Las facturas con estado 'PROCESSING', fueron consideradas como las facturas de octubre. Si bien estas incluian cuales serían financiadas por Xepelin, estos valores se utilizarón solo para contrastar los resultados obtenidos.
- Dado que el objetivo es predecir cuanto dinero mueve Xepelin en un mes, es decir, cuanto dinero van a prestar, las facturas con el estado pagadas o fallidas fueron consideradas de la misma forma, dado que en ambos caso sale una cierta cantidad de dinero.

### Conclusiones y observaciones

A continuación se realizan algunos comentarios y conclusiones de los resultados obtenidos por ambos enfoques mencionados.

- Se pudo apreciar por medio de los resultados que Xepelin al implementar estos modelos puede obtener una predicción razonable de cuanto dinero se moverá en un mes, lo cual era el principal objetivo de este estudio. Esta información es útil una vez que el nuevo producto se implementado, ya que permite a Xepelin saber cuanto es el flujo estimado de dinero mensualmente.
- La base de datos actual es bastante acotada, lo cual genera ciertas limitaciones en ambos enfoques discutidos. Para el primer caso, no existe mucha descripcción de las facturas en la base de datos, lo que se traduce en pocas variables para el entrenamiento de los modelos de Machine Learning. Para el segundo caso, el historial de datos es corto (8 meses), lo que genera dificultades a la hora de hacer análisis con series de tiempo.
- En cuanto a como mejorar los modelos, consideramos nuevamente los dos enfoques por separado. Para el primer caso, se puede seguir entrenando el modelo ajustando parametros para obtener resultados un poco mejores. Más importante aún, se deberían buscar posibles atributos para agregar a la base de datos. Estos podrían ser caracteristicas del pagador, como sector de la empresa, años de la empresa entre otras cosas. También se puede evaluar agregar variables macroeconómicas como por ejemplo el IMACEC o el valor de las tasas de interés. Esta información es pública y podría dar ciertas nociones de como está el mercado y cuanto dinero se moverá en un mes a nivel país. En cuanto al segundo caso, la mejor forma de mejorar el desempeño del modelo es obtener un mayor historial. Dado que el producto es nuevo, a medida que pase el tiempo la base de datos será más abundante y las predicciones serán más precisas. 
