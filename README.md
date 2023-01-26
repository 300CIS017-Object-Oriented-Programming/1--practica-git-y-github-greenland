# Proyecto de fundamentos de Github

Archivo de práctica, en este proyecto se practicarán conceptos relacionados con: 

* Manipular los archivos de un repositorio local mediante los comandos básicos: add, commit, status, log
* Entender qué es un repositorio remoto.
* Clonar un repositorio remoto.
* Manipular los archivos de un repositorio local y sincronizar los cambios en el repositorio remoto mediante los comandos básicos: push y pull.
* Comprender cuándo se genera un conflicto y cómo solucionarlo.


## Familiarizacion con repositorios remotos  y locales
*	Clone el repositorio. Llamaremos en adelante a este repositorio repositorio(1)
* Observe la carpeta oculta .git creada dentro del disco duro
*	Cree un archivo de texto en markdown(.md) dentro del repositorio este archivo debe tener su nombre
*	Agregue el archivo al repositorio local
*	Modifique el archivo con un nuevo texto
*	Agregue el archivo al stagging area  ``git add ruta del archivo``
*	Haga commit al archivo. Recuerde poner un comentario en el archivo.   ``git commit -m "su mensaje" ``
*	Haga status al repositorio
*	Cree un segundo archivo 
*	Agregue el archivo al stagging área 
*	Haga commit al archivo,  no poner el comentario para ver el error que arroja. Corregir el error agregando un mensaje
*	Haga push al repositorio remoto, para subir los cambios hechos al repositorio

## Conflictos
### Modificar el archivo
* Clone el repositorio remoto en un **directorio diferente** al que usó en la parte de familiarización
* En el segundo repositorio modifique la primera línea del primer archivo .md que creo previamente
* Guarde el archivo
* Agregue el archivo al stagging area:  ``git add ruta del archivo``
* Haga commit del archivo en el repositorio local: ``git commit -m "su mensaje" ``
* Haga push al repositorio remoto: ``git push origin main``
### Crear conflicto en el mismo archivo
* Vuelva a la carpeta del primer repositorio que clonó
* Abra el archivo que editó en el paso anterior
* Modifique la primera línea con algo diferente ( Note que en esta copia del repositorio todavía no se ven reflejados los cambios que hizo en el repositorio(1))
* Guarde el archivo
* Agregue el archivo al stagging area:  ``git add ruta del archivo``
* Haga commit del archivo en el repositorio local: ``git commit -m "su mensaje" ``
* Intente hacer push al repositorio remoto: ``git push origin main``. Debe aparecerle un error similar a este ``! [rejected] master -> master (fetch first)``. Esto significa que Git rechazó el push al repositorio remoto porque el mismo archivo fue modificado desde repositorios diferentes. La última versión del repositorio remoto no coincide con la versión del repositorio local que esta intentado hacer el push
### Resolver conflictos
* Existen dos tipos de conflictos. 
  * Conflictos que pueden ser resueltos automáticamente por git. Esos son conflictos que no modifican las mismas partes de un archivo o que modifican archivos   
 diferentes.  En ese caso solo deberá escribir ``git pull origin``. El comando descargará los nuevos archivos y hará un merge automáticamente con sus archivos locales.
  * Conflictos que NO puede ser resueltos automáticamente por GIT. Estos confictos ocurren cuando se han modificado las mismas líneas de un archivo en dos repositorios diferentes y por lo tanto la copia remota y la copia local no coinciden.  Para solucionar este caso es necesario: 
    * Hacer pull al repositorio
    * Abrir con el editor preferido los archivos que tienen conflicto y editarlos manualmente. Las líneas de código que están después de la etiqueta HEAD corresponden a lo que está en el repositorio local y lo que está después de ===== corresponde a lo que está en el repositorio remoto. Quien corrije el error decide cuál de las dos versiones permanece en el archivo. En todo caso recuerde eliminar las etiquetas <<<<<<< HEAD, ======= y >>>>>>>. Una vez terminado el ajuste:
       * Agregué el archivo al repositorio remoto  ``git add ruta``
       * Haga commit del archivo ``git commit -m "su mensaje" ``
       * Haga push al repositorio remoto ``git push origin main``

