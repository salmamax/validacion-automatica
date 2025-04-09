# Limpieza del Historial de Commits con `git rebase -i`

## Error Simulado:
Creamos varios commits en la rama `main` con mensajes poco claros: "Arreglos", "Cambios" y "Actualización de cosas". El objetivo era simular un historial de commits desordenado que necesitaba ser limpiado.

## Comandos Usados:
1. `git rebase -i HEAD~3`: Este comando se usó para iniciar una sesión de rebase interactiva que nos permitió modificar los últimos tres commits.
2. `git push --force origin main`: Este comando se usó al final para forzar la actualización del historial en el repositorio remoto de GitHub con el historial reescrito localmente.

## Pasos Detallados del Rebase Interactivo:
1. **Ejecutamos `git rebase -i HEAD~3`**. Esto abrió un editor de texto con una lista de los últimos tres commits.
2. **Cambiamos `pick` por `reword` (o `r`) en las tres líneas.** Esto nos permitió cambiar el mensaje de cada uno de los tres commits.
3. **Guardamos y cerramos el editor.**
4. **Se abrió un nuevo editor para el primer commit ("Arreglos").** Escribimos un mensaje más claro: "Añadido comentario explicativo al script mi_script.sh". Guardamos y cerramos.
5. **Se abrió un nuevo editor para el segundo commit ("Cambios").** Escribimos un mensaje más claro: "Añadida línea a la descripción del README.md sobre el propósito del repositorio.". Guardamos y cerramos.
6. **Se abrió un nuevo editor para el tercer commit ("Actualización de cosas").** Escribimos un mensaje más claro: "Añadido otro comentario al script mi_script.sh.". Guardamos y cerramos.
7. **Ejecutamos `git rebase -i HEAD~3` nuevamente.** Esta vez, el editor mostró los tres commits con los mensajes claros que acabábamos de escribir.
8. **Dejamos la primera línea como `pick` y cambiamos las siguientes dos a `squash` (o `s`)**. Esto indicó a Git que queríamos fusionar los últimos dos commits con el primero.
9. **Guardamos y cerramos el editor.**
10. **Se abrió un último editor con los mensajes de los tres commits.** Editamos el mensaje para que fuera conciso y representara todos los cambios combinados: "Refactor: Realizadas mejoras menores en el script y actualizada la descripción en README". Guardamos y cerramos el editor.

## Aprendizaje de la Experiencia:
Aprendimos que `git rebase -i` es una herramienta poderosa para limpiar y organizar el historial de commits. Nos permitió cambiar los mensajes de commits individuales para que fueran más descriptivos y también fusionar varios commits en uno solo, lo que puede hacer que el historial sea más fácil de seguir.

Es importante recordar que el uso de `git push --force` debe hacerse con precaución, especialmente en repositorios compartidos, ya que puede reescribir el historial remoto y causar problemas a otros colaboradores. En este caso, como era un repositorio de pruebas, pudimos usarlo para actualizar el historial en GitHub.
