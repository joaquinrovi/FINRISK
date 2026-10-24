# FINRISK Colombia · Exploración de datos

Notebook de apoyo a la primera entrega de **Despliegue de soluciones analíticas**. Examina la cobertura y la calidad de la información financiera preliminar de 2019–2024, y visualiza los indicadores resumidos en los avances del equipo.

## Alcance y procedencia

Los archivos de `data/agregados/` provienen del paquete de avances **FINRISK** compartido por el equipo. Se conservan como insumos y se distinguen de las tablas y figuras generadas por este notebook. El análisis no reproduce íntegramente la lectura y consolidación de las fuentes originales: esos archivos individuales no están incluidos.

Las cifras de empresas, observaciones, incidencias y cruces se interpretan con sus respectivas unidades. El cruce con insolvencia es preliminar; no constituye una etiqueta de entrenamiento ni permite clasificar la ausencia en un listado como ausencia de insolvencia. No se presentan probabilidades, métricas de un modelo ni decisiones de crédito.

Referencias de las fuentes originales citadas en los avances:

- [Estados financieros NIIF: situación financiera](https://www.datos.gov.co/d/pfdp-zks5).
- [Estados financieros NIIF: resultado integral](https://www.datos.gov.co/d/prwj-nzxa).
- [Informes de procedimientos de insolvencia de Supersociedades](https://www.supersociedades.gov.co/web/procedimientos-de-insolvencia/informes).

La ejecución no descarga estas fuentes ni modifica los insumos recibidos.

## Archivos

```text
notebooks/01_EDA_FINRISK.ipynb     Notebook principal
data/agregados/                  Cuatro CSV y dos TXT del avance recibido
data/privados/                   Microdatos opcionales; excluidos de Git
src/auditoria_microdatos.py      Apoyo al análisis individual opcional
results/tablas/                  Tablas del análisis
results/figuras/                 Gráficas del análisis
requirements.txt                Dependencias
```

El análisis principal funciona con los agregados incluidos. La auditoría individual es opcional y requiere que el equipo suministre `data/privados/base_financiera_preliminar.csv`. Mientras ese archivo no esté disponible, no deben interpretarse las comprobaciones individuales como realizadas.

## Abrir y ejecutar

1. Descomprima el paquete y conserve su estructura de carpetas.
2. Abra `notebooks/01_EDA_FINRISK.ipynb` en JupyterLab o en VS Code con la extensión de Jupyter.
3. Seleccione el entorno de Python que tenga instaladas las dependencias y ejecute **Run All / Ejecutar todo**.

El notebook detecta la raíz del proyecto tanto si se abre desde la carpeta principal como desde `notebooks/`. El notebook incluido ya contiene las salidas de una ejecución completa de sus 12 celdas de código. Al volver a ejecutarlo, las salidas visibles se guardan al guardar el notebook; las tablas y figuras se escriben en `results/`.

### Preparación en Windows

El entorno se comprobó con Python 3.12. Abra PowerShell en la carpeta que contiene este README y ejecute:

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m pip install jupyterlab
.\.venv\Scripts\python.exe -m ipykernel install --user --name finrisk-eda --display-name "Python (FINRISK EDA)"
.\.venv\Scripts\python.exe -m jupyterlab
```

En JupyterLab, abra el notebook y seleccione **Python (FINRISK EDA)**. También puede elegir `.venv` como entorno en VS Code. Los comandos utilizan directamente el Python del entorno y no requieren activar scripts de PowerShell.

## Compartir en GitHub

Este paquete está preparado para que Joaquín lo publique; su creación no implica que ya exista un repositorio o que se hayan subido archivos.

1. Cree un repositorio en su cuenta de GitHub y elija su visibilidad con el equipo.
2. En **Add file → Upload files**, cargue los archivos y carpetas del proyecto descomprimido, conservando su estructura: notebook, agregados, código, resultados, README, dependencias y `.gitignore`. No cargue el ZIP como sustituto del notebook: GitHub necesita el archivo `.ipynb` para mostrarlo.
3. Revise el contenido antes de confirmar la carga y compruebe después que el notebook se visualiza con sus salidas.

La carga manual desde el navegador no aplica automáticamente `.gitignore`: excluya `.venv`, `__pycache__`, `.ipynb_checkpoints` y los datos privados al seleccionar archivos. No publique los microdatos ni salidas con NIT u otros identificadores. Para una publicación futura con Git, `.gitignore` ya excluye `data/privados/`; verifique igualmente los archivos seleccionados.

## Pendientes metodológicos

La base individual, los conflictos contables, las unidades de reporte, la disponibilidad temporal de los estados y la definición histórica del evento requieren validación del equipo. El filtro descriptivo estricto no debe reutilizarse automáticamente para seleccionar una muestra de entrenamiento. Las comprobaciones disponibles en el notebook ayudan a revisar el avance; no sustituyen esos acuerdos.

## Documentación de GitHub

- [Cargar archivos y carpetas en un repositorio](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository).
- [Visualización de notebooks en GitHub](https://docs.github.com/en/repositories/working-with-files/using-files/working-with-non-code-files#working-with-jupyter-notebook-files-on-github).
