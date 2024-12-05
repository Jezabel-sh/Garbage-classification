🗑️ Garbage Classification

Día 1

📌 Motivos para elegir el proyecto:

    ¿Qué relevancia tiene este tema para ustedes?
    Queríamos crear una herramienta útil para nuestro día a día, que nos permitiera identificar los materiales que componen los productos.

    Fases del proyecto:
    1️⃣ Crear un modelo que clasifique correctamente los materiales.
    2️⃣ Implementar el modelo en una aplicación que permita al usuario tomar una foto y clasificar automáticamente el material.

    ¿Cómo puede generar utilidad en un caso real?
    Nuestro principal objetivo es identificar los objetos para reciclar en el contenedor correspondiente.

🗂️ Reflexión sobre el Dataset:

    ¿El dataset es balanceado?
    ❌ No, falta equilibrar el número de imágenes de todas las categorías.

    ¿Deberemos hacer mucha limpieza?
    ✅ No, solo es necesario reestructurar el tamaño y equilibrar las imágenes.

    ¿Es algún problema el formato de alguna variable?
    📏 Sí, el tamaño de las imágenes.

    ¿Tiene suficientes registros para entrenar el modelo?
    ✅ Sí, aunque agregaremos más imágenes para equilibrar las categorías.

🛠️ Elección del Modelo:

    ¿Qué tipo de problema están resolviendo?
    Clasificación de imágenes.

    ¿El modelo está entrenado para un dominio similar?
    ✅ Sí, clasifica muchos objetos, aunque no se especializa en ninguno.

    ¿Qué modelo han elegido y por qué?
    Seleccionamos EfficientBO, un modelo especializado en clasificar objetos, que reentrenamos para nuestro caso.

    ¿Qué dataset seleccionaron y por qué?
    Elegimos un dataset que contiene categorías de materiales para dividirlos según el reciclaje. Incluye imágenes con etiquetas, facilitando el entrenamiento.

Día 2
🔍 Nuestro Modelo:

     ❌ Pruebas Iniciales:
        Hicimos pruebas con el modelo sin entrenar, pero los resultados no fueron satisfactorios.

     🚧 Procesamiento de Datos:
        Ajustamos las imágenes a 224x224.
        Nuestro modelo tiene 238 capas. Añadimos una capa de salida para clasificar entre 6 categorías.

     📈 Resultados del Entrenamiento:
        Prueba 1: Últimas 80 capas sin congelar, 30 epochs. Métricas inestables por exceso de parámetros.
        Prueba 2: Últimas 120 capas sin congelar, 50 epochs. Menos inestabilidad, pero hay overfitting.
        Prueba 3: Últimas 20 capas sin congelar, 50 epochs. Peor estabilidad en las métricas.
        Prueba 4: Congelamos las primeras y últimas 50 capas, 50 epochs, añadimos callback. Mejoró el entrenamiento, pero las métricas seguían               inestables.
        Prueba 5: Congelamos las primeras y últimas 100 capas, 50 epochs, añadimos early stopping. ¡El modelo funcionó correctamente!

     🔎 Análisis de Resultados:
        El modelo tiene buen rendimiento con las imágenes del dataset, pero no generaliza bien con imágenes externas (por ejemplo, de Google).

Día 3
🚀 Mejoras en el Modelo:

     👀 Conclusión:
        El principal desafío era el dataset. La mayoría de las imágenes contenían un único objeto (residuo) sobre un fondo blanco, limitando la              diversidad visual y la capacidad de generalización.

     ❓ Problemas Detectados:
        Color Marrón: Asociado erróneamente al cartón.
        Tapones: Si el tapón no era azul/blanco y estaba adherido a la botella, se clasificaba como metal.
        Personas y Animales: Clasificados como papel, posiblemente por imágenes de revistas/periódicos durante el entrenamiento.
        Residuos Orgánicos: Categoría desbalanceada, incluso con data augmentation, era la peor clasificada.

      💡 Plan de Mejora:
         Evaluamos otros datasets de residuos, pero eran similares al nuestro. Decidimos descargar imágenes de internet, etiquetarlas y entrenar con          este dataset mejorado.
