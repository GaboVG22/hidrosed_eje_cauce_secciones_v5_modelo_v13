# HidroSed · Módulo Eje Cauce y Secciones v5 · Modelo v13

Versión corregida del módulo de eje del cauce y secciones. Esta versión incorpora el modelo probado de la aplicación `app_secciones_kmz_v13_fix_km_final_utm19s_3d`, especialmente para generar secciones y perfil 3D.

## Objetivo

Generar y revisar secciones transversales del cauce sobre el tramo útil entre el PC hidrológico y el PC cuenca soporte, usando el eje del cauce como referencia obligatoria.

## Mejora principal v5

Se incorpora un nuevo modo de generación:

```text
Desde curvas de nivel v13
```

Este modo genera las secciones por intersección entre:

```text
línea transversal de sección ∩ curvas de nivel de apoyo
```

Luego construye el perfil station-cota de izquierda a derecha mirando aguas abajo y genera un perfil 3D con coordenadas hidráulicas:

```text
X = progresiva sobre eje
Y = offset transversal desde eje
Z = cota
```

Esto evita que las secciones se vean deformadas o aplastadas por la escala UTM.

## Inputs obligatorios

1. Eje del cauce KMZ/KML con línea.
2. PC hidrológico KMZ/KML con punto.
3. PC cuenca soporte KMZ/KML con punto.

## DEM

La app permite:

- Descargar DEM desde OpenTopography con API Key.
- Cargar DEM GeoTIFF manual.

El DEM se usa para orientar el eje, perfil longitudinal y secciones naturales. Para el modo v13, la fuente principal de la sección son las curvas de nivel de apoyo.

## Curvas de nivel de apoyo

Para el modo v13 debes cargar curvas de nivel de apoyo en:

- KMZ/KML con elevación Z o nombre con cota.
- DXF con polilíneas 3D o elevación.

## Modo de generación recomendado

Para replicar el comportamiento de la app antigua que funcionaba mejor:

```text
Modo de generación de secciones: Desde curvas de nivel v13
```

Parámetros iniciales:

```text
Separación secciones: 50 a 100 m
Semi-ancho sección: 100 a 200 m
```

## Visualización

La aplicación incluye:

1. Vista del eje y secciones en planta.
2. Perfil longitudinal interactivo.
3. Ventana independiente de cada sección por km.
4. Editor Station-Cota.
5. Vista 3D hidráulica interactiva.

## Descargas

- KMZ eje + secciones.
- CSV perfil longitudinal.
- Excel tipo HEC-RAS.
- JSON técnico.

## Streamlit Cloud

```text
Main file path: app.py
Python version: 3.11
```

## Dependencias

La app mantiene un entorno liviano y estable:

- Sin pysheds.
- Sin geopandas.
- Sin scipy.
- Sin scikit-image.
- Sin Earth Engine.

