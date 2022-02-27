DICOM to BIDS
#############

This section covers the basics of DICOM conversion and the custom-made script to semi-automatically arrange the converted images to BIDS format.

Data Acquisition
****************

First thing first. 

You have to be careful when planning for the scanning protocol. The scanning sequences need to be named properly. 
The DICOM header contains several fields, and we will need them to identify the sequence uniquely. 
Following the Garbage-In-Garbage-Out Principle, chaotic naming of the propotol will lead to chaotic output.

DICOM Conversion
****************

We use dcm2niix for dicom conversion. This is a tool developed by Chris Rorden, which could be downloaded ``here <https://github.com/rordenlab/dcm2niix>``__. 

It converts DICOM images to Nifti files, and generate a JSON file which contain necessary headers, including slice timing and diffusion gradients, which are the most important ones, and TR, TE, FoV, etc, which we need to report in the manuscripts. 

The software can make the output files according to the fields in the DICOM header. So before you collect the data, please confirm with the radiologist that the name of the protocol is unique. For instance, if you will acquire three resting-fMRI, they should be named Resting _1, Resting_2 & Resting_3. This also apply to tasks, fieldmaps, and structural scans.

Conversion with dcm2niix
************************

The program takes various input parameters. For example, I find this command useful for post-conversion sorting.

.. code-block:

  dcm2niix -i y -b y -z y -o . -f %f/%t/%p_%r bids/sub-001

Explanation:

.. list-table:: dcm2niix arguments
   :widths: 25 75
   :header-rows: 1
  
  * - -i y
    - ignore 2D images, such as localisers
  * - -b y
    - generate BIDS compatible JSON files
  * - -z y
    - generate nii.gz (compressed nifti), instead of nii
  * - -o .
    - output to current folder
  * - -f bids/%f/%t/%p_%r
    - name of the output file (explain later)

The output files of the -f option above will create a folder bids, and an inner folder sub-001, and an inner folder with names as the scan date and time. The output files william be named as the name of the scanning protocol and the instance number.

Assuming that the sub-001 is scanned on 2022-Jan-06 at 14:05:22, and the DICOM contains the sequences as the first column, the output files will be the right column:

.. list-table:: dcm2niix arguments
   :widths: 25 75
   :header-rows: 1
  
  * - Protocol Name (%p)
    - Output
    - Explanation
  * - T1
    - ./bids/sub-001/20020106140522/T1_1.nii.gz
  * - fieldmap_1
    - ./bids/sub-001/20020106140522/fieldmap_1_1
  * - 
    - ./bids/sub-001/20020106140522/fieldmap_1_2
  * - 
    - ./bids/sub-001/20020106140522/fieldmap_ph_1
  * - resting_1
    - ./bids/sub-001/20020106140522/resting_1
  * - stress_1
    - ./bids/sub-001/20020106140522/stress_1
  * - stress_2
    - ./bids/sub-001/20020106140522/stress_2
  * - resting_2
    - ./bids/sub-001/20020106140522/resting_1resting_1
  * - fieldmap_2
    - ./bids/sub-001/20020106140522/fieldmap_2_1
  * - 
    - ./bids/sub-001/20020106140522/fieldmap_2_2
  * - 
    - ./bids/sub-001/20020106140522/fieldmap_ph_1
  * - resting_3
    - ./bids/sub-001/20020106140522/resting_3_1

As you can see here, only fieldmaps will have 2 instances. They are two EchoTimes obtained within 1 TE.

And we are ready for organising the images to the BIDS structure.



BIDS - Brain Imaging Data Structure
***********************************

Custom scripts are created for the rearranging NIFTIs into BIDS structure.






