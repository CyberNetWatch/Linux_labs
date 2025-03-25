# Google Cybersecurity Linux Labs

![Linux Permissions](screenshots/C-Change_permissions_chmod_commands.png)

This repository documents my completion of the Linux file permissions lab for the Google Cybersecurity Professional Certificate. The project involved managing file permissions in a Linux environment to improve system security.

## 🔐 Project Overview
The research team needed to update permissions for files and directories within the `projects` directory. The existing permissions didn't reflect the proper authorization levels required. My tasks included:

- Checking current permissions
- Modifying permissions for files and directories
- Verifying changes
- Ensuring proper security controls were implemented

## Screenshot Documentation

### Step 1: Checking Current file and directory details
![Step 1](screenshots/A-Navigate_and_list_permissions_commands.png)  
*Firs few commands were used to navigate to the "projects" directory, then I used ls -l command to show us our current permissions. Here we have one directory called "drafts" and four files named "project...". the 10 character string in the first column represent the set permissions. The first character shows if it's a directory (d) or regular file (-). The next nine characters are grouped in threes, showing permissions for: user/group/other. Each set of three uses r (read), w (write), and x (execute) to show what's allowed. A "-" means that permission isn't granted. Example: drwx--x--- = (d) for Directory, (rwx) user has full access, (--x) group can only execute, (---) and others cant do anyhing to the directory.*

### Step 2: Hidden Files
![Step 2](screenshots/B-hidden_files_-la_command.png)  
*Used command ls -la to show us hidden files and their permissions.*

### Step 3: Removing "write" permission 
![Step 3](screenshots/C-Change_permissions_chmod_commands.png)
*The organization determined that "other" users should only have read access to the project files. Upon reviewing the permissions, I noticed project_k.txt was the only file granting "other" users write access alongside read. Using the command chmod o-w project_k.txt, I removed the write permission for others - this command specifically targets the "other" category (o) and removes (-) write (w) permissions. Following this change, I verified the update by running ls -l to confirm the new permissions were properly applied, ensuring the file now aligned with the organization's security requirements.*

### Step 4: Revoke the group's "read" permission
![Step 4](screenshots/D-Change_permissions_chmod_commands2.png)
*The organization further specified that project_m.txt should no longer be accessible to group members. I executed chmod g-r project_m.txt to revoke the group's read permission, effectively restricting access solely to the file owner while maintaining all original user permissions. This change was immediately verified through ls -l to confirm the updated permission string showed -rw------- for proper access control.*

### Step 5: Change permissions on a hidden file
![Step 5](screenshots/E-Change_permissions_on_hidden_file_with_chmod_numbers.png)
*The organization required modifications to the hidden .project_x.txt file (indicated by the leading dot). Using ls -la to reveal hidden files, I identified it needed permission restructuring - reducing access to read-only for both user and group while revoking all other permissions.*

*Instead of multiple manual commands (g-w, u-w etc.), I efficiently implemented this with chmod 440 .project_x.txt. This octal notation translates to:*
- *First 4: User gets read-only (4)*
- *Second 4: Group gets read-only (4)*
- *0: Others receive no permissions (0)*

*The changes were verified with a ls -la, to confirm the new permission string "-r--r-----" which have matched the security requirements.*

### Step 6: Change permissions for a Directory
![Step 6](screenshots/F-removing_directory_permissions.png)
*To comply with organizational security requirements, I needed to ensure that only researcher2 have access to the drafts directory and its contents. This meant revoking all other permissions. A simple chmod g-x drafts comman was used to remove the group execute access, with that only the researcher2 is able to "rwx" the directory*

### Summary:
Through this project, I systematically modified file and directory permissions to align with the organization’s security requirements, ensuring strict access control. Each change was documented with screenshots and detailed explanations to demonstrate compliance and technical proficiency. Thank you for following along.


## 🛠️ Commands Used
Key Linux commands demonstrated in this project:
- `ls -l`/`ls -la` - View detailed directory listings
- `chmod` - (symbolic & octal notation). Adjusted permissions (e.g., chmod g-x drafts, chmod 440 .project_x.txt)
- `cd`/`pwd` - Navigate directories

## 📚 Skills Demonstrated
- Linux file system navigation
- Permission management (Applied both symbolic (u+rwx) and octal (755) notation for chmod)
- Security Hardening: Revoked unnecessary group/others access (e.g., execute on drafts) and enforced least-privilege principles
- Terminal command proficiency
- Hidden File Handling: Audited and modified permissions for dotfiles (e.g., .project_x.txt)
- Documentation & Process: Screenshot-backed verification of changes / Clear explanations / Command-line proficiency
