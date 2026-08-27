# Investigación: Comandos Básicos para Git y GitHub

Este documento recopila los comandos esenciales para trabajar con **Git** (el sistema de control de versiones) y **GitHub** (la plataforma de alojamiento de código). Está pensado como una guía de referencia rápida para desarrolladores.

---

## 1. Configuración Inicial
Antes de empezar a trabajar en cualquier proyecto, es necesario configurar tu identidad para que los commits queden registrados con tu nombre y correo.

* `git config --global user.name "Tu Nombre"`: Define el nombre de usuario global para todos tus repositorios.
* `git config --global user.email "tu.correo@ejemplo.com"`: Define el correo electrónico asociado a tus commits.
* `git config --list`: Muestra la configuración actual de Git en tu equipo.

---

## 2. Inicialización y Estado del Repositorio
Estos comandos permiten preparar un proyecto local para que comience a ser rastreado por Git.

* `git init`: Inicializa un repositorio de Git vacío en el directorio actual.
* `git status`: Muestra el estado actual del repositorio (archivos modificados, preparados para commit o sin rastrear).
* `git log`: Muestra el historial de commits realizados en la rama actual.

---

## 3. El Flujo de Trabajo Básico (Local)
El ciclo diario para guardar cambios en tu máquina se compone de tres pasos principales: preparar, confirmar y opcionalmente deshacer.

* `git add <archivo>` o `git add .`: Añade los archivos especificados (o todos los modificados) al área de preparación (*staging area*).
* `git commit -m "Mensaje descriptivo"`: Guarda de forma permanente los cambios preparados en el historial del repositorio local con un mensaje explicativo.
* `git diff`: Muestra las diferencias exactas entre los cambios realizados y la última versión guardada.

---

## 4. Sincronización con GitHub (Remoto)
Una vez que tu código está listo localmente, puedes subirlo o sincronizarlo con un repositorio remoto alojado en GitHub.

* `git remote add origin <URL-del-repositorio>`: Conecta tu repositorio local con un repositorio remoto en GitHub.
* `git push -u origin <nombre-de-rama>`: Sube tus commits locales al repositorio remoto (por ejemplo, `git push -u origin main`).
* `git pull`: Descarga y fusiona los cambios más recientes del repositorio remoto en tu rama local actual.
* `git clone <URL-del-repositorio>`: Clona (descarga) un repositorio existente desde GitHub a tu ordenador.

---

## 5. Gestión de Ramas (Branching)
Las ramas permiten desarrollar nuevas características o corregir errores de forma aislada sin afectar la versión principal del código.

* `git branch`: Lista todas las ramas locales del repositorio.
* `git branch <nombre-de-rama>`: Crea una nueva rama.
* `git checkout <nombre-de-rama>` o `git switch <nombre-de-rama>`: Cambia de la rama actual a la especificada.
* `git checkout -b <nombre-de-rama>`: Crea una nueva rama y cambia a ella de manera simultánea.
* `git merge <nombre-de-rama>`: Fusiona los cambios de la rama especificada con la rama en la que te encuentras actualmente.

---
> **Nota de buenas prácticas:** Realiza commits frecuentes con mensajes claros y descriptivos, y recuerda hacer un `git pull` antes de hacer `git push` para evitar conflictos de versiones con tu equipo de trabajo.

# Comandos Avanzados de Git

## 1. Deshacer y Limpiar Cambios
* `git restore <archivo>`: Descarta los cambios locales no guardados en un archivo, devolviéndolo a su último estado confirmado.
* `git restore --staged <archivo>`: Saca un archivo del *staging area* sin borrar los cambios que hiciste en él.
* `git commit --amend -m "Nuevo mensaje"`: Modifica el mensaje del último *commit* realizado o le agrega cambios que olvidaste incluir.
* `git clean -fd`: Elimina permanentemente todos los archivos y carpetas que no estén rastreados (*untracked*).

## 2. Guardado Temporal (Stash)
* `git stash`: Guarda temporalmente tus cambios en progreso sin hacer un *commit* para dejar el directorio de trabajo limpio.
* `git stash pop`: Recupera y aplica los últimos cambios guardados en el *stash*.
* `git stash list`: Muestra una lista de todas las capturas temporales que tienes almacenadas.

## 3. Historial Avanzado e Inspección
* `git log --oneline --graph --all`: Muestra un historial comprimido en una sola línea por *commit*, dibujando un esquema gráfico de las ramas.
* `git show <hash-de-commit>`: Muestra el detalle exacto y las líneas modificadas en un *commit* específico.
* `git blame <archivo>`: Muestra quién modificó cada línea de un archivo y en qué *commit* lo hizo.

## 4. Trabajo Avanzado con Ramas y Servidores
* `git fetch`: Descarga la información del repositorio remoto (nuevas ramas y *commits*) sin alterar tu código local.
* `git branch -d <nombre-de-rama>`: Elimina una rama local que ya fue fusionada.
* `git push origin --delete <nombre-de-rama>`: Elimina una rama directamente en el repositorio remoto de GitHub.
* `git cherry-pick <hash-de-commit>`: Aplica un *commit* específico de otra rama a la rama en la que estás actualmente.

## 5. Diagnóstico de Errores
* `git bisect start`: Inicia un proceso de búsqueda binaria en el historial para encontrar exactamente qué *commit* introdujo un error en el código.