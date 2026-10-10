# TELECOM-ANALYSIS-FINAL-PROJECT-SPRINT-7
Análisis de empresa de telecomunicaiones.

# 📞 Análisis de Clientes y Consumo: ConnectaTel 2024

Este proyecto realiza un análisis exploratorio de datos (EDA), limpieza profunda y segmentación de clientes para **ConnectaTel**, una empresa de telecomunicaciones en Latinoamérica. El análisis traduce datos crudos de comportamiento de red en estrategias comerciales accionables y perfiles estadísticos reproducibles.

## 🎯 Objetivos del Proyecto
* **Integrar y limpiar** bases de datos provenientes de tres fuentes distintas (`plans.csv`, `users.csv` y `usage.csv`).
* **Aplicar técnicas de validación**, estandarización de tipos de datos y detección de valores inconsistentes (fechas futuras y *sentinels*).
* **Construir un perfil estadístico** del uso (llamadas y mensajes) por cliente y por segmentos demográficos.
* **Detectar outliers** y comportamientos atípicos mediante métodos estadísticos (IQR) y visuales (Boxplots/Histogramas).
* **Crear segmentaciones de clientes** basadas en edad, país y comportamiento de uso.
* **Visualizar diferencias entre segmentos** y extraer insights comerciales relevantes para la retención y el *upselling*.
* **Documentar todo el proceso** en un Jupyter Notebook estructurado, junto con este README reproducible para GitHub.

## 🛠️ Tecnologías Utilizadas
* **Python 3.x**
* **Pandas** • Integración, limpieza y estandarización de tipos de datos
* **NumPy** • Lógica condicional, cálculo de IQR y segmentación eficiente
* **Seaborn & Matplotlib** • Visualización estadística, histogramas y detección visual de outliers

---

## 🔍 Resumen del Proceso y Hallazgos Clave

### 1. Validación y Estandarización de Datos
* Se sanearon valores *sentinels* en la edad (`-999`) utilizando la mediana, y caracteres corruptos (`?`) en las ciudades.
* Las columnas temporales fueron estandarizadas al tipo de dato correcto, marcando fechas futuras imposibles como nulas (`pd.NaT`).
* Se realizó una verificación **MAR (Missing At Random)** para las columnas de consumo. Se demostró científicamente que los nulos en minutos ocurren al 100% en registros de tipo SMS/Datos, confirmando que la ausencia de datos se debe a la naturaleza del servicio y no a una pérdida de información.

### 2. Perfil Estadístico y Análisis Visual (Forma de la Distribución)
* **Edad:** Presenta una distribución simétrica/uniforme sin valores atípicos.
* **Mensajes y Minutos:** Presentan distribuciones fuertemente **sesgadas a la derecha**. La gran mayoría consume volúmenes mínimos, mientras que una minoría estira la cola del gráfico.

### 3. Detección de Outliers e Impacto de Negocio
* Se detectaron múltiples *outliers* superiores en las variables de consumo utilizando diagramas de caja (*Boxplots*).
* **Decisión de negocio:** Se optó por **mantenerlos** en el dataset, ya que representan a los usuarios más rentables y operativos de la red celular (*Heavy Users*). Borrarlos sesgaría el cálculo de la facturación real.

### 4. Segmentación Estratégica de Clientes
Creamos tres nuevas dimensiones de análisis mediante comparaciones lógicas:
* **grupo_uso:** Categorizado en *Bajo uso*, *Uso medio* y *Alto uso* (según volumen de llamadas y mensajes).
* **grupo_edad:** Segmentado de forma secuencial en *Joven*, *Adulto* y *Adulto Mayor*.
* **País/Ciudad:** Mapeo de la distribución geográfica para identificar mercados clave.

---

## 🚀 Recomendaciones Comerciales Extraídas
* **Estrategia de Upselling:** Migrar de forma proactiva a los *Heavy Users* del plan Básico hacia un plan intermedio superior para evitar su fuga (*churn*) por facturas elevadas.
* **Optimización de Oferta:** Reducir la bolsa de SMS incluidos en el plan Básico (cuya mediana de uso es cercana a cero) y reemplazarla por más Gigabytes de navegación, un beneficio altamente valorado por los segmentos *Joven* y *Adulto*.

---
*Proyecto desarrollado con fines prácticos y demostrativos en el área de Análisis de Datos para Telecomunicaciones.*
