# Garbage-classification
- Día 1
  
# MOTIVOS PARA ELEGIR EL PROYECTO:
- ¿Qué relevancia tiene este tema para ustedes?  ``` Queríamos crear una herramienta útil para nuestro día a día, que nos permitiera identificar los materiales que componen los productos. Nuestro proyecto tiene varias fases: 1º Crear el modelo que pueda clasificar correctamente los materiales. 2º Implementar el modelo en una app, que permita al usuario sacar una foto y que el modelo clasifique automáticamente el material.```
- ¿Cómo puede generar utilidad en un caso real? ```Nuestro principal objetivo es identificar los objetos para reciclar en cada contenedor.```
- 
# REFLEXIÓN SOBRE EL DATASET:
- ¿El dataset es balanceado? ```No, falta equilibrar el número de imágenes de todos los tipos de clasificación```
- ¿Deberemos hacer mucha limpieza?```No, ya que solo tenemos que reestructurar el tamaño de las imágenes y el número de ellas.```
- ¿Es algun problema el formato de alguna variable?```El tamaño.```
- ¿Tiene suficientes registros para entrenar al modelo?```Si, he incluso pondremos más ya que tenemos que equilibrar las categorías.```

# MODELO:
- ¿Qué tipo de problema estás resolviendo? ```Clasificación de imágenes.```
- ¿El modelo está entrenado para un dominio similar? ```Si, clasifica muchas cosas pero no se especializa en ninguna.```
- ¿Qué modelo han elegido y por qué? ```EfficientBO que está especializado en clasificar objetos y lo reentrenaremos para nuestro caso.```
- ¿Qué dataset han seleccionado y cuál es la razón detrás de esta elección? ```Hemos elegido este dataset, ya que contiene diferentes categorias de materiales para saber como dividirlas a la hora del reciclaje, este dataset presenta imágenes con sus respectivas etiquetas lo que facilita el entrenamiento.```

- Día 2

# ETAPAS:
- Configuración del entorno
- Pruebas Iniciales con el modelo ```Realizamos una prueba inicial con el modelo sin entrenar, pero los resultados no eran buenos```
- Análisis y congelación de capas ```Nuestro modelo tenía 238 capas, creamos una nueva (output), ya que nuestro objetivo era que el modelo a la hora de hacer la predicción, eligiera una categoría de las 6 que teníamos. Tras experimentar con diferentes configuraciones para el entrenamiento del modelo, se obtuvieron los siguientes resultados:```
 - ```Prueba 1: Capas sin congelar (últimas: 80), epochs (30): Las métricas de accuracy y loss presentan oscilaciones significativas durante el entrenamiento, el modelo tenía demasiados parámetros para ajustar, lo que hacía difícil que el entrenamiento fuera estable.```
 - ```Prueba 2: Capas sin congelar (últimas: 120), epochs (50): Las métricas siguen teniendo algunas oscilaciones, pero hay overfitting.```
 - ```Prueba 3: Capas sin congelar (últimas: 20), epochs (50): Las métricas empeoran, el modelo no es estable```
 - ```Prueba 4: Capas congeladas (primeras y últimas 50), epochs (50), añadimos callback: Mejora bastante el entrenamiento pero todavía observamos demasiadas oscilaciones en las métricas.```
 - ```Prueba 5: Capas congeladas (primeras y últimas 100), e
  

