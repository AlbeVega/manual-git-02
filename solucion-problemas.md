# Guia de soluciones de problemas de git
Aqui se hará una recopilacion de problemas y situaciones mas comunes al momento de trabajar en git, luego se agregarán unas posibles soluciones a dichos problemas.
----
## 📌 Índice de Contenidos
1. [Deshacer cambios locales](#1-deshacer-cambios-locales)
2. [Modificar el último commit](#2-modificar-el-último-commit)
3. [Resolver conflictos de fusión (Merge Conflicts)](#3-resolver-conflictos-de-fusión-merge-conflicts)
4. [Manejo de ramas y pushes rechazados](#4-manejo-de-ramas-y-pushes-rechazados)
5. [Errores de credenciales y autenticación](#5-errores-de-credenciales-y-autenticación)
6. [Recuperar commits o ramas eliminadas](#6-recuperar-commits-o-ramas-eliminadas)

---
## 1. Deshacer cambios locales
Dependiendo del estado en el que se encuentren tus cambios (si solo editaste archivos, si ya usaste `git add`, o si deseas guardarlos temporalmente), el comando a utilizar varía:
1. Deshacer cambios en archivos modificados (sin hacer git add)
Si editaste un archivo pero no lo has preparado para commit:
* Un archivo específico:
```
git restore <nombre_del_archivo>
```
* Todos los archivos del directorio:
```
git restore
```
2. Quitar archivos del área de preparación (después de hacer git add)
Si agregaste archivos a staging pero aún no has hecho commit:
* Un archivo específico:
```
git restore --staged <nombre_del_archivo>
```
* Todos los archivos preparados:
```
git restore --staged
```
3. Descartar todos los cambios locales (limpieza total)
Si quieres volver al estado exacto del último commit y borrar todas las modificaciones no guardadas:
```
git reset --hard HEAD
```
>Atención: Este comando destruye los cambios locales sin posibilidad de recuperación.

## 2. Modificar el último commit
Dependiendo del cambio a realizar, existen 2 formas principales para hacerlo:
* Cambiar solo el mensaje del último commit
_Si no necesitas editar ningun archivo y solo quieres corregir el texto o un error ortografico, utiliza:_
```
git commit --amend -m "Nuevo mensaje corregido"
```
Si prefieres abrir tu editor de texto predeterminado para escribir un mensaje más extenso:
```
git commit --amend
```
* Añadir u olvidar cambios en el último commit
Si deseas modificar un archivo o quieres eliminar algo del commit:
1. Haz las modificaciones necesarias en tu código.
2. Agrega los archivos al área de preparación (staging):
```
git add <archivo> (o git add . para incluir todo)
```
3. Sobrescribe el último commit reutilizando el mensaje anterior (o cambia el mensaje omitiendo `--no-edit`):
```
git commit --amend --no-edit
```

## 3. Resolver conflictos de fusión (Merge Conflicts)
Normalmente un problema de fusión ocurre cuando dos ramas modifican las mismas líneas y Git no sabe cuál conservar.
1. Ubicar archivos:
Ejecuta git status para ver los archivos en conflicto.
2. Resolver marcas en el código:
Resolver marcas en el código, luego edita el archivo, deja solo el código correcto
```
<<<<<<< HEAD
Tu código actual
----
Código de la otra rama
>>>>>>> nombre-de-la-rama
```
3. Confirmar cambios:
Guarda y ejecuta
```
git add .
git commit -m "Resueltos conflictos de merge"
```
> Para cancelar todo usa git merge --abort para regresar al estado previo.

## 4. Manejo de ramas y pushes rechazados
__1. Manejo de Ramas (Commands principales)__
* Crear y cambiar de rama: `git checkout -b <nombre-rama> (o git switch -c <nombre-rama>)`
* Cambiar entre ramas: `git checkout <nombre-rama>`
* Listar ramas: `git branch (añade -a para ver remotas)`
* Borrar una rama local: `git branch -d <nombre-rama>`
2. __Pushes Rechazados (Non-fast-forward):__
Un git push se rechaza cuando el repositorio remoto contiene commits nuevos que no tienes en tu máquina local.
__Solución paso a paso__
* Traer e intregar los cambios remotos:
```
git pull origin <nombre-rama>
```
* Reintentar el push:
```
git push origin <nombre-rama>
```
> Atención: Evita usar git push --force, ya que sobrescribe el historial remoto y puede borrar el trabajo de otros colaboradores.

## 5. Errores de credenciales y autenticación
Estos ocurren cuando Git no tiene acceso válido al repositorio remoto o cuando tus credenciales locales expiraron.
1. __Actualizar credenciales en HTTPS__
Si usas HTTPS y cambió tu contraseña o tu Token de Acceso Personal (PAT):
### En Windows (Administrador de credenciales):
* Abre el menú Inicio y busca Administrador de credenciales.
* Ve a Credenciales de Windows.
* Busca las entradas asociadas a `git:[https://github.com](https://github.com)` (o Bitbucket/GitLab).
* Selecciónala y elige Editar o Eliminar.
* Al hacer `git push` o `git pull` nuevamente, Git te pedirá las nuevas credenciales.
### Usar Personal Access Tokens (PAT):
GitHub y GitLab ya no aceptan la contraseña de la cuenta para autenticar operaciones de Git por HTTPS. Debes generar un Token en la configuración de la plataforma (Developer Settings > Personal Access Tokens) y pegar ese token en lugar de tu contraseña habitual.
2. __Limpiar la memoria caché de credenciales de Git__
Para obligar a gir a olvidar credenciales guardadas:
```
git credential-approve erase
# O desvincular el guardado automático en el sistema:
git config --global --unset credential.helper
```
3. __Verificar la URL del repositorio remoto__
Si intentas subir a un repositorio al que no tienes permiso o la URL es incorrecta:
* Ver remoto actual: git remote -v
* Cambiar de HTTPS a SSH (o viceversa):
```
git remote set-url origin git@github.com:usuario/repositorio.git
```

## 6. Recuperar commits o ramas eliminadas
Para recuperar commits o ramas borradas en Git:
1. Abre el historial de movimientos
```
git reflog
```
2. Copia el hash (el código de 7 caracteres, ej. `a1b2c3d`) del estado o commit que quieres recuperar.
3. Ejecuta el comando según el caso:
* Recuperar una rama:
```
git checkout -b <nombre-de-la-rama> <hash>
```
* Restaurar el commit en tu rama actual:
```
git reset --hard <hash>
```
>(Solo funciona si el commit existió localmente en tu máquina).
