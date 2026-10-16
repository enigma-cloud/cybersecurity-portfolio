# Linux: Manage File Permissions

Activity on managing file and directory permissions in Linux to control access and strengthen system security.

## Description

Examination and management of file permissions in the `projects` directory for the user `researcher2`, who belongs to the `research_team` group. Permissions were verified for all files, including hidden ones, and adjusted to match the required level of authorization.

## Scenario

As a security analyst, configuring proper access permissions is essential to protect sensitive information and maintain overall system security. The user `researcher2` needed to verify that file permissions in the `projects` directory matched the intended authorization level, and change them where necessary to remove unauthorized access.

## Tasks performed

1. **Check file and directory details**: used `ls -l` and `ls -la` to list contents and permissions of the `projects` directory, including hidden files.
2. **Change file permissions**: used `chmod o-w project_k.txt` to remove write access for other users, and `chmod g-r project_m.txt` to remove read access for the group.
3. **Change permissions on a hidden file**: used `chmod u-w,g-w,g+r .project_x.txt` so that both the user and group could read, but not write, the hidden file.
4. **Change directory permissions**: used `chmod g-x drafts` to remove execute access for the group on the `drafts` directory.

## Key commands
cd projects
ls -l
ls -la
chmod o-w project_k.txt
chmod g-r project_m.txt
chmod u-w,g-w,g+r .project_x.txt
chmod g-x drafts

## Key concepts
Authorization: granting access to specific resources in a system.
File permissions: read (r), write (w), and execute (x) permissions granted to the user, group, and others.
Permission string: the 10-character string at the start of each entry; the first character indicates the file type (d for directory, - for regular file).
chmod: changes permissions on files and directories. u sets user permissions, g group permissions, and o others' permissions.
Hidden files: files starting with a dot (.) that require ls -la to be displayed.

## Tools
Linux Bash shell
Commands: cd, ls, chmod

==================

## Linux: Administrar Permisos de Archivos
Actividad sobre la administración de permisos de archivos y directorios en Linux para controlar el acceso y fortalecer la seguridad del sistema.

## Descripción
Examen y administración de los permisos de los archivos del directorio projects para el usuario researcher2, quien pertenece al grupo research_team. Se verificaron los permisos de todos los archivos, incluidos los ocultos, y se ajustaron según el grado de autorización requerido.

## Escenario
Como analista de seguridad, configurar permisos de acceso adecuados es fundamental para proteger información sensible y mantener la seguridad general del sistema. El usuario researcher2 necesitaba verificar que los permisos de los archivos del directorio projects coincidieran con el nivel de autorización previsto, y modificarlos donde fuera necesario para eliminar accesos no autorizados.

## Tareas realizadas
Verificar los detalles de archivos y directorios: usé ls -l y ls -la para listar el contenido y los permisos del directorio projects, incluidos los archivos ocultos.
Cambiar permisos de archivos: usé chmod o-w project_k.txt para quitar el permiso de escritura a otros usuarios, y chmod g-r project_m.txt para quitar el permiso de lectura al grupo.
Cambiar permisos de un archivo oculto: usé chmod u-w,g-w,g+r .project_x.txt para que tanto el usuario como el grupo pudieran leer, pero no escribir, el archivo oculto.
Cambiar permisos de un directorio: usé chmod g-x drafts para quitar el permiso de ejecución del grupo sobre el directorio drafts.

## Comandos clave
cd projects
ls -l
ls -la
chmod o-w project_k.txt
chmod g-r project_m.txt
chmod u-w,g-w,g+r .project_x.txt
chmod g-x drafts

## Conceptos clave
Autorización: otorgar acceso a recursos específicos de un sistema.
Permisos de archivos: permisos de lectura (r), escritura (w) y ejecución (x) otorgados al usuario, al grupo y a otros.
Cadena de permisos: la cadena de 10 caracteres que encabeza cada entrada; el primer carácter indica el tipo de archivo (d para directorio, - para archivo común).
chmod: cambia los permisos de archivos y directorios. u establece los permisos del usuario, g los del grupo y o los de otros.
Archivos ocultos: archivos que comienzan con un punto (.) y que requieren ls -la para mostrarse.
## Herramientas
Shell Bash de Linux
Comandos: cd, ls, chmod
