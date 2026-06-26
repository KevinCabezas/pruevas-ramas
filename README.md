# Guía Completa para Trabajar con Ramas (Branches) en Git y GitHub

Esta guía explica paso a paso cómo trabajar correctamente con ramas utilizando Git y GitHub, desde clonar un proyecto hasta fusionar cambios con la rama principal.

---

# ¿Qué es una rama?

Una rama (branch) es una copia independiente del proyecto donde puedes realizar cambios sin afectar el código principal.

Esto permite que varios desarrolladores trabajen al mismo tiempo en diferentes funcionalidades.

Ejemplo:

```
main
 ├── login
 ├── carrito
 ├── panel-admin
 └── pasarela-pagos
```

Cada rama desarrolla una funcionalidad distinta.

---

# 1. Clonar el repositorio

Si todavía no tienes el proyecto:

```bash
git clone https://github.com/usuario/proyecto.git
```

Entrar al proyecto:

```bash
cd proyecto
```

---

# 2. Ver en qué rama estás

```bash
git branch
```

Salida:

```
* main
```

El asterisco indica la rama actual.

También puedes usar:

```bash
git status
```

---

# 3. Actualizar la rama principal

Antes de crear una nueva rama siempre debes actualizar `main`.

```bash
git checkout main
```

o

```bash
git switch main
```

Luego:

```bash
git pull origin main
```

Ahora tienes la última versión del proyecto.

---

# 4. Crear una nueva rama

Crear una rama nueva:

```bash
git branch nombre-rama
```

Ejemplo:

```bash
git branch login
```

Pero esto **NO** cambia de rama.

---

# 5. Cambiar de rama

```bash
git checkout login
```

o

```bash
git switch login
```

---

# 6. Crear y cambiar de rama al mismo tiempo

Es la forma más utilizada.

Con checkout:

```bash
git checkout -b login
```

Con switch:

```bash
git switch -c login
```

---

# 7. Ver todas las ramas

Locales:

```bash
git branch
```

Remotas:

```bash
git branch -r
```

Todas:

```bash
git branch -a
```

---

# 8. Trabajar normalmente

Modificar archivos.

Agregar archivos:

```bash
git add .
```

Realizar commit:

```bash
git commit -m "Se agregó el formulario de login"
```

---

# 9. Subir la rama a GitHub

La primera vez:

```bash
git push -u origin login
```

La opción `-u` vincula la rama local con la remota.

Después solo será necesario:

```bash
git push
```

---

# 10. Continuar trabajando

Cada vez que hagas cambios:

```bash
git add .
```

```bash
git commit -m "Descripción del cambio"
```

```bash
git push
```

---

# 11. Cambiar entre ramas

```bash
git switch main
```

o

```bash
git checkout main
```

Para volver:

```bash
git switch login
```

---

# 12. Traer cambios del repositorio

Actualizar la rama actual:

```bash
git pull
```

O específicamente:

```bash
git pull origin login
```

---

# 13. Fusionar una rama con main

Primero cambiar a main:

```bash
git switch main
```

Actualizar:

```bash
git pull origin main
```

Fusionar:

```bash
git merge login
```

Si no existen conflictos:

```
Merge made successfully.
```

Subir cambios:

```bash
git push origin main
```

---

# 14. Eliminar una rama local

```bash
git branch -d login
```

Forzar eliminación:

```bash
git branch -D login
```

---

# 15. Eliminar una rama remota

```bash
git push origin --delete login
```

---

# 16. Ver el historial de ramas

```bash
git log --oneline --graph --all
```

Ejemplo:

```
* a12d32 Login terminado
|\
| * e3452 Formulario
| * 53fa1 Inputs
|/
* 76df3 Proyecto inicial
```

---

# 17. Ver diferencias entre ramas

```bash
git diff main login
```

---

# 18. Renombrar una rama

Renombrar la rama actual:

```bash
git branch -m nuevo-nombre
```

Renombrar otra rama:

```bash
git branch -m viejo nuevo
```

---

# 19. Obtener ramas remotas

```bash
git fetch
```

Verlas:

```bash
git branch -r
```

---

# 20. Crear una rama desde otra

Ejemplo:

```
main
   │
   └── login
          │
          └── login-google
```

```bash
git switch login
```

```bash
git switch -c login-google
```

---

# Flujo de trabajo recomendado

## Paso 1

Actualizar main.

```bash
git switch main
git pull origin main
```

---

## Paso 2

Crear una rama.

```bash
git switch -c nueva-funcionalidad
```

---

## Paso 3

Programar.

---

## Paso 4

Guardar cambios.

```bash
git add .
git commit -m "Descripción"
```

---

## Paso 5

Subir la rama.

```bash
git push -u origin nueva-funcionalidad
```

---

## Paso 6

Crear un Pull Request en GitHub.

---

## Paso 7

Revisar el código.

---

## Paso 8

Fusionar con `main`.

---

## Paso 9

Eliminar la rama.

---

# Buenas prácticas

- Nunca trabajar directamente sobre `main`.
- Crear una rama para cada funcionalidad.
- Hacer commits pequeños y descriptivos.
- Actualizar `main` antes de crear una rama.
- Subir frecuentemente los cambios a GitHub.
- Eliminar ramas que ya fueron fusionadas.
- Utilizar nombres claros para las ramas.

Ejemplos:

```
feature/login
feature/carrito

bugfix/login

hotfix/error-pago

refactor/api

docs/readme

test/login
```

---

# Comandos más utilizados

| Acción | Comando |
|---------|----------|
| Ver ramas | `git branch` |
| Crear rama | `git branch nombre` |
| Crear y cambiar | `git switch -c nombre` |
| Cambiar rama | `git switch nombre` |
| Actualizar rama | `git pull` |
| Agregar cambios | `git add .` |
| Commit | `git commit -m "mensaje"` |
| Subir rama | `git push` |
| Subir primera vez | `git push -u origin nombre` |
| Fusionar ramas | `git merge nombre` |
| Ver historial | `git log --oneline --graph --all` |
| Eliminar rama | `git branch -d nombre` |
| Eliminar rama remota | `git push origin --delete nombre` |
| Ver diferencias | `git diff rama1 rama2` |
| Obtener cambios remotos | `git fetch` |

---

# Flujo visual

```
main
 │
 │ git pull
 ▼
Crear rama
 │
 ▼
feature/login
 │
 │ Programar
 │
 │ git add .
 │
 │ git commit
 │
 │ git push
 ▼
GitHub
 │
 ▼
Pull Request
 │
 ▼
Code Review
 │
 ▼
Merge
 │
 ▼
main
 │
 ▼
Eliminar rama
```

---

# Resumen

El flujo recomendado para trabajar con ramas es:

```bash
# Actualizar main
git switch main
git pull origin main

# Crear una rama nueva
git switch -c feature/nueva-funcionalidad

# Realizar cambios
git add .
git commit -m "Descripción del cambio"

# Subir la rama
git push -u origin feature/nueva-funcionalidad

# Crear un Pull Request en GitHub

# Una vez aprobado, fusionar con main

# Eliminar la rama cuando ya no se utilice
git branch -d feature/nueva-funcionalidad
git push origin --delete feature/nueva-funcionalidad
```