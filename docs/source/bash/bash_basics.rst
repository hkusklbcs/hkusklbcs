BASH Basics
###########

Folder Structures
*****************

In the skl5 server, your home folder will be located at ``/data/home``. Files located here could only see by you.

We would like to improve the project management. In short, the data collected will be gone with the lab members once they left the lab. That's awful.

You will need to read the section ``Project Management`` once you understand the basic operation with the Linux environment.

Project folders are located at ``/data/proj``. 
The brain imaging data, demo+behavioral data, as well as project documents, published data and paper, etc, should be place there, so that other could follow up with that.

You will need to understand the permissions of the files and folders, so that lab members could collaborate with each other.

The folders of the Linux system is more or less the same as Windows, except there are no Drive Letters (e.g. C:, D:).

The ``root`` or ``/`` is the lowest folder struct you could access to, just like ``C:\`` in Windows.

The folder separator in Linux is ``/`` instead of ``\``.

Here is some example which you could access to the file system in Linux.

Assuming we have a folder structure like this:

::

    /
    ├── data
    │   ├── apps
    │   │   ├── afni
    │   │   ├── ANTs
    │   │   └── bin
    │   │       ├── c3d *
    │   │       └── dcm2niix *
    │   ├── proj
    │   │   ├── p21_Resil
    │   │   │   ├── bi1dcm
    │   │   │   │   ├── R001
    │   │   │   │   │   ├── Scan1
    │   │   │   │   │   │   └── dicom files
    │   │   │   │   │   └── Scan2
    │   │   │   │   │       └── dicom files
    │   │   │   │   ├── R002
    │   │   │   │   └── R003
    │   │   │   ├── bi2json
    │   │   │   └── bids
    │   │   └── p21_Stress
    │   └── home
    │       ├── johndoe
    │       └── siuming
    └── tmp

Assume I am johndoe, and I am now working in the project folder ``p21_Resil``.

.. list-table:: Path Names
   :widths: 20 40 40
   :header-rows: 1
   
   * - Path Name
     - Explanation
     - Actual Path
   * - /
     - root directory
     - /
   * - ~
     - home directory
     - /data/home/johndoe
   * - .
     - current working directory 
     - /data/proj/p21_Resil
   * - bi1dcm
     - bi1dcm of current directory 
     - /data/proj/p21_Resil/bi1dcm
   * - bi1dcm/R001
     - folder R001 of bi1dcm of current directory 
     - /data/proj/p21_Resil/bi1dcm/R001
   * - \..
     - parent directory
     - /data/proj
   * - ../..
     - parent of parent
     - /data/
   * - ../../apps
     - apps of parent of parent
     - /data/apps
   * - ../../apps/bin/dcm2niix
     - travel through...
     - /data/proj/apps/bin/dcm2niix
     

Basic Commands
**************

Some basic command will be handy for accessing the files.

.. list-table:: Linux Commands
   :widths: 25 75
   :header-rows: 1
   
   * - Command
     - Function
   * - pwd
     - current working directory
   * - ls
     - list the files in the current directory
   * - ls ~
     - list the files in YOUR home folder
   * - ls /data/proj/stress
     - list the files in the particular folder
   * - ls \*.nii.gz
     - list the files in the current directory which ended with .nii.gz
   * - ls \*.{nii,nii.gz}
     - similar as above, but ended with both .nii and .nii.gz
   * - ls sub-00{01..23}
     - list files named sub-0001 to sub-0023
   * - ls -l
     - list files with details
   * - ls sub-\*/ses-\*/\*task\*.json
     - asterisk will be expanded if the filename matches
   * - cd /data
     - change to the folder /data. The preceding slash indicate it is located at root.
   * - cd proj/fmriprep/sub-001
     - From the current folder, go into proj, then fmriprep, etc.
   * - mkdir feat
     - make directory with name "feat"
   * - mkdir feat/sub-001
     - This will fail if the folder feat does not exist.
   * - mkdir -p feat/sub-001
     - Use -p to create folder structures.
   * - mkdir feat/sub-{001,013,015}
     - create three folders under feat.
   * - mkdir feat/sub-{001..015}
     - create 15 folders.
   * - rm myfile.txt
     - remove the file
   * - rm \*.txt
     - remove all file ended with txt
   * - rm doc/file.txt
     - remove the file.txt in doc
   * - rm doc/
     - This will fail. You can't remove a folder with rm.
   * - rm -r doc
     - Unless you use the command with -r (recursive, be careful).
   * - rmdir doc
     - or remove the directory. It will fail if folder is not empty.
   * - mv file1.txt file2.txt
     - rename (or move) the file.
   * - mv sub-001 sub-1001
     - rename the folder.
   * - mv nii/sub-001 bids
     - move the folder sub-001 from nii to bids.

And some more commands to peep into the text files.

.. list-table:: Linux Commands
   :widths: 25 75
   :header-rows: 1
   
   * - Command
     - Function
   * - gedit file.txt
     - use the ui-based text editor to edit the file.
   * - nano file.txt
     - it is a terminal-based editor.
   * - less file.txt
     - show the text in the file. Can scroll up/down.
   * - cat file.txt
     - print the text on the screen
   * - head file.txt
     - print the top few lines of the file
   * - tail file.txt
     - print the last few lines
   * - grep "male" file.txt
     - show the lines with the word "male"
   * - grep "apple\|orange" file.txt
     - lines with apple or orange
   * - grep "apple\|orange" file.txt > newfile.txt
     - save the extracted lines into newfile.txt
   * - grep "banana" file.txt >> newfile.txt
     - append the extracted lines into newfile.txt
 
