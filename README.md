# Ipre-reconocimiento-facial-en-jovenes

## Cycle GAN: 
Este codigo permite entrenar y testear una Cycle GAN (originalmente extraido de: https://github.com/hyunbo9/yonsei). 
Al final de la funcion *train* se puede especificar un path de Google Drive donde guardar los checkpoints del modelo.
Los parametros mas importantes son: 
* checkpoint_dir: Si continue_train es True, buscará en este path el checkpoint a cargar
* test_dir: Carpeta donde se guarda el test generado                           
* dataset_dir: Path donde se encuentra el set de entrenamiento o de test. Para train se necesitan las carpetas trainA y trainB (imagen joven y vieja respectivamente) y para test se necesitan testA y testB                          
* phase: Puede ser test o train
* which_direction: Puede ser BtoA o AtoB dependiendo si se busca envejecer o rejuvenecer

## VGG-FACE:

Este archivo tiene todo el pipeline para calcular el d-prime de un conjunto de imagenes, utilizando VGG-FACE como extractor de features y similaridad del coseno clasificador. 
Los unicos parametros importantes son las carpetas: 
* type_pos: Aca van los pares de imagenes que son genuinas
* type_neg: Aca van los pares de imagenes que son impostores
El código es bastante directo de correr, se puede encapsular en una funcion para probar distintos datasets.

## Denoising

Contiene un codigo para hacer denoising de una imagen. El parámetro *h* de la función *fastNlMeansDenoisingColored* (Es el 5to parámetro), regula la cantidad de denoising aplicado a la imagen

## Split Images

Código para crear las carpetas trainA, trainB, testA y testB a partir de las carpetas de imagenes del dataset para utilizar en el código de Cycle GAN

## Disorder Images

Código para crear las carpetas de genuinos e impostores para los datasets originales y los envejecidos/rejuvenecids por las GANs, estas carpetas se pueden usar directamente para calcular el d-prime en el archivo VGG-FACE

