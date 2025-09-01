# Ejemplo Git - Series y Películas

Este práctico introduce los **comandos básicos de Git**, partiendo de un archivo inicial `series.md` con 2 commits ya creados.  

## Objetivos

- Aprender a usar los comandos básicos de Git.
- Entender el flujo de trabajo básico de Git (local y remoto).
- Introducción a ramas.
- Manejo de conflictos.

## Requisitos

- Tener instalado [Git](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Instalaci%C3%B3n-de-Git) en tu máquina.
- Tener una cuenta en [GitHub](https://github.com/).
- Tener instalado VSCode (Este paso es opcional. Se puede hacer manejo de los archivos desde la terminal).

## Procedimiento

1. Clona este repositorio en tu máquina local. ¿Qué comando es el más adecuado para esto?.
2. Verifica el estado del repositorio.
3. Verifica el historial de commits. 
4. Agrega una nueva serie. Usa el formato de lista con checkboxes de markdown. Guarda el archivo y envíalo al staging area.
5. Verifica el estado de tu repositorio.
6. Agrega el archivo movies.md al repositorio.
7. Verifica el estado de tu repositorio.
8. Realiza un commit con los elementos en el staging area. Verifica el estado y el historial de commits.
9. Agrega una película al archivo movies.md. Guarda el archivo y envíalo al staging area. Agrega una nueva película, guarda el archivo pero **no** lo envíes al staging area. Realiza un commit y verifica el contenido del mismo.
10. Agrega una película y una serie. Solo envía al staging area la película. Realiza un commit y verifica el contenido del mismo.
11. ¿Para que sirve el comando `git commit -am "mensaje"`?.
12. Los commits pueden ser representados en forma de grafo. ¿Qué comando permite ver el historial de commits en forma de grafo?.

> Pista: `--oneline --graph --all`

13. Crea una nueva rama llamada `dev`. (`git branch <nombre_rama>`).
14. Cambia a la rama `dev`. (`git checkout <nombre_rama>`).
15. Verifica en qué rama estás trabajando actualmente.
16. Verificar que ramas son locales, y cuales son remotas. 
17. ¿Qué sucede con el puntero HEAD al crear una nueva rama y moverse entre ramas?.
18. Agrega una nueva serie y una nueva película. Envía ambos archivos al staging area y realiza un commit.
19. Realiza un push y verifica que la rama `dev` se haya creado en el repositorio remoto.
20. Cambia a la rama `main`. Verifica el contenido de los archivos modificados
21. ¿Por qué no se ven los cambios realizados en la rama `dev`? ¿En qué rama estás trabajando actualmente?
22. Ejecuta el comando `git log --oneline --graph --all` para ver el historial de commits en forma de grafo. ¿Qué observas?.
23. Fusiona la rama `dev` con la rama `main`. ¿Qué comando es el adecuado para esto?. 

> Se puede agregar una etiqueta con el comando `git tag <nombre_etiqueta>` para marcar un punto específico en el historial de commits.

### Conflictos

24. Cambia a la rama `dev`.
25. Agrega una nueva serie y una nueva película. Envía ambos archivos al staging area y realiza un commit.
26. Cambia a la rama `main`.
27. Agrega una nueva serie y una nueva película. Envía ambos archivos al staging area y realiza un commit.
28. Cambia a la rama `dev` y fusiona la rama `main` con la rama `dev`. ¿Qué sucede?.
29. Resuelve el conflicto en el archivo `series.md`. Envía el archivo al staging area y realiza un commit.
30. Cambia a la rama `main` y fusiona la rama `dev` con la rama `main`.
31. Verifica el historial de commits en forma de grafo. ¿Qué observas?.
32. Realiza un push de la rama `main` al repositorio remoto.

### Otras operaciones sobre ramas:

#### Eliminar una rama local:

```bash
git branch -d <nombre_rama>
```

#### Eliminar una rama remota:

```bash
git push origin --delete <nombre_rama>
```


### Otros comando útiles:

**Git stash:** Permite guardar cambios temporales que no se quieren commitear aún.

Ejemplo:
Supongamos que se está trabajando en la rama `dev` y se necesita cambiar a la rama `main` para realizar un cambio en esta rama, pero se tienen cambios sin guardar en el archivo `series.md` de la rama `dev` que no queremos llevar a main, pero como todavía son cambios que no están completos, tampoco queremos commitearlos a dev (tedavía). Se puede usar el comando `git stash` para guardar temporalmente esos cambios:

```bash
# Guarda los cambios actuales en el stash
git stash

# Cambia a la rama main
git checkout main

# Realiza el hotfix y haz un commit
echo "Hotfix realizado" >> hotfix.md
git add hotfix.md
git commit -m "Hotfix en la rama main"

# Vuelve a la rama dev
git checkout dev

# Recupera los cambios guardados en el stash
git stash pop
```

Esto permite cambiar de rama sin perder los cambios que aún no committeados.

**Git show:**

Muestra información detallada sobre un commit específico, incluyendo los cambios realizados en ese commit.

`git show <commit_id>`

(El id del commit se puede obtener con `git log`).

**Git reset:**
Permite deshacer cambios en el historial de commits. Hay tres modos principales: `--soft`, `--mixed` y `--hard`.

```bash
# Deshace el último commit pero mantiene los cambios en el staging area
git reset --soft HEAD~1

# Deshace el último commit y mueve los cambios al working directory
git reset --mixed HEAD~1

# Deshace el último commit y elimina los cambios (¡Cuidado!)
git reset --hard HEAD~1

```

**Git revert:**

Crea un nuevo commit que deshace los cambios de un commit anterior sin modificar el historial.

```bash
git revert <commit_id>
```

## Recursos adicionales
- [Pro Git Book](https://git-scm.com/book/en/v2)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Convenciones de mensajes de commit](https://www.conventionalcommits.org/en/v1.0.0/)
- [Gitflow](https://nvie.com/posts/a-successful-git-branching-model/)