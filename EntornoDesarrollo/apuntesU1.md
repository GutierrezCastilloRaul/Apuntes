##  **APUNTES TEMA 1: GIT configuraciones y primeros pasos**  ##

### 1. git y github: introducción avanzada ###

Git es una herramienta que te ayuda a guardar distintas versiones de tus documentos y codigos/programas. Este funciona con otros dispositivos y puede guardar y seguir la pista de otros cambios y deshacerlos.

Github es un sistema de repositorios remotos que puden subirse a la nube. Este está basado en git y comparte lo que deseas con repositorios remotos.

Git tiene su propia terminal y por lo tanto lenguaje y comandos necesarios para gestionarlo bien.

### 1.1 Conceptos claves de git: ###

- **repositorio**: una carpeta la cual git guarda tu progreso
- **Clone**: Crea una copia de un repositorio en una carpeta de tu ordenador
- **Stage**: Le dice a git que cambios son los que planeas subir/cambiar. Puedes hacer cambios y no subirlos
- **commit**: Guarda una version de todos los cambios planeados
- **branch**: Separa un comit (unos cambios planteados) para trabajar por separado en otros.
 
    * ***Ej branch***: Tenemos el archivo 1, 2 y 3, hemos echo cambios en 1 y 2 y los hemos subido con un commit y ahora queremos trabajar en el archivo 3, creando una branch, podemos volver al momento antes de hacer tanto los cambios a los arch. 1 y 2 y así editar el 3. Al momento de pushear, se crean dos caminos distintos.
  
- **merge**: Une dos branchs de commits

    * ***Ej merge***: Antes trabajamos en dos ramas separadas, en 1 editamos arch. 1 y 2 y en la otra solo el 3. ahora podemos unificar todos los cambios en un solo camino con el comando " git merge". Más adelante aprenderemos la sintaxis correcta.

- **push**: Sube a la nube (*GitHub*) Nuestros commits
- **Pull**: Trae a tu ordenador el commit más reciente

|||  **IMPORTANTE: NO VAMOS A INCLUIR COMANDOS DE "BASH", ESOS ESTÁN EN SIST. INFORMÁTICOS** |||

### 1.2 Primeros comandos y configuraciones de git ###

Vamos a empezar dejandole saber a git quienes somos, para saber quien está publicando los cambios.

Podemos usar los siguientes comandos para configurar git:

* configurar nuestro nombre:
 
        git configg --global user.name "Nombre" 

* Configurar nuestro correo:

        git config --globar user.email "Miemail@ejemplo.com"

    ***(Usamos "--local" para solo un repositorio mientras que "--global" para todos.)***

* Ver nuestra configuración: 

        git config --list

### 1.3 Nos manchamos las manos ###

En este apartado, cada concepto clave anterior tiene mínimo un comando y añade otros. Empecemos por los mas sencillos:

```bash
 mkdir "carpeta" # -> crea una carpeta.

 cd carpeta # -> nos mueve dentro de "carpeta".

 cd .. # -> Nos lleva un paso atrás en la ruta absoluta de nuestra zona de trabajo. Acepta tanto rutas absolutas como relativas. Con "/" empezamos en el 0 absoluto

 cd /home/usuarioT/Documentos... # -> Ej. de ruta absoluta

 cd GitHub/Ejercicios... # -> Ej. de ruta relativa

 git init # -> inicia git en la "zona de trabajo"  en la que nos situemos.

touch "archivo.txt" # -> crea un archivo con el nombre que introduzcas en la ubicación q nos encontremos.

ls # -> Nos muestra una lista simple con los archivos de nuestra ubicacion. Acepta multitud de opciones como:

    ls -a # -> (all) muestra los comandos ocultos
    ls -l # -> formato largo de los archivos (muestra los permisos)
    ls -R # -> (recursive) muestra lo que hay en una carpeta y lo que hay DENTRO de otras carpetas
    ls -t # -> (time) ordenados x fecha

    ¡¡¡ TODAS ESTAS SE PUEDEN COMBINAR !!!

git "opciones" # -> le dice a la terminal bash que vamos a trabajar con git (iniciado en el comando "git init") Opciones git:

git add # -> añade 

    git add "archivo.txt" # -> Le deja saber a git que quieres añadir ese archivo a un commit

    git add -A | --all | # -> muestra todos los archivos cambiados/eliminados de los que git tiene conocimiento.

    git status # -> ver que cambios estan subidos al commit

    git restore --staged "archivo.txt" # -> quita un archivo de la lista de cambios planteados

git status # -> muestra la lista de cambios

```
Ya hemos añadido nuestros primeros cambios a la lista de cambios, ahora vamos a subirlos a un commit con los siguientes comandos: 

```bash
git commit # -> añade los cambios planteados al commit. tambien recibe varias opciones:

    git commit -m "mensaje" # -> deja un mensaje describiendo el commit para tener mas orden. es NECESARIO.

    git commit -a -m "mensaje" # -> añade todos los cambios al commit. equivale a hacer "git add" y añade el mensaje igual que antes. ¡¡ IMPORTANTE !! no añade los archivos nuevos, por eso es necesario hacer "git add -a"


