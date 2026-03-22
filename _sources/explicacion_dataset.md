# Explicacion del dataset 

El dataset fue sacado de la pagina de kaggle de una competicion realizada en el año 2015, con aproxiadamente 40 millones de registros, corresponde a registros de impresiones de anuncios en tiempo real y se utiliza para el problema de **predicción de Click-Through Rate (CTR)**.  
Cada fila representa **una impresión de un anuncio**, y la variable objetivo indica si el usuario hizo click o no.

**Fuente de los datos**: [Fuente de prediccion](https://www.kaggle.com/competitions/avazu-ctr-prediction/data)

- **Número de observaciones:** 40,428,967  
- **Número de variables:** 24  

## Explicacion de variables del dataset 
---
### Variable objetivo 
| Variable | Tipo | Descripción |
|--------|------|-------------|
| `click` | int | Variable binaria objetivo. Toma el valor **1** si el anuncio fue clickeado y **0** en caso contrario. |

---
### variable temporal
| Variable | Tipo | Descripción |
|--------|------|-------------|
| `hour` | int | Hora en la que ocurrió la impresión del anuncio, en formato **YYMMDDHH**. Permite extraer características temporales como hora del día o día de la semana. |


### Variables categoricas anonimas

Estas variables representan características del contexto del anuncio, usuario o entorno, y han sido anonimizadas por Avazu.


| Variable | Tipo | Descripción |
|--------|------|-------------|
| `C1` | int | Variable categórica anónima asociada al contexto del anuncio. |
| `C14` | int | Variable categórica anónima. |
| `C15` | int | Variable categórica anónima. |
| `C16` | int | Variable categórica anónima. |
| `C17` | int | Variable categórica anónima. |
| `C18` | int | Variable categórica anónima. |
| `C19` | int | Variable categórica anónima. |
| `C20` | int | Variable categórica anónima. |
| `C21` | int | Variable categórica anónima. |

### Variables de sitio web 
Describen el sitio web donde se mostró el anuncio.

| Variable | Tipo | Descripción |
|--------|------|-------------|
| `site_id` | object | Identificador único del sitio web. |
| `site_domain` | object | Dominio del sitio web. |
| `site_category` | object | Categoría del sitio web. |

---
### Variables de aplicación
Describen la aplicación donde se mostró el anuncio (si aplica).

| Variable | Tipo | Descripción |
|--------|------|-------------|
| `app_id` | object | Identificador único de la aplicación. |
| `app_domain` | object | Dominio de la aplicación. |
| `app_category` | object | Categoría de la aplicación. |

---
### variables de dispositivo
Contienen información del dispositivo desde el cual se mostró el anuncio.

| Variable | Tipo | Descripción |
|--------|------|-------------|
| `device_id` | object | Identificador único del dispositivo (anonimizado). |
| `device_ip` | object | Dirección IP del dispositivo (anonimizada). |
| `device_model` | object | Modelo del dispositivo. |
| `device_type` | int | Tipo de dispositivo (ej. móvil, tablet, desktop). |
| `device_conn_type` | int | Tipo de conexión del dispositivo (ej. wifi, datos móviles). |

---
### variable de identificador 
| Variable | Tipo | Descripción |
|--------|------|-------------|
| `id` | float | Identificador único de la impresión del anuncio. No aporta información predictiva y suele eliminarse antes del modelado. |
