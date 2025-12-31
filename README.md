# syncc

## Descripción

**syncc** es un script en Bash diseñado para automatizar tareas basadas en una lista de tareas en formato Markdown. El script verifica tareas marcadas como completadas en un archivo Markdown y ejecuta comandos asociados a esas tareas. También permite editar la configuración y el archivo Markdown, y muestra logs de las tareas ejecutadas.

## Características

- **Automatización de tareas**: Ejecuta comandos asociados a tareas marcadas como completadas en un archivo Markdown.
- **Edición de configuración**: Permite editar el archivo de configuración y el archivo Markdown directamente desde la línea de comandos.
- **Logs**: Registra las tareas ejecutadas y permite ver los logs.
- **Notificaciones**: Envía notificaciones a través de Telegram cuando se ejecuta una tarea.

## Requisitos

- **rclone**: Para manejar archivos remotos.
- **curl**: Para enviar notificaciones a Telegram.
- **emacs**: Editor de texto (puede ser reemplazado por otro editor en la configuración).


## Uso

### Comprobar tareas pendientes
```bash
./syncc
```

### Editar archivo de configuración
```bash
./syncc e
```

### Editar lista en archivo Markdown
```bash
./syncc md
```

### Ver logs
```bash
./syncc log
```

### Ayuda
```bash
./syncc h
```

## Configuración

El archivo de configuración `syncc.conf` contiene las siguientes variables:

- **MD**: Ruta del archivo Markdown que contiene la lista de tareas.
- **LOG**: Ruta del archivo de log donde se registran las tareas ejecutadas.
- **EDITOR**: Editor de texto utilizado para editar los archivos de configuración y Markdown.
- **COMMAND**: Comandos asociados a las tareas. Cada línea debe tener el formato `COMMAND="nombre-tarea,comando-a-ejecutar"`.
- **NOTIFICATIONS**: Comando para enviar notificaciones a través de Telegram, Ntfy,...

## Ejemplo de archivo Markdown

El archivo Markdown debe tener el siguiente formato:

```markdown
- [x] Tarea 1
- [ ] Tarea 2
- [x] Tarea 3
```

## Ejemplo de archivo de configuración

```bash
MD="local:/home/angel/syncthing/notas/syncc.md"
LOG="webdav:logs/syncc.log"
EDITOR="emacs -nw -q"

COMMAND="nginx-stop,docker stop nginx"
COMMAND="nginx-start,docker start nginx"

NOTIFICATIONS="curl -X POST https://api.telegram.org/botXXXXXX:XXXXXXXX/sendMessage\?chat_id\=XXXXXXXXXXX\&text\=\"$(echo \"Syncc $LINEA\" | sed 's/ /%20/g')\""
```

## Contribución

Si deseas contribuir a este proyecto, por favor abre un issue o envía un pull request.

## Licencia

Este proyecto está bajo la licencia MIT. Consulta el archivo LICENSE para más detalles.
