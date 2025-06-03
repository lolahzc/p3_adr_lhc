# Informe de Resultados: Estimación y Simulación con Filtros de Kalman

## 1. Introducción

Este proyecto tiene como objetivo implementar y comparar el desempeño de tres variantes del filtro de Kalman, cada una con diferente dimensionalidad del estado (3D, 7D y 8D), en un entorno simulado con distintas configuraciones de ruido. Se analizó su precisión y robustez a través de simulaciones y visualizaciones comparativas.

## 2. Modelos de Estimación Implementados

Se utilizaron tres filtros de Kalman con diferentes representaciones del estado:

- **Filtro Kalman 3D**
- **Filtro Kalman 7D**
- **Filtro Kalman 8D**

## 3. Metodología

1. **Estimación**: Se ejecutó cada filtro sobre los datos del rosbag.
2. **Visualización**: Se compararon las trayectorias estimadas con la trayectoria real.
3. **Análisis de escenarios**: Se evaluó el rendimiento en tres condiciones de ruido:

   - **Caso base**: configuración por defecto.
   - **Alta incertidumbre en la observación**: se incrementó la covarianza del sensor.
   - **Alta incertidumbre en el modelo de movimiento**: se incrementó la covarianza del proceso.

## 4. Resultados

### 4.1 Caso Base

- El filtro 3D fue el más rápido computacionalmente pero el menos preciso.
- El filtro 7D logró un buen equilibrio entre precisión y complejidad.
- El filtro 8D mostró un leve sobreajuste, pero buena respuesta en trayectorias más complejas.

### 4.2 Alta Incertidumbre en la Observación

- El filtro 3D sufrió desviaciones significativas debido a su menor capacidad de integración de estados.
- El filtro 8D mostró mayor estabilidad, beneficiándose de la redundancia del modelo.

### 4.3 Alta Incertidumbre en el Modelo de Movimiento

- El filtro 3D fue el menos afectado, dado que su modelo de movimiento es más simple.
- El filtro 7D manejó razonablemente bien la incertidumbre.
- El filtro 8D mostró oscilaciones en los estados derivados (como aceleraciones), evidenciando sensibilidad al modelo dinámico más complejo.

## 5. Conclusiones

- **Filtro 3D**: útil para aplicaciones ligeras y rápidas, pero limitado en escenarios con mucho ruido o dinámica compleja.
- **Filtro 7D**: balance ideal entre complejidad y precisión.
- **Filtro 8D**: potente en entornos complejos, pero más sensible a mala modelación y requiere mayor ajuste fino.

El análisis visual de las trayectorias permitió identificar errores sistemáticos, y los resultados fueron consistentes con las expectativas teóricas de cada modelo.
