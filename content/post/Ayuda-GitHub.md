---
date: 2020-05-19T21:43:05-04:00
description: "Articulo de Julio Villacis"
featured_image: "images/mundoML.jpg"
tags: []
title: "Articulo: Resolver un conflicto de fusion con la linea de comando"
disable_share: false
---

El articulo y la imagen fueron tomados del siguiente link:

https://help.github.com/es/github/collaborating-with-issues-and-pull-requests/resolving-a-merge-conflict-using-the-command-line

#### Foro de ayuda de Github

# Wikipedia


Los conflictos de fusi�n ocurren cuando se hacen cambios contrapuestos en la misma l�nea de un archivo o cuando una persona edita un archivo y otra persona borra el mismo archivo. Para obtener m�s informaci�n, consulta "Acerca de los conflictos de fusi�n".
Conflictos de fusi�n de cambios de l�neas contrapuestos
Para resolver un conflicto de fusi�n causado por cambios de l�neas contrapuestos, debes decidir qu� cambios incorporar desde las diferentes ramas de una confirmaci�n nueva.

Por ejemplo, si usted y otra persona editaron el archivo styleguide.md en las mismas l�neas de diferentes ramas del mismo repositorio de Git, recibir�s un error de conflicto de fusi�n cuando trates de fusionar estas ramas. Debes resolver este conflicto de fusi�n con una confirmaci�n nueva antes de que puedas fusionar estas ramas.

Abre la Git Bash.

Navega en el repositorio de Git local que tiene el conflicto de fusi�n.

cd REPOSITORY-NAME
Genera una lista de los archivos afectados por el conflicto de fusi�n. En este ejemplo, el archivo styleguide.md tiene un conflicto de fusi�n.

Abre tu editor de texto preferido, como Atom, y navega hasta el archivo que tiene los conflictos de fusi�n.

Para ver el origen de un conflicto de fusi�n en tu archivo, busca el archivo para el marcador de conflicto <<<<<<<. Cuando abras el archivo en tu editor de texto, ver�s los cambios desde la rama.
Decide si quieres mantener �nicamente los cambios de tu rama, mantener �nicamente los cambios de las dem�s ramas, o hacer un cambio nuevo, el cual puede incorporar cambios de ambas ramas. Borra los marcadores de conflicto <<<<<<<, =======, >>>>>>> y realiza los cambios que quieras en la fusi�n final.En este ejemplo, ambos cambios se incorporaron en la fusi�n final:
