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
