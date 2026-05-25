Umask

root user = 022 
local user = 0022

file permission calculation:
* full permission - umask value = defalt permission


1. System Defined File Types
    - Regular files
    - Directories
    - Symbolic links
    - Device files (block and character)
    - Pipes and sockets


2. User Defined File Types
    - Custom file extensions (e.g., .txt, .jpg, .exe)
    - Configuration files (e.g., .conf, .ini)

## Linux File System Security
Linux File System Security restricts user to access the files and directories. User require permissions to access files or directories. “ls -l” or “ll” command can be used to check security of any file or directory. Above command will display contents from directory along with its security details. 

### Linux
1. File type.
2. Owner Permissions.
3. Group Permissions.
4. Other User Permission.
5. Link Count.
6. Owner of file/directory.
7. Group Owner of File or Directory. 
8. File Size.
9. Creation Date and Time. 
10. File/Directory Name.

file types in Linux 
- `-` : Regular file
- `d` : Directory
- `l` : Symbolic link
- `b` : Block device file
- `c` : Character device file
- `p` : Pipe
- `l` : linkfile

(-) Regular File: The regular file is a most common file type found on the Linux system. It governs all different files such us text files, images, binary files, shared libraries, etc. 

(d) Directory: Directory is second most common file type found in Linux. Directory can be created with the mkdir command.

(l) Symbolic Link: With symbolic links an administrator can assign a file or directory multiple identities. Symbolic link can be thought of as a pointer to an original file.

## File Permissions
read (r) (4) : Read permission allows a user to open and read the contents of a file. In case of directory, read permission allows user to list the contents of the directory.

write (w) (2) : Write permission allows a user to modify or delete the contents of a file. In case of directory, write permission allows user to add, delete, or rename files within the directory.

execute (x) (1) : Execute permission allows a user to run a file as a program or script. In case of directory, execute permission allows user to access files and subdirectories within the directory.

## link count
Link count indicates the number of hard links associated with a file or directory. A hard link is an additional name for an existing file on the filesystem. Each hard link points to the same inode (data structure) on the disk.

## difference between hard link and soft link
* Hard Link:
  - Points directly to the inode of a file.
  - Cannot span across different file systems.
  - If the original file is deleted, the hard link still retains access to the data.    

* Soft Link (Symbolic Link):
  - Points to the file name and path.   
  - Can span across different file systems.
  - If the original file is deleted, the soft link becomes a broken link and no longer points to valid data.    

  ## user and group management
  u --> user owner
    g --> group owner
        o --> other users

    r --> read  
       w --> write
          x --> execute

syntax to change file permission:
chmod (u,g,o) +-= (rwx) <filename>


## defalt permission (umask)
* default permission for file = 666
* default permission for directory = 777

full permission - umask value = default permission

