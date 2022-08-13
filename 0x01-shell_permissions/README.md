# Shell, permissions

In this project, I learned about using the `chmod`, `sudo`, `su`, `chown`, and
`chgrp` commands to represent and change Linux file permissions and change users
in the Shell.

## Tasks :page_with_curl:

* **0. My name is Betty**
  * [0-iam_betty](./0-iam_betty): Bash script that changes the user ID to `betty`.

* **1. Who am I**
  * [1-who_am_i](./1-who_am_i): Bash script that prints the effective userid of the
  current user.
  
  * **2. Groups**
  * [2-groups](./2-groups): Bash script that prints all the groups the
  current user is a part of.

* **3. New owner**
  * [3-new_owner](./3-new_owner): Bash script that changes the owner of the
  file `hello` to the user `betty`.

* **4. Empty!**
  * [4-empty](./4-empty): Bash script that creates an empty file called `hello`.

* **5. Execute**
  * [5-execute](./5-execute): Bash script that adds execute permissions to the owner
  of the file `hello`.

* **6. Multiple permissions**
  * [6-multiple_permissions](./6-multiple_permissions): Bash script that adds
  execute permission to the owner and the group owner, and read permission to
  other users, for the file `hello`.
  
  * **7. Everybody!**
  * [7-everybody](./7-everybody): Bash script that adds execution permission to the owner,
  the group owner and the other users, for the file `hello`.

* **8. James Bond**
  * [8-James_Bond](./8-James_Bond): Bash script that sets the permission for the file
  `hello` as follows:
    * Owner - no permission at all
    * Group - no permission at all
    * Other users - all permissoins

* **9. John Doe**
  * [9-John_Doe](./9-John_Doe): Bash script that sets the mode of the file
  `hello` to -rwxr-x-wx.

* **10. Look in the mirror**
  * [10-mirror_permissions](./10-mirror_permissions): Bash script that sets the mode
  of the file `hello` the same as the file `olleh`.

* **11. Directories**
  * [11-directories_permissions](./11-directories_permissions): Bash script that adds execute
  permission to all subdirectories of the current directory for the owner, the group owner
  and all other users. Regular files are not changed.

* **12. More directories**
  * [12-directory_permissions](./12-directory_permissions): Bash script that creates a
  directory `dir_holberton` with permissions 751 in the working directory.

* **13. Change group**
  * [13-change_group](./13-change_group): Bash script that changes the group owner to
  `holberton` for the file `hello`.