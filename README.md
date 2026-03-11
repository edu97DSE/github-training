# Curso de GitHub y GitHub Codespaces

Bienvenido al repositorio oficial del curso de GitHub y GitHub Codespaces. Aquí encontrarás los recursos y ejercicios prácticos para aprender a trabajar con Git, GitHub y el flujo de trabajo colaborativo.

## Contenido del Curso

- Introducción a Git y GitHub
- Repositorios, ramas y commits
- Pull Requests y revisión de código
- Manejo de conflictos de merge
- GitHub Codespaces

---

## Ejercicio 1 — Flujo de trabajo individual con GitHub

### Objetivo

Practicar el flujo completo de trabajo en GitHub: crear un repositorio, trabajar en una rama, subir cambios, abrir un Pull Request, recibir revisiones y hacer merge.

### Pasos

1. **Crear tu propio repositorio**
   - Ve a [github.com](https://github.com) e inicia sesión.
   - Haz clic en el botón **"New"** (o **"+"** → **"New repository"**).
   - Asigna un nombre al repositorio (por ejemplo: `mi-primer-repo`).
   - Selecciona **Public** y marca la opción **"Add a README file"**.
   - Haz clic en **"Create repository"**.

2. **Clonar el repositorio localmente (o abrir en Codespaces)**
   - Opción A — Codespaces: Haz clic en **"Code"** → **"Codespaces"** → **"Create codespace on main"**.
   - Opción B — Local: Copia la URL del repositorio y ejecuta:
     ```bash
     git clone <URL-de-tu-repositorio>
     cd mi-primer-repo
     ```

3. **Crear una rama de trabajo**
   ```bash
   git checkout -b feature/mi-primera-rama
   ```

4. **Agregar archivos al repositorio**
   - Crea o edita el archivo `README.md` con una descripción personal, o agrega archivos de código.
   - Ejemplo: crea un archivo `saludo.c` con el siguiente contenido:
     ```c
     #include <stdio.h>

     int main() {
         printf("Hola, soy <tu nombre>!\n");
         return 0;
     }
     ```

5. **Registrar y subir los cambios**
   ```bash
   git add .
   git commit -m "Agrego mi primer archivo"
   git push origin feature/mi-primera-rama
   ```

6. **Crear un Pull Request (PR)**
   - Ve a tu repositorio en GitHub.
   - Verás un aviso de la rama recién subida; haz clic en **"Compare & pull request"**.
   - Escribe un título y una descripción que expliquen tus cambios.
   - Haz clic en **"Create pull request"**.

7. **Solicitar y recibir revisiones**
   - En el PR, ve a la sección **"Reviewers"** y solicita la revisión de al menos un compañero o del instructor.
   - Responde los comentarios y realiza los ajustes necesarios si se te solicitan cambios.

8. **Hacer merge del Pull Request**
   - Una vez aprobado el PR, haz clic en **"Merge pull request"** → **"Confirm merge"**.
   - Borra la rama remota si ya no la necesitas.

---

## Ejercicio 2 — Conflictos de merge en equipo

> **Repositorio a utilizar:** El instructor les indicará el repositorio el día del ejercicio.

### Objetivo

Simular un flujo de trabajo colaborativo en el que varios integrantes modifican el mismo archivo y experimentan conflictos de merge al intentar integrar sus cambios.

### Pasos

1. **Clonar el repositorio del ejercicio (o abrir en Codespaces)**
   ```bash
   git clone <URL-del-repositorio-indicado>
   cd <nombre-del-repositorio>
   ```

2. **Crear tu rama de trabajo personal**
   ```bash
   git checkout -b feature/<tu-nombre>
   ```

3. **Modificar el archivo `main.c`**
   - Abre el archivo `main.c` y realiza algún cambio dentro de la función `main()`.
   - Por ejemplo, modifica o agrega un `printf` con tu nombre:
     ```c
     printf("Modificado por <tu nombre>\n");
     ```

4. **Registrar y subir tus cambios**
   ```bash
   git add main.c
   git commit -m "Modificación de main.c por <tu nombre>"
   git push origin feature/<tu-nombre>
   ```

5. **Crear un Pull Request**
   - Ve al repositorio en GitHub.
   - Abre un Pull Request desde tu rama hacia `main`.
   - Describe brevemente qué cambio realizaste.

6. **Observar el proceso de merge**
   - El instructor hará merge de uno o dos PRs hacia `main`.
   - Los demás PRs mostrarán un **conflicto de merge** porque todos modificaron las mismas líneas de `main.c`.

7. **Resolver el conflicto (para los PRs restantes)**
   - Actualiza tu rama local con los últimos cambios de `main`:
     ```bash
     git checkout main
     git pull origin main
     git checkout feature/<tu-nombre>
     git merge main
     ```
   - Git marcará las secciones en conflicto dentro de `main.c` con marcadores como:
     ```
     <<<<<<< HEAD
     // Tu cambio
     =======
     // Cambio de la rama main
     >>>>>>> main
     ```
   - Edita el archivo, elige qué código conservar y elimina los marcadores.
   - Registra la resolución y sube los cambios:
     ```bash
     git add main.c
     git commit -m "Resuelvo conflicto de merge en main.c"
     git push origin feature/<tu-nombre>
     ```

---

## Recursos adicionales

- [Documentación oficial de Git](https://git-scm.com/doc)
- [GitHub Docs — Pull Requests](https://docs.github.com/es/pull-requests)
- [GitHub Docs — Resolver conflictos de merge](https://docs.github.com/es/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line)
- [GitHub Codespaces](https://docs.github.com/es/codespaces)
