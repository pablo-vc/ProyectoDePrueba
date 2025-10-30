# 🧠 Práctica de Git — Pablo Vaz

---

## ⚙️ 1. Inicialización (`git init` y `git status`)

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git init
Reinitialized existing Git repository in C:/Users/User/Desktop/2ºDAM/Afondamento
/Git/.git/
```

Comprobar el estado de los archivos del directorio:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        script.bat
        texto.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Cambiar el nombre de la rama principal y lo restaurarlo:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git branch -m main

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (main)
$ git branch -m master

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$
```

---

## 📝 2. Añadiendo archivos (`git add` y `git commit`)

Añadimos **script.bat** a los archivos rastreados y comprobamos que ahora git sí que lo reconoce:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git add script.bat
warning: in the working copy of 'script.bat', LF will be replaced by CRLF the ne
xt time Git touches it
```

Comprobamos el estado:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   script.bat

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        texto.txt
```

Confirmamos la sincronización del archivo:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git commit -m "Confirmacion inicial"
[master (root-commit) 00d9f97] Confirmacion inicial
 1 file changed, 2 insertions(+)
 create mode 100644 script.bat
```

Comprobamos el estado nuevamente:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        texto.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Comprobamos el tipo de objeto codificado,en este caso **blob**(archivo):

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git cat-file 436f -t
blob
```

---

## ✏️ 3. Modificando archivos

Añadimos también el archivo `texto.txt` y confirmamos el cambio:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git add texto.txt
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it

$ git commit -m "Añadido archivo texto.txt"
[master 1ff8051] Añadido archivo texto.txt
 1 file changed, 3 insertions(+)
 create mode 100644 texto.txt
```

Comprobamos que no hay archivos con acciones pendientes:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git status
On branch master
nothing to commit, working tree clean
```

Git reconoce cuando modificamos un archivo:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ nano texto.txt
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Preparamos el archivo `texto.txt` para el siguiente commit
```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git add texto.txt
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
```

Al modificar el archivo git reconoce ambas versiones del archivo, la que habiamos preparado para el commit, y la nueva modificada:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ nano texto.txt

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
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

Preparamos la nueva versión del archivo y confirmamos el cambio:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git add texto.txt
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
$ git commit -m "Ampliada la explicacion del texto"
[master b06e843] Ampliada la explicacion del texto
 1 file changed, 2 insertions(+)
```

Podemos observar que se han aplicado los cambios y ya no hay ninguna version pendiente de añadir:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git status
On branch master
nothing to commit, working tree clean
```

---

## 🔍 4. Información (`git show` y `git log`)

Podemos comprobar los cambios hechos en las versiones mediante `show` o `log`:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git show
commit b06e843f926b6c6f48ddd739d3c424ca9c73dd65 (HEAD -> master)
Author: Pablo <pablo.vaz.111@gmail.com>
Date:   Wed Oct 29 09:47:42 2025 +0100

    Ampliada la explicacion del texto

diff --git a/texto.txt b/texto.txt
index 15bf608..23c83ff 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,3 +1,5 @@
 uno
 dos
 tres
+cuatro
+cinco
```

Historial completo:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git log
commit b06e843f926b6c6f48ddd739d3c424ca9c73dd65 (HEAD -> master)
Author: Pablo <pablo.vaz.111@gmail.com>
Date:   Wed Oct 29 09:47:42 2025 +0100

    Ampliada la explicacion del texto

commit 1ff805162d1e34c63ec501173ed7019da6c4168c
Author: Pablo <pablo.vaz.111@gmail.com>
Date:   Wed Oct 29 09:34:45 2025 +0100

    Añadido archivo texto.txt

commit 00d9f97fe13c7b64092021cab777c64b1aada4b5
Author: Pablo <pablo.vaz.111@gmail.com>
Date:   Wed Oct 29 09:28:26 2025 +0100

    Confirmacion inicial
```

El show nos muestra los cambios en el archivo y el log un historial de versiones

Con el modificador -p en el comando cat-file usado anteriormente se muestra el contenido de un archivo:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git cat-file 436f -p
echo Listado completo
dir -l

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git cat-file 23c8 -p
uno
dos
tres
cuatro
cinco
```

---

## 🧮 5. Diferencias (`git diff`)

Tras modificar el archivo y ejecutar el diff podemos comprobar que nos indica las diferencias respecto a la ultima version sincronizada:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ nano texto.txt

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git diff
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
diff --git a/texto.txt b/texto.txt
index 23c83ff..bf98941 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,5 +1,5 @@
 uno
 dos
-tres
 cuatro
 cinco
+seis
```

Añadiendo el modificador -a en el commit se ahorra la ejecucion del add previo para archivos de los que ya existe una version anterior:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git commit -a -m "Probando diff"
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
[master 6692482] Probando diff
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Despues de realizar varios cambios y comprobar las diferencias con el comando diff he llegado a la conclusion de que muestra la linea nueva o modificada junto con las 3 lineas previas y las 3 posteriores

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ nano texto.txt    #Cambios en el archivo

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git diff  #Comprobacion
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
diff --git a/texto.txt b/texto.txt
index bf98941..430cdae 100644
--- a/texto.txt
+++ b/texto.txt
@@ -3,3 +3,4 @@ dos
 cuatro
 cinco
 seis
+siete

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ nano texto.txt    #Cambios en el archivo

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git diff  #Comprobacion
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
diff --git a/texto.txt b/texto.txt
index bf98941..01ce528 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,4 +1,5 @@
 uno
+aaaa
 dos
 cuatro
 cinco

```

---

## 🚫 6. Ignorar archivos (`.gitignore`)

Creamos todos los archivos indicados:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ nano .gitignore
$ nano Hola.java
$ touch temporal~
$ touch importante~
```

Verificamos su existencia:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ ls -a
./   .git/       Hola.java    script.bat  texto.txt
../  .gitignore  importante~  temporal~
```

Compilamos el archivo Hola.java:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ javac Hola.java
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ dir   #Comprobamos que se ha compilado
Hola.class  Hola.java  importante~  script.bat  temporal~  texto.txt
```

Al hacer un status podemos comprobar que se ignora lo indicado en el archivo `.gitignore`:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
        Hola.java
        importante~

no changes added to commit (use "git add" and/or "git commit -a")
```

Con git add . añadimos todos los archivos pendientes, esto añadiria tambien subdirectorios si los hubiese:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git add .
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
warning: in the working copy of '.gitignore', LF will be replaced by CRLF the ne
xt time Git touches it
warning: in the working copy of 'Hola.java', LF will be replaced by CRLF the nex
t time Git touches it

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git commit -m "Añadidos fuentes en java y archivos importantes"
[master 00e4409] Añadidos fuentes en java y archivos importantes
 4 files changed, 13 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 Hola.java
 create mode 100644 importante~
```

Mostramos los archivos tras el commit de la rama principal:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git ls-tree --name-only -r HEAD
.gitignore
Hola.java
importante~
script.bat
texto.txt
```

---

## 🏷️ 7. Tags y gestión de versiones (`git tag` y `git checkout`)

Se puede añadir un tag a la version actual con git tag "nombre version" o a una anterior añadiendo al final del comando el codigo hash de la version:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git tag v0.7

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git log
commit 00e440960bf3041098638e8dd9153a70b5333663 (HEAD -> master, tag: v0.7)
Author: Pablo <pablo.vaz.111@gmail.com>
Date:   Wed Oct 29 10:32:32 2025 +0100

    Añadidos fuentes en java y archivos importantes
```

Con este cambio es más simple operar con las versiones ya que en vez de ponen el codigo hash basta con poner el nombre de la version

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git tag v0.3 b06e843f926b6c6f48ddd739d3c424ca9c73dd65

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git show v0.3
commit b06e843f926b6c6f48ddd739d3c424ca9c73dd65 (tag: v0.3)
Author: Pablo <pablo.vaz.111@gmail.com>
Date:   Wed Oct 29 09:47:42 2025 +0100

    Ampliada la explicacion del texto

diff --git a/texto.txt b/texto.txt
index 15bf608..23c83ff 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,3 +1,5 @@
 uno
 dos
 tres
+cuatro
+cinco
```

Cambio entre versiones:

```bash
#Cambio a la versión v.03
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
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

HEAD is now at b06e843 Ampliada la explicacion del texto

#Cambio a la última versión
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git ((v0.3))
$ git checkout master
Previous HEAD position was b06e843 Ampliada la explicacion del texto
Switched to branch 'master'
```

---

## 🌿 8. Ramas

Se pueden crear nuevas ramas para realizar pruebas y posteriormente descartarlas o mezclarlas con la rama principal:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git branch Prueba

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git log --oneline
00e4409 (HEAD -> master, tag: v0.7, Prueba) Añadidos fuentes en java y archivos
importantes
6692482 Probando diff
b06e843 (tag: v0.3) Ampliada la explicacion del texto
1ff8051 Añadido archivo texto.txt
00d9f97 Confirmacion inicial
```

Para cambiar a esta nueva rama (se puede hacer tambien con checkout):  

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git switch Prueba
Switched to branch 'Prueba'

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (Prueba)
$ git branch
* Prueba
  master
```

Podemos que ahora head apunta a la rama Prueba:
```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (Prueba)
$ git log --oneline
00e4409 (HEAD -> Prueba, tag: v0.7, master) Añadidos fuentes en java y archivos
importantes
6692482 Probando diff
b06e843 (tag: v0.3) Ampliada la explicacion del texto
1ff8051 Añadido archivo texto.txt
00d9f97 Confirmacion inicial
```



Realizando algun cambio en la nueva rama, en este caso en el archivo "Hola.java"

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (Prueba)
$ nano Hola.java

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (Prueba)
$ git commit -a -m "Llegan los Ents a Java"
[Prueba c9be2c4] Llegan los Ents a Java
 1 file changed, 1 insertion(+)
gt t
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (Prueba)
$ git tag v0.7-Ent-Release
```

Podemos ver que git ahora separa las ramas:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (Prueba)
$ git log --oneline
c9be2c4 (HEAD -> Prueba, tag: v0.7-Ent-Release) Llegan los Ents a Java
00e4409 (tag: v0.7, master) Añadidos fuentes en java y archivos importantes
6692482 Probando diff
b06e843 (tag: v0.3) Ampliada la explicacion del texto
1ff8051 Añadido archivo texto.txt
00d9f97 Confirmacion inicial
```

Cambiando a la rama principal podemos comprobar que el contenido del archivo sigue inmutado en esta rama:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (Prueba)
$ git switch master
Switched to branch 'master'

Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ cat Hola.java
class Hola {
 public static void main(String[] args){
 System.out.println("Welcome to the Java World");
 }
}
```

Si se quieren aplicar los cambios, se puede juntar nuevamente la rama experimental con la original, en este caso no surge ningun problema pero en proyectos mas complejos puede haber conflictos

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git merge Prueba
Updating 00e4409..c9be2c4
Fast-forward
 Hola.java | 1 +
 1 file changed, 1 insertion(+) 
```

---

## 🧹 9. Eliminar y quitar de seguimiento

Eliminamos archivos y confirmamos(rm "nombre archivo"):

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git rm importante~
rm 'importante~'
```
Hay que confirmar el cambio con un commit

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git commit -m "Eliminar importante"
[master f518fda] Eliminar importante
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 importante~
```

Quitar archivos del área de preparación:

Para quitar algun archivo que ya estaba en seguimiento preparado para el siguiente commit se puede ejecutar git reset

```bash
#Comprobamos que el archivo esta preparado para el siguiente commit
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   archivo.prueba

#Ejecutamos el reset
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git reset head archivo.prueba
Unstaged changes after reset:
M       archivo.prueba

#Comprobamos que el archivo ya no se tendrá en cuenta para el próximo commit
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   archivo.prueba

no changes added to commit (use "git add" and/or "git commit -a")
```

---

## ☁️ 10. Repositorios remotos: GitHub

Para clonar un repositorio de github:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git clone https://github.com/pablo-vc/ProyectoPrueba
Cloning into 'ProyectoPrueba'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (3/3), done.
```

Para sincronizar tu repositorio local con un repositorio remoto:

```bash
Pablo@DESKTOP-UFQIAI9 MINGW64 ~/Desktop/2ºDAM/Afondamento/Git (master)
$ git push -u origin master
Enumerating objects: 27, done.
Counting objects: 100% (27/27), done.
Delta compression using up to 4 threads
Compressing objects: 100% (20/20), done.
Writing objects: 100% (27/27), 2.53 KiB | 323.00 KiB/s, done.
Total 27 (delta 6), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (6/6), done.
To https://github.com/pablo-vc/ProyectoDePrueba
 * [new branch]      master -> master
branch 'master' set up to track 'origin/master'.
```

---
