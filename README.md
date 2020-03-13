# Instalar entorno en ubuntu 0 => 100

Mas que una guía es un recordatorio de que cosas instalar, algunos archivos de configuración que conviene tenerlos en un repo mio por la dudosa estabilidad de la procedencia y una ayuda de memoria de donde se encuentran mis configuraciones y software para instalar mi devPc a mi gusto y de forma rápida y practica

## Software necesario

1. [Google chrome](https://www.google.com.mx/intl/es-419/chrome/?brand=CHBD&gclid=Cj0KCQjw3qzzBRDnARIsAECmryqQ7s8n6O1T4Sk7xO3EsdhEymfydLbIpk33SQ-heFggNLyB1YjWPqkaApLmEALw_wcB&gclsrc=aw.ds)
2. [git](https://git-scm.com/download/linux)
3. [VsCode](https://code.visualstudio.com/docs/setup/linux)
4. [Inicializar VsCode](###-Inicializar-VsCode)
5. [Terimator](###-Instalar-y-configurar-Terminator)
6. [Agregar git status al prompt](###-Agregar-git-status-al-prompt)

### Instalar git y configurar credenciales

Instalar git

[git](https://git-scm.com/download/linux)

Para almacenar nuestras credenciales en git ejecutar:

```bash
git config --global credential.helper store # Si queremos que las
# credenciales queden en el disco y no las vuelva a solicitar
# >>> ó <<<
git config --global credential.helper 'cache --timeout=<segundos>'
# Si no queremos almacenar las credenciales en el disco y queremos que
# las recuerde por la cantidad de <segundos> indicados, esta opción esta buena
# para ponerle unas cuantas horas y que las pida cada tanto o al comenzar el dia.
```

Luego para configurar el nombre de usuario/password y el email, tipear:

```bash
git config --global user.name "your username"
git config --global user.password "your password"
git config --global user.email "yourEmail@yourDomain"
```

### Inicializar VsCode

#### Instalar extensiones

1. Luego de instalar VsCode, abrir el entorno e ir al menu  `vew => extensiones` , luego buscar la extension  `Settings Sync` e instalarla.
2. Sincronizar configuraciones de VsCode.

Si luego de instalada la extension de `settings sync` no se abrio la pantalla inicial de la misma, presionar:
**presionar**
`ctr+shift+d`
**ó**
`ctl+shift+p`
y luego seleccionar la opción
**sync: Download Settings**

se debería abrir la pagina de la extension, en el caso de querer:

- **administrar de la configuración de vscode:** hacer click en login con github y luego de hecho el login con la cuenta de sincronización, en mi caso `ibarretorey`, volver a vscode y ahi deberían aparecer los gists de esa cuenta donde uno de ellos es la configuración, en mi caso el gist se llama:
`Visual Studio Code Settings Sync Gist` y el id es `dabbdddb1340119ae3181cb3ec90abd4`
- **descargar la configuracion:**  hacer click en Download Public Gist y luego ingresar el id del Gist, en nuestro caso `dabbdddb1340119ae3181cb3ec90abd4`

Finalizada la instalación de las extensiones, reiniciar vscode y ya estamos en condiciones de configurar las fuentes.

#### Configurar las fuentes

1. Instalar fuentes en vscode: entrar a la carpeta [VsCodeFont](./VsCodeFont/) en `./VsCodeFont/FiraCodeiScript` y luego ejecutar

```bash
sudo cp  -r ./FiraCodeiScript /usr/share/fonts # Para copiar las fuentes en el equipo
sudo fc-cache -f -v # para instalar las fuentes, puede tomar unos minutos
```

**Seleccionar la fuente:**
En visual studio code presionar `crtl+shift+p` y seleccionar `=>` Preferences: Color Theme `=>` Dark++ Italic, reinciar vscode y qeudo listo.

### Instalar y configurar terminator


#### Instalación

Para instalar terminator seguir el siguiente paso a paso

1. Actualizar la lista source apt

```bash
sudo apt-get update
```

2. Instalar Terminator

```bash
sudo apt-get install terminator
```

#### Configuración

Para configurar terminator pararse dentro de la carpeta [Terminator](./Terminator) `./Terminator` y ejecutar

```bash
mkdir ~/.config/terminator
cp -r ./* ~/.config/terminator/
```

### Agregar git status al prompt

#### Instalación

Copiar la carpeta bash-git-prompt al directorio local en `home`

```sh
sudo cp -r ./bash-git-prompt ~/bash-git-prompt
```

Agregar el siguiente script a `~/.bashrc` para que si nos encontramos dentro de un directorio con git nos agregue el status al prompt:

```bash
if [ -f "$HOME/.bash-git-prompt/gitprompt.sh" ]; then
    GIT_PROMPT_ONLY_IN_REPO=1
    source $HOME/.bash-git-prompt/gitprompt.sh
fi
```


#### Ejemplos

El prompt se vera como se detalla a continuacion:

![Example prompt](./bash-git-prompt/gitprompt.png)

* ``(master↑3|✚1)``: on branch ``master``, ahead of remote by 3 commits, 1 file changed but not staged
* ``(status|●2)``: on branch ``status``, 2 files staged
* ``(master|✚7…)``: on branch ``master``, 7 files changed, some files untracked
* ``(master|✖2✚3)``: on branch ``master``, 2 conflicts, 3 files changed
* ``(master|⚑2)``: on branch ``master``, 2 stash entries
* ``(experimental↓2↑3|✔)``: on branch ``experimental``; your branch has diverged by 3 commits, remote by 2 commits; the repository is otherwise clean
* ``(:70c2952|✔)``: not on any branch; parent commit has hash ``70c2952``; the repository is otherwise clean

Los simbolos son los siguientes:

- Local Status Symbols
  - ``✔``: repository clean
  - ``●n``: there are ``n`` staged files
  - ``✖n``: there are ``n`` files with merge conflicts
  - ``✖-n``: there are ``n`` staged files waiting for removal
  - ``✚n``: there are ``n`` changed but *unstaged* files
  - ``…n``: there are ``n`` untracked files
  - ``⚑n``: there are ``n`` stash entries
- Upstream branch
  - Shows the remote tracking branch
  - Disabled by default
  - Enable by setting GIT_PROMPT_SHOW_UPSTREAM=1
- Branch Tracking Symbols
  - ``↑n``: ahead of remote by ``n`` commits
  - ``↓n``: behind remote by ``n`` commits
  - ``↓m↑n``: branches diverged, other by ``m`` commits, yours by ``n`` commits
  - ``L``: local branch, not remotely tracked
- Branch Symbol:<br />
  	When the branch name starts with a colon ``:``, it means it's actually a hash, not a branch (although it should be pretty clear, unless you name your branches like hashes :-)
