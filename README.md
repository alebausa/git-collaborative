# Working in pairs with Git 👯

> This repo is for students to practise committing, creating branches and merging them, and working in pairs with Git to get ready for the project

## 📝 Git cheatsheet

| Command                                   | Description                       | 
|-------------------------------------------|-----------------------------------|
| <code>git checkout -b branch-name</code>  | Create new branch AND move to it  | 
| <code>git checkout branch-name</code>     | Move to other branch              | 
| <code>git pull</code> | Brings all changes in branches from remote to local | 
| <code>git pull origin branch-name</code> | Bring changes from specific remote branch  | 
| <code>git stash</code> | Set aside changes without commiting them to change branches for a while  | 
| <code>git stash pop</code> | Bring back the changes you stashed  | 
| <code>git stash drop</code> | Dismiss the changes you stashed  | 
| <code>git add .</code> | Add the files you want to commit or use "." if it is all of them  | 
| <code>git commit -m "Commit name"</code> | Commit changes | 
| <code>git merge branch-name</code> | **From the receiving branch**, merge another branch  | 
| <code>git push origin branch-name</code> | Update branch also on remote repository  | 
| <code>git log --pretty=oneline</code> | See repository commits  | 


⭐️ To add a <code>tree</code> command to see the tree version of the git log, run in any terminal:
```bash
git config --global alias.tree "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"
```

After this, you can run, on any project with git:

```bash
git tree
```

To quit the command line and get out of the log, run:
```bash
:q
```

To practise and improve your Git skills, follow [this tutorial](https://githowto.com/history).

___
## 👯 Proceso para trabajar en pareja:

**A) Cuando voy a empezar una nueva tarea**
1. Cuando voy a iniciar una nueva tarea, me voy a la rama dev (<code>git checkout dev</code>) y hago un <code>git pull origin dev</code> para sincronizar mi rama local de dev con lo que haya podido subir mi compañer@ a github
2. Creo una rama con <code>git checkout -b branch-name</code> con el nombre del feature que voy a hacer, y muevo la targeta en el kanban como "In progress". Una rama también puede ser un bug
```bash
git checkout dev
git pull origin dev
git checkout -b feature-name
```

**B) Cuando acabo la tarea**

Cuando acabo la tarea de esa rama, la guardo y después me llevo los cambios a dev:
```bash
git status
git add .
git commit -m "Closed #number nombre tarea"
git push origin branch-name  # si quiero subir la rama a github para tener la copia ahí, este paso es opcional
git checkout dev  # me voy a la rama compartida
git pull origin dev # vuelvo a comprobar si mi compañer@ ha hecho cambios mientras yo trabajaba
git merge branch-name # me traigo los cambios que he hecho yo a la rama dev y si hay conflictos los arreglo
git commit -m "merges branch-name into dev" # guardo los cambios
git push origin dev # subo los cambios a github para que se los pueda descargar mi compañer@
```
___
## 🎬 Practise time!
### Iteration 1: me, myself and I

- Miembro 1 del equipo debe forkear y clonar el repositorio. En Github, debe dar permisos al otro miembro para editar el repositorio (*Repo > Settings > Collaborators and teams*)
- El otro miembro (Miembro 2), clona el repo **desde la cuenta de Github del compañero (no hacer dos forks)**.
- Miembro 1 crea una rama *dev*: <code>git checkout -b dev</code>
- Miembro 1 hace una función cualquiera en el archivo index.js, los comitea en la rama dev y después sube los cambios la rama *dev* en remoto (Github): <code>git push origin dev</code>

### Iteration 2: conflict is a part of life

- Miembro 2, para traerse lo que hay en remoto, hace <code>git pull</code>
- Miembro 2 se va a la rama *dev*: <code>git checkout dev</code>
- DESDE DEV, crea una nueva rama: <code>git checkout -b navbar</code>
- Crea una navbar en el archivo index.html
- De mientras, Miembro 1 del equipo **se queda en dev** y genera a la vez una navbar en el archivo index.html. Cuando la acaba, comitea los cambios y los sube a la rama dev en remoto
- Miembro 2, cuando acaba de hacer su navbar en la rama *navbar*, comitea los cambios en su rama
- Miembro 2 se va a dev (<code>git checkout dev</code>), trae los cambios que ha hecho el otro compañero en remoto (<code>git pull origin dev</code>) y entonces procede a mergear su rama: <code>git merge navbar</code>
- Como se han tocado las mismas líneas de código, debería haber conflicto. Solucionadlo y después comitear los cambios y subirlo a la rama dev.

### Iteration 3: automation is cool

- Generar un nuevo proyecto en el apartado de Github *Projects > Classic*
- Crear algunas tareas y convertiras a issues
- Asignar etiquetas (routes, views, style) a las tareas y asignar miembros del equipo a las tareas
- Moved una de las tareas **cada uno** a la columna *In progress*
- Hacer cambios en los archivos y probad de hacer commits que cierren las tareas de forma automática. Debéis hacer mínimo 4 tareas: 2 sin conflictos y 2 con conflictos.
```bash
git status
git add .
git commit -m "closed #num featureName"
git push origin branchName
## Después de cada tarea, me voy a la rama dev a actualizarla
git checkout dev
## Miro si mi compi ha hecho algo mientras yo trabajaba
git pull origin dev
git merge branchName
## Soluciono conflictos
git status
git commit -m "merges branchName into dev"
git push origin dev
```
