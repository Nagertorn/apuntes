# Procedimiento y comandos básicos de Git
Se asume que estamos trabajando en una carpeta exclusiva para el repositorio, es decir la carpeta solo contiene archivos de repositorio.

## 0: Cosas que tener antes
1. El repositorio al que quieres subir los archivos. Al crear un repositorio te dan una URL que necesitaremos copiar para trabajar con el. En este caso la URL de mi repositorio es:
	https://github.com/MatiasAGomezJ/apuntes.git
	
2. La carpeta en la que vas a trabajar
	P.ej:
	```a
	~/Documentos/Repositorios/Proyecto_PyDevops
	```

##  1: Proceso de creacion y subida de archivos a un repositorio

Sin el siguiente comando no se pueden hacer control de versiones, por lo tanto es lo primero que deberemos hacer a la hora de trabajar con git.
``` a 
$ git init
```
 Esto creara una carpeta oculta con archivos de configuración.
 
Crearemos el primer documento, en este caso lo llamaré `documento1`.

El comando `$ git status` muestra el estado de los archivos con respecto al repositorio, como lo acabamos de crear nos dirá que esta **untracked**.
```a
$ git status

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        documento1
```
Para añadirlo utilizaremos:
- Para añadir todos los archivos
```a
$ git add . 
```
- Para añadir solo un archivo
```a
$ git add nombre_del_archivo
```
Ahora el archivo esta en estado **Stage**.
```a
$ git status

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   documento1
```
El siguiente paso es commitear
```a
$ git commit -m "Esto es un comentario"
```

Al hacer un commit estamos poniendo en una cola de espera a los archivos en los que hayamos usado el `$ git add`. El siguiente paso es hacer el `$ git push` pero todavia no hemos especificado a que repositorio vamos a subir los archivos.
> Nota: el parametro `-m` sirve para añadir un comentario, si lo omitimos nos saldra el editor de texto **VIM** para añadir el comentario
> ***IMPORTANTE***. Al hacer un commit sera totalmente necesario hacer un comentario, si no, no dejará subirlo.

Para añadir nuestro repositorio vacio utilizaremos:
```a
$ git remote add origin *URL*
```
Si hacemos  lo siguiente mostrará dos links, uno de `(fetch)` y otro de `(push)`, significa que todo esta bien.
```a
$ git remote -v
origin https://github.com:MatiasAGomezJ/my-obsidian-vault.git (fetch)
origin https://github.com:MatiasAGomezJ/my-obsidian-vault.git (push)
```
Siguiendo con el proceso de antes, haremos un `$ git push` esto subira, por fin, los archivos de tu dispositivo al repositorio.
```a
$ git push -u origin master
```
Sera necesario, *creo*, especificar la rama a la que subiremos los archivos, en este caso es la rama `master`, que se crea automaticamente cada vez que creemos un repositorio.
> Nota: Ni idea para que sirve el `-u origin`.
> Nota 2: Solo hace falta utilizar este comando 1 vez, despues se puede utilizar `$ git push` y ya asumirá la rama en la que subira los archivos.
> Fin de la nota.

Hecho esto ya se estarán subidos los archivos en GitHub.

##  2. Proceso de clonacion y descarga de un repositorio
**ESTAMOS EN OTRA MAQUINA** o otra carpeta.

El primer paso para clonar un repositorio es ir a la pagina de este y copiar su *URL*. Teniendo esto podemos utilizar el siguiente comandillo.
```a
$ git clone https://github.com/MatiasAGomezJ/apuntes.git
```
Hecho esto estará descargada la ultima version del repositorio.
>***IMPORTANTE***. Al hacer una clonacion no estas descargando los archivos en una carpeta estas **descargando el repositorio como carpeta**

P.ej:
Mi repositorio de `apuntes`, tiene el archivo `"Procedimiento y comandos básicos de Git"`.
Si hago una clonacion en la carpeta `Proyecto_PyDevops`:
```a
~/Documentos/Repositorios/Proyecto_PyDevops$ ls
archivo1
~/Documentos/Repositorios/Proyecto_PyDevops$ git clone https://github.com/MatiasAGomezJ/hello-world-dual.git
Cloning into 'hello-world-dual'...
.
.
```
Sucederá esto:
```a
~/Documentos/Repositorios/Proyecto_PyDevops$ ls
archivo1 apuntes/
```
**No esto**:
```a
~/Documentos/Repositorios/Proyecto_PyDevops$ ls
archivo1 .git documento1
```