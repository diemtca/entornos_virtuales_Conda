# Entornos virtuales con Conda

## Instalación de conda desde la terminal

Debes ingresar al navegador y escribir "Anaconda downloads", haces click en "Get Additional Installers" y copias la dirección del instalador que necesitas, según tu sistema operativo

``` sh
wget -O anaconda.sh <link_copiado>

# para linux (si utilizas WSL  copias el link de instalación para linux)
wget -O anaconda.sh <link_linux>
```
Despues de completar la descarga, ejecutamos el instalador según el shell que utilicemos

Para Bash:

```bash
bash anaconda.sh
```

Para Zsh:

```zsh
zsh anaconda.sh
```

Para Fish:

```fish
fish anaconda.sh
```

Para csh o tcsh:

```csh
csh anaconda.sh
```

Para PowerShell (Windows):

```powershell
.\anaconda.sh
```

Anaconda trae consigo instalados **Jupyter Notebooks**, para correrlos podemos ejecutar este comando en la terminal:
```bash
jupyter-notebook
```
Arrojará una dirección que puede ser copiada en el navegador para trabajar nuestras notebooks en el servidor

**Anaconda** tiene por defecto un ambiente virtual llamado **base**. La terminal puede configurarse de tal manera que abra este ambiente de manera predeterminada cada vez que entremos a la terminal.
``` sh
 conda config --set auto_activate_base <false_or_true>
```
### Comandos útiles para el manejo de *Anaconda*
``` sh
# Muestra todos los ambientes virtuales creados en conda, si está en uso lo marca con un asterisco (*)
conda env list
#Para crear un ambiente: 
conda create --name <nombre> python=<version> <pandas=<ver1> ...
#Para activar un ambiente: 
conda activate <nombre_del_ambiente>
#Para ver las dependencias de un ambiente:
conda list
#ver información de algún paquete en específico
conda list <python>
#Para actualizar una dependencia a la versión más reciente: 
conda update <nombre>
# Instalar una dependencia
conda install <nombre>=<version>
#Para crear un ambiente a partir de otro: 
conda create --name <nombre_ambiente_nuevo> --copy <nombre_ambiente_anterior>
#Para desactivar el ambiente actual: 
conda deactivate
#Para desinstalar un paquete: 
conda remove <nombre>
#Para eliminar un ambiente: 
conda env remove --name <nombre>
```

### Comandos avanzados para el manejo de *Anaconda*

Cuando instalamos un paquete en un ambiente, conda busca en repositorios o canales suyos y los descarga. Estos canales no tienen todos los paquetes que realmente existen, por lo que por defecto algunos paquetes (como `boltons`) no estarán disponibles. Si tratamos de instalar un paquete así, conda nos dirá que no lo encontró y nos mostrará la lista de canales donde buscó el paquete (cada canal es una URL).

Para resolver esto debemos agregar más canales. Para saber que canal agregar nos dirigimos a [https://anaconda.org/](https://anaconda.org/) y en la barra de búsqueda buscamos nuestro paquete.

Los resultados de esta búsqueda serán el paquete anterior pero prefijado con distintos nombres de canales (por ejemplo para boltons tendremos conda-forge, lightsource2-tag, entre otros). Debemos seleccionar el canal adecuado para nuestra plataforma.

``` sh
#Para instalar un paquete desde un canal específico: 
conda install --channel <nombre_canal> <nombre_paquete>
#Podemos hacer seguimiento a los diferentes estados o versiones de un ambiente, los cuáles reciben formalmente el nombre de revisiones.
#Para listar las revisiones de un ambiente: 
conda list --revision
# Si queremos volver a un punto de una revisión anterior podemos usar:
conda install --revision <numero de la revisión>

#Para exportar un ambiente: 
conda env export #puede mostrar exceso de información con versiones y subversiones de otras dependencias
conda env export --no-builds #exporta sin mostrar este exceso de información
conda env export --from-history #exporta solo mostrando unicamente las dependencias que instalamos de forma manual (RECOMENDADA)
conda env export --file <requirements.yml> #exporta los paquetes al archivo indicado

#Podemos crear un ambiente a partir de un archivo
conda env create --file <requirements.yml>
```
### Acelerar la creación de ambientes virtuales con Mamba

Mamba es una re implementación de Conda para crear ambientes virtuales.

Mamba permite resolver (descargar) dependencias en paralelo, por lo tanto es más rapido que conda.

Mamba se instala a través de Conda con `conda install --channel conda-forge mamba`

- Este comando lo debemos ejecutar mientras estamos en el ambiente `base`

Para obtener la ayuda de mamba: `mamba --help`

Los comandos de conda para instalar o crear ambientes a partir de un archivo que aprendimos anteriormente también sirven en mamba, simplemente usamos `mamba` en lugar de `conda`