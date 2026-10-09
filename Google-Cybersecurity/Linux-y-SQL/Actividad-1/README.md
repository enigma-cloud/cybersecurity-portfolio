# Linux: Manage File Permissions

Activity on managing file and directory permissions in Linux using command-line tools.

## Description

The research team at my organization needs to update file permissions for certain files and directories within the projects directory. The current permissions do not reflect the required authorization level. Reviewing and updating these permissions helps keep the system secure.

## Tasks performed

1. **Check file and directory details**: used `ls -la` to list all contents of the projects directory, including hidden files, and determine the permissions set for each file and directory.

2. **Describe the permission string**: analyzed the 10-character string that represents file permissions:
   - **1st character**: indicates the file type (`d` for directory, `-` for regular file).
   - **2nd–4th characters**: read, write, and execute permissions for the user.
   - **5th–7th characters**: read, write, and execute permissions for the group.
   - **8th–10th characters**: read, write, and execute permissions for other users.

3. **Change file permissions**: used `chmod` to remove write permissions for other users on `project_k.txt`.

4. **Change permissions on a hidden file**: modified permissions on `.project_x.txt` to remove write access for user and group, and add read access for the group.

5. **Change directory permissions**: removed execute permissions for the group on the `drafts` directory so only `researcher2` has access.

## Key commands

```bash
ls -la
chmod o-w project_k.txt
chmod u-w .project_x.txt
chmod g-w .project_x.txt
chmod g+r .project_x.txt
chmod g-x drafts

