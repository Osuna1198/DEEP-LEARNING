DEEP-LEARNING
Este trabajo busca crear un modelo híbrido de Deep Learning que pueda predecir el nivel de interés o interacción que generan los puntos turísticos, combinando tanto la información visual de las imágenes como los datos adicionales que tenemos sobre ellos. Con este enfoque, podemos mejorar las estrategias de contenido y obtener datos útiles para tomar mejores decisiones.

1.	Exploración de Datos
•	Registros totales: 1,569
•	Variables: 14 características principales
•	Valores nulos: No se identificaron datos nulos

2.	Cómo definimos el nivel de engagement
Calculamos el nivel de interacción con esta fórmula:
engagement_score = likes - dislikes + bookmarks
Esta forma de calcularlo nos pareció la mejor para reflejar el interés real que tienen los usuarios hacia los puntos turísticos.
-	Distribución de los resultados
•	La mayoría de los valores están cerca de cero, aunque hay algunos datos fuera de lo común.
-	División de los datos
•	70% para entrenar el modelo
•	15% para validar los resultados
•	15% para probar la precisión final
________________________________________
3.	Estructura del Modelo
El modelo combina una Red ResNet50, que ya viene entrenada para analizar imágenes, con una red neuronal que procesa los datos adicionales.
-	ResNet50
o	Se usa para extraer características importantes de las imágenes, aprovechando su entrenamiento previo con ImageNet.
-	Red neuronal para datos adicionales
o	Incluye técnicas para evitar que el modelo se adapte demasiado a los datos de entrenamiento (Dropout).
o	Los tags se convierten en números a través de una técnica llamada embeddings.
-	Regularización
o	Se aplican métodos como Dropout, detener el entrenamiento temprano (Early Stopping) y reducir la velocidad de aprendizaje para evitar estancamientos.
-	Entrenamiento
o	Se usa una función que mide el error llamada CrossEntropyLoss.
o	El optimizador es Adam con un ajuste para evitar sobreajustes (weight decay).
o	Se entrenó durante 50 ciclos o epochs.
________________________________________
4.	Resultados del Entrenamiento
•	La pérdida o error disminuyó rápido al principio y luego se mantuvo estable.
•	El balance entre el error en entrenamiento y validación fue bueno.
•	En varias ocasiones, el modelo fue mejor en datos nuevos que en los usados para entrenar, lo que indica que generaliza bien.
________________________________________
5.	Evaluación del Modelo
Al analizar cómo se comportó el modelo con los datos de prueba:
•	Falsos negativos: 15 casos
•	Precisión total: 92%
Lo que esto significa:
•	El modelo predice con bastante exactitud el nivel de interés para la mayoría de los puntos turísticos.
•	El balance entre precisión y capacidad para detectar correctamente casos positivos fue bueno.
•	El desempeño en la categoría con menos datos (High Engagement) todavía puede mejorar.
________________________________________
6.	Conclusión
El modelo alcanza una precisión global del 92%, mostrando buen desempeño para predecir el engagement de los puntos turísticos. Aunque se puede mejorar especialmente en la categoría menos frecuente, en general el modelo funciona bien manteniendo un equilibrio sólido entre precisión y detección.


