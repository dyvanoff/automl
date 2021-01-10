# AutoML - H2O

## Integrantes

- Leonardo Palacios
- Marcelo Tisera
- Dario Yvanoff

## Estructura del GIT
```
|-imagenes
|-notebooks
| |-AutoML_Practico_MNIST_H2O                      <- Notebook H2O
| |-AutoML_Practico_MNIST_SKLEARN.ipynb            <- Notebook Tradicional
| |-AutoML_Practico_MNIST_Keras.ipynb              <- Notebook Tradicional
| |-AutoML_Practico_MNIST_SKLEARN-checkpoint.ipynb
|-h2o_modelos
| |-automl_h2o_best_model                          <- Modelo H2O entrenado
```

## Setup
#### Para visualizar Notebooks .ipynb
* Correr directamente sobre Google Colab

#### Para visualizar Notebbok H2O
- Tener instalado Java JRE
- Instalar H20 Flow a partir de los pasos del sitio oficial de [H2O.ai](http://h2o-release.s3.amazonaws.com/h2o/rel-zermelo/3/index.html)

- O directamente descargar desde aqui [H20](http://h2o-release.s3.amazonaws.com/h2o/rel-zermelo/3/h2o-3.32.0.3.zip), descomprimir y luego ejecutar el .jar


```bash
cd ~/Downloads
unzip h2o-3.32.0.3.zip
cd h2o-3.32.0.3
java -jar h2o.jar
```

> Para acceder a la H2O Flow ingresar a [http://localhost:54321/](http://localhost:54321/)

## Cómo usar H2O Flow

1) Una vez dentro de **H2O Flow** dirigirse a `Flow > Open Flow` y elegir el archivo `AutoML_Practico_MNIST_H2O`

> ![](/imagenes/automl_open_flow.png)

2) En esta notebook encontraremos los pasos para:

* Importar archivo de train
* Parsear archivo de train
* Idem con archivo de test
* Seleccionar la opcion de **Run AutoML** y definir los parametros de entrenamiento

> ![](/imagenes/autom_flow_run_automl.png)
>
> En nuestro caso elegimos **kfold=3**, **max_runtime_secs=3600** y solamente utilizamos el modelo de DeepLearning


De esta manera se puede correr todo el proyecto y luego de 1hs (*más adelante detallamos como cargar un modelo ya entrenado*) devuelve el resultado:

> ![](/imagenes/autom_flow_results.png)

Al seleccionar algun modelo del ranking nos devuelve todo el set de metricas del modelo, tales como:

* Resumen de los parametros del modelo seleccionado
* Scoring - Logloss
* Ranking de Variables más importantes
* Confussion Matrix
* Metricas de entrenaminto, validacion y cross validation

> ![](/imagenes/autom_flow_model_summary.png)

## Cargar Modelo Entrenado

1) Dentro de **H2O Flow** Dirigirse a `Model > Import Model...`

> ![](/imagenes/automl_open_trained_model.png)

2) Esta accion agregara un campo en la notebook en donde deberemos especificar la ruta del archivo a cargar, seleccion  `Import` y luego `View Model`

> ![](/imagenes/automl_imported_model.png)

3) Finalmente podremos navegar por toda la informacion que nos devuelve H2O sobre el modelo.
