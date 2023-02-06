# Configuración de un entorno de trabajo para Ciencia de Datos

@author: jeduque, 06/02/2023

## Conda  
Conda es una herramienta de gestión de paquetes y entornos de Python, que permite a los usuarios instalar paquetes y controlar su compatibilidad con otros paquetes en un entorno aislado. También es útil para resolver dependencias y para compartir y replicar entornos de desarrollo en un equipo.  
Para instalar conda basta con obtener miniconda (la versión minima con python, conda y modulos base) o Anaconda, una distribución más completa con más de 150 modulos e interfac gráfica.
`>> wget -0 anaconda.sh link_distribucion`

### Recomendaciones:
1. Crear y utilizar entornos separados para cada proyecto: esto asegura que las dependencias y las versiones de los paquetes se mantengan separadas y evita conflictos.

2. Mantener actualizado Conda: correr regularmente el comando "conda update conda" para asegurarse de tener la última versión de la herramienta.

3. Verificar las dependencias antes de instalar paquetes: usar el comando "conda list" para verificar si hay paquetes en conflicto o dependencias no satisfechas antes de instalar nuevos paquetes.

4. Almacenar los entornos en un lugar accesible: utilizar el comando "conda env export" para exportar un entorno completo y guardarlo en un archivo para su posterior uso.

5. Utilizar el canal de Anaconda para descargar paquetes: Anaconda es una distribución de Python que incluye un gran número de paquetes, y los paquetes descargados desde el canal de Anaconda a menudo son más confiables que los descargados desde otros canales.

6. Documentar los entornos: mantener un registro de las dependencias y las versiones de los paquetes instalados en cada entorno, para poder replicarlos fácilmente en el futuro.

### Comandos

- `conda create` Crea un nuevo entorno con los paquetes especificados.
 `conda create --name py35 python=3.5 pandas=`
- `conda env list` Muestra una lista de todos los entornos existentes.
- `conda list` Muestra una lista de todos las librerias existentes en un entorno.
- `conda activate xx` Activa un entorno específico.
- `conda update pandas` Actualiza una libreria en un entorno específico.
- `conda install pandas=1.2` Instala una libreria en un entorno específico.
- `conda install  --channel conda-forge paquete` Instala una libreria de una fuente específica.
- `conda list --revision` Muestra una lista de los cambios en laslibrerias en un entorno.
- `conda install --revision 0` Vuelve al estado 0 del entorno
- `conda deactivate` Desactiva el entorno actual.
- `conda remove pandas`: `Elimina un paquete específico.
- `conda env remove --name py35`: `Elimina un ambiente específico.
- `conda create  --name py39 --copy --clone py35` Copia un ambiente a partir de otro
- `conda env export --file environment.yml`: Crea un archivo con el ambiente generado
- `conda env create --file environment.yml`: Crea un ambiente a partir de un archivo


#### Mamba
Mamba es una herramienta de gestión de paquetes para Python que se promueve como una alternativa más rápida y ligera a conda. Mamba utiliza el mismo formato de paquetes que conda, por lo que los paquetes descargados desde conda también pueden ser utilizados en mamba. Mamba también es compatible con los comandos de conda y puede ser utilizado junto con conda, lo que le permite a los usuarios aprovechar la potencia de ambas herramientas.