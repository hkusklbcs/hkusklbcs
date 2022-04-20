Server Admin
############

Setting up server environment for users
***************************************

The script is added at ``/etc/profile.d/sklserver.sh``, which only source the file ``/data/scripts/bashrc``.

This script should only be triggered from interactive shell.

The script also set ``umask 002``, the created files will be accessible to group members.

Create Project and Adding Users to Group
****************************************

The script ``/data/scripts/proj_create.sh`` has been created to add project group and project folder.

Project folder is created with ``chmod g+s``, so the files and folders beneath will be created under the group. 

The script ``/data/scripts/proj_adduser.sh`` will add users to the group.
