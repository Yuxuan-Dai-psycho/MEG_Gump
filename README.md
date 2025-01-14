# ForrestGump-MEG: A audio-visual movie watching MEG dataset

For details please refer to our paper on [] and dataset on [].

This dataset contains MEG data recorded from 11 subjects while watching the 2h long Chinese-dubbed audio-visual movie 'Forrest Gump'. The data were acquired with a 275-channel CTF MEG. Auxiliary data (T1w) as well as derivation data such as preprocessed data and MEG-MRI co-registration are also included. 


## Stimuli presentation

The audio-visual stimulus material was from the Chinese-dubbed 'Forrest Gump' DVD released in 2013 (ISBN: 978-7-7991-3934-0), which cannot be publicly released here due to copyright restrictions. The timing alignment for stimuli in the Chinese (cn) and German (de) version ‘Forrest Gump’ is provided in our paper. 

the movie stimuli was presented to the participants using Psychophysics Toolbox Version 3 in MATLAB 2016.  
  Code: ./exp_MEG/megMovieWatching.m


## Pre-process procedure description

The T1w images stored as NIFTI files were minimally-preprocessed using the anatomical preprocessing pipeline from fMRIPrep with default settings. 
  
  Code: ./preproc/mri_preproc.sh

MEG data were pre-processed using MNE following a three-step procedure: 1. bad channels were detected and removed. 2. a high-pass filter of 1 Hz was applied to remove possible slow drifts from the continuous MEG data. 3. artifacts removal was performed with ICA.
  
  Code: ./preproc/meg_preproc.py


## Technical validation procedure description

Quality of both raw and preprocessed data is accessed by four different measurements: head-motion magnitude, stimuli-induced time-frequency characteristics, homotopic functional connectivity (FC) and inter-subject correlation (ISC). 

1. The motion magnitude for each sample was calculated as the Euclidian distance and shown as density and accumulative histogram.
   
   Code:./tech_val/01_compute_headmotion.ipynb
        ./tech_val/02_plot_headmotion_figure.ipynb
   
2. Validation indicates that the change of brain activity induced by stimuli could be successfully detected by MEG recordings.

   Code: ./tech_val/03_stimuli_induced_timefreq.ipynb

3. Homotopic functional connectivity (FC) and heterotopic FC are computed and compared.

   Code: ./tech_val/04_compute_homopotic_conn.ipynb
         ./tech_val/05_plot_homopotic_conn_figure.ipynb

4. Compute inter-subject signal correlation of different band for both raw and preprocessed data.

   Code: ./tech_val/06_compute_ISC.ipynb
         ./tech_val/07_plot_ISC_figure.ipynb
