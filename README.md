# ModeloCovidMX19

# Predicción de COVID-19 en México

Este proyecto se centra en la predicción de la clasificación final de pacientes de COVID-19 en México utilizando el aprendizaje automático. El modelo se ha entrenado en datos epidemiológicos recopilados durante la pandemia y se utiliza para predecir la gravedad de la enfermedad en pacientes.

## Requisitos

Antes de comenzar, asegúrate de tener los siguientes requisitos instalados:

- [RAPIDS](https://rapids.ai/) (para aceleración GPU)
- [gradio](https://www.gradio.app/) (para la interfaz web de predicción)


## Uso de la interfaz

La interfaz de predicción te permite ingresar información sobre un paciente y obtener una predicción sobre la clasificación final de su estado de salud con respecto al COVID-19. A continuación, se describen los campos de entrada:

- **Sexo**: Género del paciente (1 para masculino, 2 para femenino).
- **Tipo de Paciente**: Tipo de paciente (1 para ambulatorio, 2 para hospitalizado).
- **Intubado**: Indicador de si el paciente está intubado (1 para sí, 2 para no).
- **Neumonía**: Indicador de si el paciente tiene neumonía (1 para sí, 2 para no).
- **Edad**: Edad del paciente (entre 0 y 120 años).
- **Embarazo**: Indicador de si el paciente está embarazado (1 para sí, 2 para no).
- **Diabetes**: Indicador de si el paciente tiene diabetes (1 para sí, 2 para no).
- **EPOC**: Indicador de si el paciente tiene EPOC (1 para sí, 2 para no).
- **Asma**: Indicador de si el paciente tiene asma (1 para sí, 2 para no).
- **Inmunosupresión**: Indicador de si el paciente tiene inmunosupresión (1 para sí, 2 para no).
- **Hipertensión**: Indicador de si el paciente tiene hipertensión (1 para sí, 2 para no).
- **Otra Comorbilidad**: Indicador de si el paciente tiene otra comorbilidad (1 para sí, 2 para no).
- **Cardiovascular**: Indicador de si el paciente tiene enfermedad cardiovascular (1 para sí, 2 para no).
- **Obesidad**: Indicador de si el paciente tiene obesidad (1 para sí, 2 para no).
- **Enfermedad Renal Crónica**: Indicador de si el paciente tiene enfermedad renal crónica (1 para sí, 2 para no).
- **Tabaquismo**: Indicador de si el paciente es fumador (1 para sí, 2 para no).
- **Contacto con otro caso**: Indicador de si el paciente tuvo contacto con otro caso (1 para sí, 2 para no).
- **Toma de muestra de laboratorio**: Indicador de si se tomó una muestra de laboratorio (1 para sí, 2 para no).
- **Resultado de laboratorio**: Resultado de la muestra de laboratorio (1 para positivo, 2 para negativo).
- **Toma de muestra de antígeno**: Indicador de si se tomó una muestra de antígeno (1 para sí, 2 para no).
- **Resultado de antígeno**: Resultado de la muestra de antígeno (1 para positivo, 2 para negativo).
- **UCI**: Indicador de si el paciente estuvo en la UCI (1 para sí, 2 para no).
- **Días de Hospitalización**: Número de días de hospitalización del paciente.
- **Días con Síntomas**: Número de días desde el inicio de los síntomas.

Después de ingresar la información requerida, haz clic en "Predecir" para obtener la clasificación final del estado de salud del paciente.

## Resultados

El modelo proporcionará la clasificación final del paciente, que puede ser una de las siguientes opciones:

- 1: Caso confirmado de COVID-19.
- 3: Caso sospechoso de COVID-19.
- 6: Caso sin muestra.
- 7: Caso no aplicable.

## Resultados del Modelo

### Resultados del Modelo con Random Forest usando sklearn

```
              precision    recall  f1-score   support

           1       0.97      0.01      0.02      2431
           3       1.00      1.00      1.00    125424
           6       0.97      0.97      0.97     19345
           7       0.99      1.00      0.99    208098

    accuracy                           0.99    355298
   macro avg       0.98      0.75      0.75    355298
weighted avg       0.99      0.99      0.99    355298
```

### Resultados del Modelo con KNN usando sklearn

```
              precision    recall  f1-score   support

           1       0.30      0.01      0.03      2431
           3       0.95      0.84      0.89    125424
           6       0.96      0.92      0.94     19345
           7       0.90      0.97      0.93    208098

    accuracy                           0.92    355298
   macro avg       0.78      0.69      0.70    355298
weighted avg       0.91      0.92      0.91    355298
```

### Resultados del Modelo con Random Forest usando cuML

El modelo de Random Forest entrenado con cuML obtuvo una precisión de aproximadamente 0.992.

### Resultados del Modelo con KNN usando cuML

El modelo de KNN entrenado con cuML también obtuvo una precisión de aproximadamente 0.992.

```

Estos son los resultados de los modelos de aprendizaje automático entrenados en los datos epidemiológicos de COVID-19 en México. Ten en cuenta que los resultados pueden variar según los datos utilizados y los hiperparámetros del modelo.

```

## Notas adicionales

- Este proyecto utiliza el paquete [RAPIDS](https://rapids.ai/) para acelerar el procesamiento en GPU.
- La interfaz web se crea con [gradio](https://www.gradio.app/) para facilitar la predicción de casos de COVID-19.
- Los resultados de predicción son informativos y no deben utilizarse como diagnóstico médico oficial. Si tienes síntomas de COVID-19, consulta a un profesional de la salud.
- Se implementó RAPIDS en vez de sklearn donde fue posible.