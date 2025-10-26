# Proyecto: Segmentación del Miocardio en Imágenes de Resonancia Magnética

Proyecto de semestre para el curso **Inteligencia Computacional (EL4106-1)**, enfocado en la aplicación de **redes neuronales convolucionales (CNN)** para la segmentación médica del miocardio en imágenes de resonancia magnética (MRI).

---

## Descripción del Proyecto

El trazado de las estructuras cardíacas a partir de imágenes MRI es una tarea clínica clave para evaluar la función del corazón.  
En este proyecto se aborda la **segmentación automática del miocardio**, formulada como un problema de clasificación por píxel, donde el modelo debe distinguir entre el miocardio (clase 1) y el fondo (clase 0).

El modelo implementado utiliza una arquitectura **Encoder–Decoder** basada en **U-Net**, inspirada en el paper:

> Ronneberger, O., Fischer, P., & Brox, T. (2015).  
> *U-Net: Convolutional Networks for Biomedical Image Segmentation.*  
> [arXiv:1505.04597](https://arxiv.org/abs/1505.04597)

---

## Arquitectura Utilizada

- **Modelo:** U-Net 2D  
- **Framework:** PyTorch  
- **Optimización:** Adam y AdamW  
- **Funciones de pérdida:**  
  - `Dice Loss`  
  - `Binary Cross Entropy with Logits (BCE)`  
  - Combinación `0.5 * BCE + 0.5 * Dice`  

El modelo sigue el esquema clásico de *encoder-decoder*:
- El **encoder** extrae características progresivamente reduciendo la resolución espacial.  
- El **decoder** reconstruye la segmentación incrementando la resolución hasta el tamaño original.  
- Se incluyen *skip connections* para conservar detalles espaciales.

---

## Dataset

- **Fuentes:** bases públicas **ACDC** y **York**.  
- **Formato:** imágenes en escala de grises y máscaras binarias anotadas por expertos.  
- **Preprocesamiento:** normalización y redimensionamiento a resolución fija.

El conjunto de datos se divide en:
- `Train`: ~70%
- `Validation`: ~15%
- `Test`: ~15%


