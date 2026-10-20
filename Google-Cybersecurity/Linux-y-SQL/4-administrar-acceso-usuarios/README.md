# Linux: Manage User Access

Activity on managing user access in Linux using the commands `useradd`, `usermod`, `userdel`, and `chown`.

## Description

I added a new employee to the system and managed their access during their time in the organization. I created the user, assigned file ownership, added them to a secondary group, and finally removed them from the system when they left.

## Scenario

As a security analyst, I must ensure that only authorized users have access to the system: new users are added, and users who change roles or leave are updated or removed. A new employee with the username `researcher9` joined the organization, so I managed their access throughout their stay.

---

## Task 1: Add a new user

I added the new user `researcher9` to the system and set `research_team` as their primary group.

**Screenshot goes here**

---

## Task 2: Assign file ownership

I made `researcher9` the owner of `/home/researcher2/projects/project_r.txt` with `chown`.

**Screenshot goes here**

---

## Task 3: Add the user to a secondary group

After a few months, the employee also worked in Sales, so I added them to the `sales_team` group. Their primary group remained `research_team`.

**Screenshot goes here**

---

## Task 4: Delete a user

After a year, the employee left the organization. I removed the user with `userdel` and then deleted the empty group with `groupdel`.

**Screenshot goes here**

---

## Summary

I managed user access in Linux: I added a new user, assigned file ownership, added the user to a secondary group, and removed the user and their empty group when they left the organization.

## Commands used

```bash
sudo useradd researcher9
sudo usermod -g research_team researcher9
sudo chown researcher9 /home/researcher2/projects/project_r.txt
sudo usermod -a -G sales_team researcher9
sudo userdel researcher9
sudo groupdel researcher9
```

## Key concepts

- **Authentication**: the process by which a user proves who they are in the system.
- **Authorization**: granting access to specific resources.
- **sudo**: prefix required for administrator tasks.
- **Primary and secondary groups**: a user belongs to one primary group and can belong to several secondary groups.

## Tools

- Linux Bash shell
- Commands: `useradd`, `usermod`, `userdel`, `chown`, `groupdel`

---

# Linux: Administrar el Acceso de Usuarios

Actividad sobre la administración del acceso de usuarios en Linux con los comandos `useradd`, `usermod`, `userdel` y `chown`.

## Descripción

Agregué un nuevo empleado al sistema y administré su acceso durante su permanencia en la organización. Creé el usuario, asigné la propiedad de un archivo, lo agregué a un grupo secundario y, finalmente, lo borré del sistema cuando se fue.

## Escenario

Como analista de seguridad, debo asegurarme de que solo los usuarios autorizados tengan acceso al sistema: se agregan los usuarios nuevos, y se actualizan o eliminan los que cambian de rol o se van. Un nuevo empleado con el nombre de usuario `researcher9` se unió a la organización, así que administré su acceso durante toda su permanencia.

---

## Tarea 1: Agregar un usuario nuevo

Agregué al sistema al nuevo usuario `researcher9` y establecí `research_team` como su grupo primario.

**Aquí va el pantallazo**

---

## Tarea 2: Asignar la propiedad del archivo

Hice a `researcher9` propietario de `/home/researcher2/projects/project_r.txt` con `chown`.

**Aquí va el pantallazo**

---

## Tarea 3: Agregar al usuario a un grupo secundario

Después de unos meses, el empleado también trabajó en Ventas, así que lo agregué al grupo `sales_team`. Su grupo primario siguió siendo `research_team`.

**Aquí va el pantallazo**

---

## Tarea 4: Borrar un usuario

Después de un año, el empleado se fue de la organización. Quité al usuario con `userdel` y luego borré el grupo vacío con `groupdel`.

**Aquí va el pantallazo**

---

## Resumen

Administré el acceso de usuarios en Linux: agregué un usuario nuevo, asigné la propiedad de un archivo, agregué al usuario a un grupo secundario y lo borré junto a su grupo vacío cuando se fue de la organización.

## Comandos utilizados

```bash
sudo useradd researcher9
sudo usermod -g research_team researcher9
sudo chown researcher9 /home/researcher2/projects/project_r.txt
sudo usermod -a -G sales_team researcher9
sudo userdel researcher9
sudo groupdel researcher9
```

## Conceptos clave

- **Autenticación**: el proceso mediante el cual un usuario demuestra que es quien dice ser en el sistema.
- **Autorización**: otorgar acceso a recursos específicos.
- **sudo**: prefijo requerido para tareas de administrador.
- **Grupos primario y secundario**: un usuario pertenece a un grupo primario y puede pertenecer a varios secundarios.

## Herramientas

- Shell Bash de Linux
- Comandos: `useradd`, `usermod`, `userdel`, `chown`, `groupdel`
