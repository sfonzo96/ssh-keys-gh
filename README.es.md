# Script de Gestión de Claves SSH

Available languages:

-   [English](README.md)
-   [Español](README.es.md)

Este script en Bash simplifica la gestión de claves SSH para un usuario. Permite verificar si ya existe una clave SSH,
mostrar la clave pública actual y generar una nueva clave SSH ED25519 usando un correo electrónico proporcionado.

> ⚠️ **Nota**: Este script está diseñado únicamente para sistemas **Linux**. Se planea una versión compatible con
> Windows (probablemente usando PowerShell) en el futuro.

## Funcionalidades

-   Verificar si ya existe una clave SSH (`id_ed25519.pub`)
-   Mostrar la clave pública SSH actual
-   Generar un nuevo par de claves SSH con un correo electrónico
-   Instalar `ssh-keygen` si no está presente
-   Agregar automáticamente la clave al `ssh-agent` si está corriendo

## Preparación

Clonar este repositorio en tu máquina local ejecutando los siguientes comandos:

```bash
git clone https://github.com/sfonzo96/ssh-keys-gh
cd ssh-keys-gh
```

## Uso

```bash
./set_ssh_key.sh [opción] [correo]
```

### Opciones

-   `-h`, `--help`  
    Muestra la ayuda del script.

-   `-s`, `--show`  
    Muestra la clave pública SSH actual.

-   `-c`, `--check`  
    Verifica si ya existe una clave SSH.

-   `-g`, `--generate <correo>`  
    Genera una nueva clave SSH. Requiere un correo válido como argumento.

### Ejemplos

Verificar si ya existe una clave:

```bash
./set_ssh_key.sh --check
```

Generar una nueva clave con tu correo:

```bash
./set_ssh_key.sh --generate tu_correo@ejemplo.com
```

Mostrar tu clave pública SSH:

```bash
./set_ssh_key.sh --show
```

## Agregar la clave SSH en GitHub

-   Después de generar la clave SSH, necesitas agregarla a tu cuenta de GitHub. Sigue estos pasos:

    -   Copia la clave SSH generada (output del script completo) al portapapeles.
    -   Ve a la configuración de tu cuenta de GitHub.
    -   Navega hasta "SSH and GPG keys".
    -   Haz clic en "New SSH key" (Nueva clave SSH).
    -   Añade un título para la clave (por ejemplo, "Clave SSH de mi laptop").
    -   Asegúrate de que el campo "Key type" tenga seleccionada la opción "Authentication Key" (Clave de autenticación).
    -   Pega la clave SSH en el campo "Key".
    -   Haz clic en "Add SSH key" (Agregar clave SSH).
    -   Es posible que se te pida ingresar tu contraseña de GitHub para confirmar la adición de la clave.

-   Seguir estos pasos te permitirá hacer _push_ y _pull_ desde tus repositorios de GitHub de inmediato.

## Notas

-   Si `ssh-keygen` no está instalado, el script preguntará si deseás instalarlo usando `apt-get`.
-   Las claves se generan usando el algoritmo ED25519 y se guardan en `~/.ssh/id_ed25519`.

## Planes Futuros

-   Agregar soporte para Windows mediante PowerShell
-   Implementar un manejo de errores más avanzado

## Referencias

-   [Generar clave SSH y agregarla a ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
-   [Agrgar clave SSH a GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account?tool=webui)
