Project Management
##################

All project information, including documents, subject information, behavioral and imaging data, data analysis and results, should be made accessible to all lab members.

Here, a project folder structure is defined. I will go through the details in subsequent sections.

.. warning::
  This section is just a draft and subject to discussion.

Project Folder
**************

The project folder will be named as p<year>_<name>, e.g. p21_resilience.

Public dataset will be named as pub_<name>, e.g. pub_ukbiobank.

The project folder will be created with the hierarchy as below. 

::

    /
    ├── data
    │   ├── proj
    │   │   ├── p21_resilience
    │   │   │   ├── docs
    │   │   │   ├── instruments
    │   │   │   ├── measures
    │   │   │   ├── paradigm
    │   │   │   ├── biraw
    │   │   │   ├── bids
    │   │   │   ├── preproc
    │   │   │   ├── analysis
    │   │   │   └── published
    │   │   └── p21_Stress
    │   └── ...
    └── ...


Documents (docs)
****************

The folder is intended for all documents related to the project. Including but not limited to:

* Proposal
* Ethics
* Consent Form
* Questionnaires
* Task Paradigms

``Please make suggestions and comments``

Instruments (instruments)
**************************

Questionnaires and related stuff will go here.

Measurements (measures)
************************

The folder is intended for all demographics, questionnaires and experimental data. 

Brain Imaging Data - RAW files (biraw)
***************************************

DICOM files have to be manually sorted into folder named with subject id.

The naming of subject should be labelled with a fixed number of characters. If it is the first one, name it as sub-001, instead of sub-1.

If it is a study with multiple groups, label the subjects with proper initials.

For example:

.. list-table:: Path Names
   :widths: 20 40 40
   :header-rows: 1
   
   * - Groups
     - Labels
   * - Age Group: Young, Middle-age, Old
     - sub-Y001, sub-Y002, ..., sub-M001, sub-M002, ..., sub-O001, sub-O002...
   * - Dx: Major Depression, Healthy Control
     - sub-MD001, sub-MD002, ..., sub-HC001, sub-HC002, ...
   * - Intervention: Qigong vs Physical Exercise
     - sub-QG001, sub-QG002, ..., sub-PE001, sub-PE002, ...
   * - Experimental Manipulatin: Sad Mood vs Neutral
     - sub-SAD001, sub-SAD002, ..., sub-NEU001, sub-NEU002, ...

For groups which follows certain order, but the initials do not:

* sub-1Y001, sub-1Y002, ..., sub-2M001, sub-2M002, ..., sub-3O001, sub-3O002, ...

This will ensure the subject id will be sorted in order, otherwise the file system will show you the files according to alphabetical order, that is sub-M, then sub-O and finally sub-Y.

For data with single timepoint, you can arrange the files as below:

::

    bi1dcm
    ├── sub-R001
    │   └── <dicom files>
    ├── sub-R002
    │   └── <dicom files>
    └── ...

For data with multiple timepoint, you can arrange the files as below:

::

    bi1dcm
    ├── sub-R001
    │   ├── ses-01
    │   └── ses-02
    ├── sub-R002
    │   ├── ses-01
    │   └── ses-02
    └── ...

OR, to make it more readable

::

    bi1dcm
    ├── sub-R001
    │   ├── ses-1baseline
    │   ├── ses-2fu03mths
    │   └── ses-3fu12mths
    ├── sub-R002
    │   ├── ses-1baseline
    │   ├── ses-2fu03mths
    │   └── ses-3fu12mths
    └── ...

Note that the name of the sessions is better equal-lengthed.

.. note::
   Plan the naming of subject and session ahead. It will save your life.

Brain Imaging Data Structure (bids)
***********************************

This folder is intended for brain imaging datas sorted according to the `Brain Imaging Data Structure (BIDS) <https://bids.neuroimaging.io/>`__.
Please read the `specification<https://bids-specification.readthedocs.io/en/stable/>`__ for details. 

There should be a json (dataset_description.json) file descripting the dataset, a text file containing the participant information (participants.tsv) and a description sidecar (participants.json). See `here<https://bids-specification.readthedocs.io/en/stable/03-modality-agnostic-files.html>`__ for details.

::

    bids
    ├── dataset_description.json
    ├── participants.json
    ├── participants.tsv
    ├── sub-R001
    ├── sub-R002
    └── ...

Preprocessed Data (preproc)
***************************

This folder is intended for preprocessed files. 

Currently, two pipelines have been developed for functional MRI and diffusion-weighted images. 
After you have converted and sorted the images to the bids folder, you can run the corresponding scripts, and the output files will be stored there.

::

    preproc
    ├── fmriprep
    ├── tortoisedti
    └── ...

Analysis (analysis)
*******************

.. note::
  This section is just a recommendation.
  
  I understand that everyone has his/her own habit, but it's still better to follow some system, 
  such that other lab members could pick up what you did after you left the lab.
  
  Data analysis procedures will be illustrated in separate sections.

The structure below illustrate the pattern for the arrangement. As you could see, the naming convention resembles closely with the BIDS format.

.. list-table:: 
   :widths: 20 40
   :header-rows: 1
   
   * - Prefix
     - Meaning
   * - task-
     - the task being analysed
   * - level-
     - level-1: first-/subject-level, level-2: second-/group-level
   * - con-
     - Name of the contrast.
   * - seed-
     - For seed-based analysis, e.g. ppi.

::

    analysis
    ├── roi
    ├── feat
    │   ├── task-mist_level-1_con-01
    │   ├── task-mist_level-2_con-01
    │   ├── task-mist_seed-aaldacc_level-1_con-01
    │   ├── task-mist_seed-aaldacc_level-2_con-01
    │   ├── seed
    │   │   ├── aal
    │   │   └── shen268
    │   ├── fsf
    │   └── scripts
    ├── dcm12
    ├── mrtrix
    ├── bedpostx
    └── ...

Published
*********

For all published data, it's better to keep a version could reproduce the results.

If possible, all analysis, including the text descriptions, scripts, data and the paper itself, should be documented in this folder.

The structure should be the same as the analysis folder, just simply move or copy the final version here.

::

    published
    ├── Lee2021NeuroImage
    │   ├── feat
    │   └── scripts
    └── ...

