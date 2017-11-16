# Manual Kaldi for Russian

## 1) Get source code of Kaldi & Voxforge_ru recipe for Kaldi:

  `git clone https://github.com/kaldi-asr/kaldi.git`

  `cd kaldi/egs/`

  `git clone https://github.com/freerussianasr/recipes.git`

  `cd ..`

## 2) Build tools:
  
  `cd tools`
  
  `extras/check_dependencies.sh`
  
  *Note: Install dependencies until you've got: ./extras/check_dependencies.sh: all OK.*

  In my particular case:
  
  `sudo apt-get install libtool subversion`
  
  `sudo ln -s -f bash /bin/sh`
  
  `make -j 4`

  *Wait until you have got: All done OK.*
  
  `cd ..`

## 3) Build src:
  
  `cd src`
  
  `./configure` 
  
  *You should get SUCCESS*

  `make depend -j 2`
  
  `make -j 2`
  
  *Wait until you have got: Done*

  `cd ..`

## 4) Go and get data for voxforge_ru:

  `cd egs/recipes/voxforge_ru`
  
  `./getdata.sh`

  *You should get the following output:*
  
    FINISHED —2016-10-24 22:54:44--
  
    Total wall clock time: 1h 17m 39s

## 5) Copy or create symbolic links to utils & steps:

  `ln -s ../../voxforge/s5/steps steps`
  `ln -s ../../voxforge/s5/utils utils`

## 6) Install additional dependencies:

  `sudo apt-get install flac`
  
  `cd ../../../tools/`
  
  `./install_srilm.sh`
  
  If you face the following message:
  
    This script cannot install SRILM in a completely automatic
    way because you need to put your address in a download form.
  
  then:
    
    - go to http://www.speech.sri.com/projects/srilm/download.html
    
    - download srilm...
    
    - put file in ./tools/srilm.tgz (it should be renamed)
  
  `sudo apt-get install gawk`
  `./install_srilm.sh`

  *You should get:*
    
    Installation of SRILM finished successfully
    Please source the tools/extras/env.sh in your path.sh to enable it

  `cd extras/`
  
  `sudo apt-get install swig`
  
  `./install_sequitur.sh`

  `./install_mpg123.sh`

  `./install_atlas.sh`

  *You should get:*
  
    Installation of SEQUITUR finished successfully
  
  `cd ../../`

## 7) Run training script:

  `cd egs/recipes/voxforge_ru`

  Add to path.sh the following line:
  
  `source $KALDI_ROOT/tools/env.sh`

  `./run.sh`

## 8) For running script to record audio:

  `sudo apt-get install python-pyaudio python3-pyaudio`

## Licenses:

*Voxforge ru* - **GPL license**

*Kaldi* - **Apache License**


