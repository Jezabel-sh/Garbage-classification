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

# ELECCIÓN DEL MODELO:
- ¿Qué tipo de problema estás resolviendo? ```Clasificación de imágenes.```
- ¿El modelo está entrenado para un dominio similar? ```Si, clasifica muchas cosas pero no se especializa en ninguna.```
- ¿Qué modelo han elegido y por qué? ```EfficientBO que está especializado en clasificar objetos y lo reentrenaremos para nuestro caso.```
- ¿Qué dataset han seleccionado y cuál es la razón detrás de esta elección? ```Hemos elegido este dataset, ya que contiene diferentes categorias de materiales para saber como dividirlas a la hora del reciclaje, este dataset presenta imágenes con sus respectivas etiquetas lo que facilita el entrenamiento.```

- Día 2

# NUESTRO MODELO:
- Pruebas Iniciales con el modelo ```Realizamos una prueba inicial con el modelo sin entrenar, pero los resultados no eran buenos```
- Análisis, construcción, compilación y preprocesamiento de los datos: ```Preparamos los datos (se ajustan las imágenes a 224 x 224). Nuestro modelo tenía 238 capas, creamos una nueva (output), ya que nuestro objetivo era que el modelo a la hora de hacer la predicción, eligiera una categoría de las 6 que teníamos.```
- Entrenamiento del modelo ```Tras experimentar con diferentes configuraciones para el entrenamiento del modelo, se obtuvieron los siguientes resultados:```
 - ```Prueba 1: Capas sin congelar (últimas: 80), epochs (30): Las métricas de accuracy y loss presentan oscilaciones significativas durante el entrenamiento, el modelo tenía demasiados parámetros para ajustar, lo que hacía difícil que el entrenamiento fuera estable.```
 - ```Prueba 2: Capas sin congelar (últimas: 120), epochs (50): Las métricas siguen teniendo algunas oscilaciones, pero hay overfitting.```
 - ```Prueba 3: Capas sin congelar (últimas: 20), epochs (50): Las métricas empeoran, el modelo no es estable```
 - ```Prueba 4: Capas congeladas (primeras y últimas 50), epochs (50), añadimos callback: Mejora bastante el entrenamiento pero todavía observamos demasiadas oscilaciones en las métricas.```
 - ```Prueba 5: Capas congeladas (primeras y últimas 100), epochs (50), añadimos earlystopping: El modelo funciona correctamente```
- Análisis de resultados: ```Nuestro modelo es muy bueno con las imágenes de prueba del dataset, pero no tanto con las imágenes del mundo real (google)```


- Día 3

# MEJORAS DE NUESTRO MODELO:
- Conclusiones: ```Concluimos que el principal desafío radicaba en el dataset, ya que la mayoría de las imágenes consistían en un único objeto (residuo) sobre un fondo blanco. Esto limitaba la diversidad visual y podría haber reducido la capacidad del modelo para generalizar en escenarios más complejos.```
- Problemas del modelo: ```Los principales problemas de nuestro modelo eran```:
- ```Color marrón: nuestro modelo había asociado el color marrón al cartón```
- ```Tapones: si el tapón no era azul o blanco y estaba adherido a la botella, nuestro modelo lo clasificaba erróneamente como metal```
- ```Imágenes personas y animales: el modelo los identificaba como papel, ya que seguramente durante el entrenamiento tuvo imágenes de revistas y periódicos etiquetadas como papel```
- ```Residuos orgánicos: En esta categoría apenas teníamos imágenes comparado con las otras e hicimos un data augmentation, por lo que era la categoría que peor se le daba al modelo a la hora de clasificar```
- Plan de mejora: ```Para mejorar las imágenes de nuestro dataset, estuvimos evaluando otros dataset de residuos, pero las imágenes eran muy parecidas a las nuestras y no nos servían, decidimos descargarlas de internet y etiquetarlas y empezar nuestro entrenamiento con el dataset mejorado```

   

  

