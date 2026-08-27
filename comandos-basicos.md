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

