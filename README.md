# IA-Retinografia
## Aplicación de técnicas de IA para la extracción automática de estructuras de interés en retinografías
Debido a restricciones de tamaño, los archivos del proyecto se almacenan externamente. Puede descargarlos desde el siguientes enlace:
- [IA-Retinografia](https://drive.google.com/file/d/1juptBlBX2XPWhbZJpMRNqV0cTUNg2ZSr/view?usp=drive_link)

## Contenido del Proyecto
### Scripts

- **Segmentacion_UNET.ipynb**: Script de la segmentación. Este notebook contiene el código para segmentar el disco y la copa óptica en imágenes de retinografías utilizando un modelo UNET.

- **retinal_features_extraction.py**: Script de extracción de características. Este script automatiza la extracción de 14 características morfológicas a partir de las imágenes segmentadas.

- **decision_tree_classification.ipynb**: Script del clasificador de árbol de decisión. Este notebook contiene el código para clasificar las imágenes de retinografías en categorías relacionadas con la presencia o ausencia de glaucoma, utilizando un modelo de árbol de decisión.

### Carpetas

- **RIM-ONE_DL_images**: Contiene las retinografías utilizadas en el proyecto.

- **RIM-ONE_DL_reference_segmentations**: Contiene las máscaras originales de las retinografías.

- **Resultados**: Contiene carpetas con las imágenes de retinografías ordenadas, las máscaras originales y las máscaras segmentadas del modelo UNET. Esta carpeta es utilizada por el script de extracción de características.

- **Resultados_UNET**: Contiene los valores de la extracción de características para el modelo UNET.

- **Resultados_Caracteristicas_RIMONE_DL_test**: Contiene los valores de la extracción de características para las máscaras originales de test.

- **Resultados_Caracteristicas_RIMONE_DL_train**: Contiene los valores de la extracción de características para las máscaras originales de prueba.

- **Datos_arbol_decision**: Contiene los archivos CSV que se usan en el script del clasificador de árbol de decisión.

### Archivos

- **modelo_copa_entrenado.h5**: Modelo de segmentación UNET entrenado para la copa óptica.

- **modelo_disco_entrenado.h5**: Modelo de segmentación UNET entrenado para el disco óptico.

- **rimone.dot**: Representación del árbol de decisiones.

  ## Preparación del Entorno
Para ejecutar los notebooks de segmentación y clasificación, es necesario preparar el entorno utilizando Miniconda. Sigue los pasos a continuación para configurar el entorno:

1. Crear un nuevo entorno con Anaconda y Python 3.8:
```sh
conda create -n Unet anaconda python=3.8

2. Activar el nuevo entorno:
    ```sh
    conda activate Unet
    ```

3. Instalar TensorFlow y otras dependencias:
    ```sh
    conda install tensorflow-gpu==2.1.0 cudatoolkit=10.1 tensorboard==2.1.0 tensorflow-estimator==2.1.0
    pip install tensorflow==2.1.0
    ```

4. Instalar Jupyter Notebook:
    ```sh
    pip install jupyter
    ```

5. Instalar Keras y otras bibliotecas necesarias:
    ```sh
    pip install keras==2.3.1
    pip install numpy scipy matplotlib scikit-image opencv-python imageio tqdm scikit-image scikit-learn graphviz

    ```

Una vez completados estos pasos, deberías tener un entorno adecuado para ejecutar los notebooks y scripts del proyecto.

### Ejecución de Jupyter Notebooks y Scripts Python

Una vez que el entorno está activado, puedes comenzar a interactuar con los notebooks y scripts del proyecto de la siguiente manera:

#### Ejecutar Jupyter Notebook

Para iniciar Jupyter Notebook y acceder a los notebooks de segmentación U-Net y el clasificador de árbol de decisiones, ejecuta el siguiente comando en tu terminal:

```bash
jupyter notebook

Esto abrirá la interfaz de Jupyter en tu navegador por defecto, donde podrás abrir y ejecutar los notebooks incluidos en el directorio del proyecto.

### Ejecutar Script de Extracción de Características
Para ejecutar el script de extracción de características, que procesa las imágenes utilizando los modelos entrenados y extrae las características relevantes, usa el siguiente comando en la terminal:
```bash
py retinal_features_extraction.py Resultados\x_test_images Resultados\mascaras_disco_UNET Resultados\mascaras_copa_UNET Resultados_UNET

Los argumentos para el comando python son los siguientes:

Resultados\x_test_images: Directorio que contiene las retinografías a examinar.
Resultados\mascaras_disco_UNET: Directorio que contiene las máscaras de discos generadas por el modelo U-Net.
Resultados\mascaras_copa_UNET: Directorio que contiene las máscaras de copas generadas por el modelo U-Net.
Resultados_UNET: Directorio donde deseas almacenar los resultados de la extracción de características.

Asegúrate de reemplazar los caminos de los directorios con los caminos reales donde tienes almacenados los archivos correspondientes en tu sistema si son diferentes a los proporcionados.
