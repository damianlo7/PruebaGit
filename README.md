# PruebaGit
## Creamos el directorio y a continuación vamos a el.
```bash
mkdir prueba_git
```
```bash
cd prueba_git/
```

## Dentro de el crearemos los siguintes archivos:
```bash
nano texto.txt
```
```bash
nano script.sh
```
## Accedemos a texto.txt
```bash
nano texto.txt
```
## Una vez dentro de el introducimos el texto
```txt
uno
dos
tres
```
## A continuacion accederemos a "script.sh" 
```bash
nano script.sh
```
## Y añadiremos el siguiente texto :
```
echo Listado completo
ls -l
```
## Debemos añadir permisos y luego lo ejecutaremos:
```bash
chmod a+x script.sh
```
```bash
./script.sh
```
# 1. INICIALIZACION

## Desde el directorio "/prueba_git" ejecutaremos esto:
```bash
git init
```
## el resultado esperado sera este:
```txt
Initialized empty Git repository in C:/Users/dloppin/prueba_git/.git/
```

## Para ver el historico del repositorio debemos usar:
```bash
git status
```
## Nos devolvera lo siguiente:
```txt
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        script.sh
        texto.txt

nothing added to commit but untracked files present (use "git add" to track)
```
## Esto indica que los archivos todavia no estan gestionados por git, tambien vemos que la rama principal se llama "master", la cambiaremos a "main" de la siguiente forma:

```bash
git branch -m main
```

## Si queremos restaurarlo ejecutaremos:
```bash
git branch -m master
```


# 2. AÑADIR ARCHIVOS (add y commit)

## Añadimos los archivos a rastreado de la siguiente forma: 
```bash
git add script.sh
```

## Lo siguiente es hacer un estatus en el que el resultado deberia ser el siguiente
```bash

$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   script.sh

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        texto.txt
```


## Ahora debemos hacer un "Comit" para sincronizar el archivo
```bash
$ git commit -m "Confirmacion inicial"
[master (root-commit) deb00bc] Confirmacion inicial
 1 file changed, 2 insertions(+)
 create mode 100644 script.sh
```

## Debemos hacer un status en el que veremos que esta todo guardado como version menos "texto.txt" que no esta en seguimiento

```bash
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        texto.txt

nothing added to commit but untracked files present (use "git add" to track)
```


## Le añadiremos texto a nuestro txt y lo guardaremos de la siguiente forma: 
```bash
$ git add texto.txt
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it

$ git commit -m "Añdadido archivo texto.txt"
[master d05b774] Añdadido archivo texto.txt
 1 file changed, 3 insertions(+)
 create mode 100644 texto.txt

$ git status
On branch master
nothing to commit, working tree clean
```
### Con el ultimo status podemos ver que esta todo confirmado.


# 3. Modificar Archivos

### Para ello editaremos nuestro txt, para ello deberemos ejecutar el siguiente comando:

```bash
$ nano texto.txt
```
### Dentro de el añadiremos texto

## A continuacion ejecutaremos un status para ver como ahora se muestra como "modificado"

```bash
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

no changes added to commit (use "git add" and/or "git commit -a")
```


## Añadimos y preparamos el archivo para el siguiente commit
```bash
$ git add texto.txt
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it

$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   texto.txt
```

## Añadiremos otra linea y veremos su estatus antes de hacer un commit

```bash
$ nano texto.txt
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   texto.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt
```

## Para añadir estos cambios haremos un nuevo add y luego el respectivo commit
```bash
$ git add texto.txt
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it

$ git commit -m "Ampliada la explicacion del texto"
[master cb411b7] Ampliada la explicacion del texto
 1 file changed, 2 insertions(+)

$ git status
On branch master
nothing to commit, working tree clean
```
# 4. Información (git show y git log)

##  Resumir en un paso add y commit
```bash
$ git commit -a -m "Nueva version"
On branch master
nothing to commit, working tree clean
```
## Obtener la informacion de la ultima version:
```bash
$ git show
commit cb411b7d7cbcf70b224a5857e85eb19c573e65ad (HEAD -> master)
Author: Hornet <hornet@pharloom.com>
Date:   Mon Sep 29 09:43:07 2025 +0200

    Ampliada la explicacion del texto

diff --git a/texto.txt b/texto.txt
index 15bf608..818aba5 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,3 +1,5 @@
 uno
 dos
 tres
+cuadro
+cinco

```
## Por otro lado tenemos el log para ver los cambios/historico

```bash
$ git log
commit cb411b7d7cbcf70b224a5857e85eb19c573e65ad (HEAD -> master)
Author: Hornet <hornet@pharloom.com>
Date:   Mon Sep 29 09:43:07 2025 +0200

    Ampliada la explicacion del texto

commit d05b774ae302713f98874acc0b0c15e07bd5aa83
Author: Hornet <hornet@pharloom.com>
Date:   Mon Sep 29 09:33:49 2025 +0200

    Añdadido archivo texto.txt

commit deb00bcad78b52ecc7fb587c477fbdeeb16c7def
Author: Hornet <hornet@pharloom.com>
Date:   Fri Sep 26 13:54:02 2025 +0200

    Confirmacion inicial
```
# 5. Diferencias (git diff)

## Añadiremos una nueva linea y borraremos otra para ver el resultado. 
```bash
$ nano texto.txt
$ git diff
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
diff --git a/texto.txt b/texto.txt
index 818aba5..c478791 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,5 +1,5 @@
 uno
 dos
-tres
 cuadro
 cinco
+seis
```

## Ahora haremos otro commit, añadimos una nueva linea y lovolveremos a ejecutar 
```bash
$ git commit -a -m "Probando diff"
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
[master bcd6acc] Probando diff
 1 file changed, 1 insertion(+), 1 deletion(-)
```

```bash
$ git diff
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
diff --git a/texto.txt b/texto.txt
index c478791..4d426ee 100644
--- a/texto.txt
+++ b/texto.txt
@@ -3,3 +3,4 @@ dos
 cuadro
 cinco
 seis
+siete
```
# 6. Ignorar archivos(.gitignore)

## Creamos los siguientes archivos
```bash
$ nano .gitignore
# ignora los archivos terminados en .class
*.class
# ignora los archivos terminados en ~
*~
# pero no importante~, aun cuando había ignorado los archivos
terminados en ~ en la linea anterior
!importante~

```
```bash
$ nano hola.java
class Hola {
public static void main(String[] args){
System.out.println("Welcome to the Java World");
}
}
```
```bash
$ nano temporal~
```
```bash
$ nano importane~
```
## Comprobamos que esten creadoslos archivos y el status
```bash
$ ls -a
./   .git/       hola.java    script.sh  texto.txt
../  .gitignore  importante~  temporal~
```
```bash

$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
        hola.java

no changes added to commit (use "git add" and/or "git commit -a")

```

## Ahora añadiremos todo lo que esta pendiente y sus subdirectorio
```bash
$ git add .
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
warning: in the working copy of '.gitignore', LF will be replaced by CRLF the ne
xt time Git touches it
warning: in the working copy of 'hola.java', LF will be replaced by CRLF the nex
t time Git touches it
```
```bash
$ git commit -m "Añadimos fuentes en java y archivos importantes"
[master 48b0128] Añadimos fuentes en java y archivos importantes
 3 files changed, 12 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 hola.java
```
## Vemos los archivos que hay en el directorio ejecutando lo siguiente 
```bash
$ git ls-tree --name-only -r HEAD
.gitignore
hola.java
script.sh
texto.txt
```
# 7 Tags y gestion de versiones (git tag y git checkout)

## Ejecutaremos un git log para obtener el identificador

```bash
$ git log
commit 48b012839a357f637cc5d0aec641d6e4a074eaeb (HEAD -> master)
Author: Hornet <hornet@pharloom.com>
Date:   Wed Oct 1 10:55:54 2025 +0200

    Añadimos fuentes en java y archivos importantes

commit bcd6acc63051919bda34cbcb2c0373e175397106
Author: Hornet <hornet@pharloom.com>
Date:   Mon Sep 29 12:45:56 2025 +0200

    Probando diff

commit cb411b7d7cbcf70b224a5857e85eb19c573e65ad
Author: Hornet <hornet@pharloom.com>
Date:   Mon Sep 29 09:43:07 2025 +0200

    Ampliada la explicacion del texto

commit d05b774ae302713f98874acc0b0c15e07bd5aa83
Author: Hornet <hornet@pharloom.com>
Date:   Mon Sep 29 09:33:49 2025 +0200

    Añdadido archivo texto.txt

commit deb00bcad78b52ecc7fb587c477fbdeeb16c7def
Author: Hornet <hornet@pharloom.com>
Date:   Fri Sep 26 13:54:02 2025 +0200
```

## Con el identificador haremos un git shou
```bash
$ git show 48b0
commit 48b012839a357f637cc5d0aec641d6e4a074eaeb (HEAD -> master)
Author: Hornet <hornet@pharloom.com>
Date:   Wed Oct 1 10:55:54 2025 +0200

    Añadimos fuentes en java y archivos importantes

diff --git a/.gitignore b/.gitignore
new file mode 100644
index 0000000..f3af98f
--- /dev/null
+++ b/.gitignore
@@ -0,0 +1,6 @@
+#ignora los archivos terminados en .class
+*.class
+#ignora los archivos termiandos en ~
+*~
+#pero no importante~, aun cuando había ignorado los archivos termiandos en ~ en
 la linea anterior !importante~
+
diff --git a/hola.java b/hola.java
new file mode 100644
index 0000000..6198593
--- /dev/null
```

## Añadimos un tag a la version actual 

```bash
$ git tag v0.7
```
## Añadimos un tag a una version posterior

```bash
$ git tag v0.3 d05b774ae302713f98874acc0b0c15e07bd5aa83
```

## Para escribir el log ejecutaremos lo siguiente: 

```bash
$ git log --oneline
48b0128 (HEAD -> master, tag: v0.7) Añadimos fuentes en java y archivos importan
tes
bcd6acc Probando diff
cb411b7 Ampliada la explicacion del texto
d05b774 (tag: v0.3) Añdadido archivo texto.txt
deb00bc Confirmacion inicial
```
## Tambien podemos ver una version determinada de esta forma: 
```bash
$ git show v0.3
commit d05b774ae302713f98874acc0b0c15e07bd5aa83 (tag: v0.3)
Author: Hornet <hornet@pharloom.com>
Date:   Mon Sep 29 09:33:49 2025 +0200

    Añdadido archivo texto.txt

diff --git a/texto.txt b/texto.txt
new file mode 100644
index 0000000..15bf608
--- /dev/null
+++ b/texto.txt
@@ -0,0 +1,3 @@
+uno
+dos
+tres
```
## Para ir a una version mas antigua debemos ejecutar lo siguiente:

```bash
$ git checkout v0.3
Note: switching to 'v0.3'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at d05b774 Añdadido archivo texto.txt
```

## Volvemos a la version actual
```bash
$ git checkout master
Previous HEAD position was d05b774 Añdadido archivo texto.txt
Switched to branch 'master'

PUNTO 8 RAMAS
$git branch Prueba
$ git log --oneline
48b0128 (HEAD -> master, tag: v0.7, Prueba) Añadimos fuentes en java y archivos
importantes
bcd6acc Probando diff
cb411b7 Ampliada la explicacion del texto
d05b774 (tag: v0.3) Añdadido archivo texto.txt
deb00bc Confirmacion inicial
```

# 8. Ramas

## Creamos una rama

```bash
$ git branch Prueba
$ git log --oneline
48b0128 (HEAD -> master, tag: v0.7, Prueba) Añadimos fuentes en java y archivos
importantes
bcd6acc Probando diff
cb411b7 Ampliada la explicacion del texto
d05b774 (tag: v0.3) Añdadido archivo texto.txt
deb00bc Confirmacion inicial
```

## Ahora veremos el listado de ramas 
```bash
$ git branch
  Prueba
* master
```
## Cambiamos de rama
```bash
$ git switch Prueba
Switched to branch 'Prueba'
```
## Volvemos a listar
```bash
$ git branch
* Prueba
  master
```
### Podemos observar que el asterisco cambio de sitio, este marca la rama en la que te encuentras

## Miraremos el log
```bash
$ git log --oneline
48b0128 (HEAD -> Prueba, tag: v0.7, master) Añadimos fuentes en java y archivos
importantes
bcd6acc Probando diff
cb411b7 Ampliada la explicacion del texto
d05b774 (tag: v0.3) Añdadido archivo texto.txt
deb00bc Confirmacion inicial
```

## Haremos el commit de la nueva rama
```bash
$ git commit -a -m "Rama para pruebas de código"
On branch Prueba
nothing to commit, working tree clean

$ git log --oneline
48b0128 (HEAD -> Prueba, tag: v0.7, master) Añadimos fuentes en java y archivos
importantes
bcd6acc Probando diff
cb411b7 Ampliada la explicacion del texto
d05b774 (tag: v0.3) Añdadido archivo texto.txt
deb00bc Confirmacion inicial
```

## Modificamos el archivo hola.javay hacemos de nuevo un commit
```bash
$ nano hola.java

$ git commit -a -m "Llegan los Ents a Java"
[Prueba 62f330c] Llegan los Ents a Java
 1 file changed, 2 insertions(+), 1 deletion(-)

$ git tag v0.7-Ent-Realease

$ git log --oneline
62f330c (HEAD -> Prueba, tag: v0.7-Ent-Realease) Llegan los Ents a Java
48b0128 (tag: v0.7, master) Añadimos fuentes en java y archivos importantes
bcd6acc Probando diff
cb411b7 Ampliada la explicacion del texto
d05b774 (tag: v0.3) Añdadido archivo texto.txt
deb00bc Confirmacion inicial

```
## Volvemos a la rama principal y vemos que el archivo no cambio (porque lo editamos  en otra rama)
```bash
$ git switch master
Switched to branch 'master'

$ cat hola.java
class Hola {
        public static void main(String[] args){
        System.out.println("Welcome to the Java World");
        }
}

```
## Si nos convence juntamos las ramas
```bash
$ git merge Prueba
Updating 48b0128..62f330c
Fast-forward
 hola.java | 3 ++-
 1 file changed, 2 insertions(+), 1 deletion(-)
```

# 9. Eliminar y quitar de seguimiento


## Eliminamos un archivo
```bash
$ git rm -f importante~
rm 'importante~'
```

## Eliminamos los archivos que estan en seguimiento
```bash
$ git reset HEAD *.class
```
# 10. Repositorios remotos: GitHub

## Clonamos un proyecto ejecutando 
```bash
$ git clone https://github.com/ColegioVivasCurro/HolaED
Cloning into 'HolaED'...
remote: Enumerating objects: 20, done.
remote: Total 20 (delta 0), reused 0 (delta 0), pack-reused 20 (from 1)
Receiving objects: 100% (20/20), 4.26 KiB | 544.00 KiB/s, done.
Resolving deltas: 100% (8/8), done.
```

## Enlazar repositorio con directorio actual 
```bash
$ git clone https://github.com/damianlo7/PruebaGit
Cloning into 'PruebaGit'...
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (4/4), done.

```

## Mandar cambios al repositorio remoto
```bash
dloppin@DESKTOP-F6UG93B MINGW64 ~/prueba_git/PruebaGit (main)
$ git push -u origin main
info: please complete authentication in your browser...
branch 'main' set up to track 'origin/main'.
Everything up-to-date
```




