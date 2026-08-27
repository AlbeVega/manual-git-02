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
