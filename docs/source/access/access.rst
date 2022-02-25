Remote Access
#############

Summary
*******

The server is accessible within HKU Network. Remote desktop is also available. 
If you wish to access the server outside HKU network, you will need to use HKU VPN.
See the relevant sections below for details.

Account Application
*******************

You will first need an account. Please contact IT personnel for it.

You will also need to tell them to create project folders. 
The project folder follows some structures, so that other users could follow up even if you left the lab.
Please also read the project management page for further information


SSH - Secure Shell
******************

SSH is the first entry to the server. For Windows users, it is advised to use MobaXterm for remote access. 
It provides not only the secure shell, but also a VNC client, with which you could use the desktop service.

For Mac and iPad, I would recommend Remoter. It is a paid software.


VNC - Virtual Network Computing
*******************************

VNC is a remote desktop service. Graphical User Interfaces will be provided, and you can use the server like your desktop.


MobaXterm
*********

Download from the `MobaXterm website <https://mobaxterm.mobatek.net/download.html>`__. It is a free software.

After you installed the software, you will need to create a SSH session.

.. figure:: MobaXterm-1-SSH.png

The terminal will be started and ask for your password.

For further information using the shell, you will need to see the *BASH tutorial*.


VNC
***

For now, you will want to use the VNC server.

You can type the command below to see the help

.. code-block:: Bash

  vncserver --help
  

.. figure:: MobaXterm-2-VNC-1-help.png
