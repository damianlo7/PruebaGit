# PruebaGit
## Creamos el directorio y acontinuacion vamos a el.
```bash
mkdir prueba_git
```
```bash
cd prueba_git/
```

## Dentro de el crearemos los sigueintes archivos:
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
# INICIALIZACION

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
### Esto indica que los archivos todavia no estan gestionados por git, tambien vemos que la rama principal se llama "master", la cambiaremos a "main" de la siguiente forma:

```bash
git branch -m main
```

### Si queremos restaurarlo ejecutaremos:
```bash
git branch -m master
```




# AÑADIR ARCHIVOS (add y commit)
```bash

```

