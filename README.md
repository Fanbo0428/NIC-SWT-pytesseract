# Contents
1.[Introduction](# Introduction)
2.[Environment Setup](# Environment Setup)
3.[Customize configurations](# Customize configurations)
4.[Test](# Test)
5.[Training](# Training)
6.[FAQs](# FAQs)
# Introduction
This code is for assembling Google's NIC model, SWT and tesseract to do the tasks on image caption with text recognition. See the report for details
# Environment Setup
For running the code, make sure that you've got environment for Google's NIC model in your computer first. See https://github.com/tensorflow/models/tree/master/research/im2txt for details.

After you build up the enrironment for running Google's NIC model, copy the file 'run_inference.py' to replace the original one in the corresponding directory. 

The file DetectText is generated by codes defined in https://github.com/aperrau/DetectText, the codes are not inclued here, you can go to the link given to get the full code, through this you can change the parameter and some relavent settings. It is noticeable that for different devices and running operation systems, the performance of the same configuration of parameters may be different. 

This code also relies on tesseract (https://pypi.org/project/pytesseract/), you can run the command below in your terminal

$shell sudo pip install pytesseract

In this project, text recognition tasks and image caption tasks focus on English only, so the corresponding model for text recognition in English for tesseract should be installed also.

For some NLP techniques used in this project, SpaCy (https://spacy.io/) is used, you can run the command below for installing SpaCy

$shell sudo pip install spacy

The for models and data in SpaCy, download all the models for NLP in English. 

$shell sudo python -m spacy.en.download all


# Customize configurations
In the prcocess of developing the models, some configurations in code are only acceptable in developer's computer. Here for running in your own computer, you need to modify some codes in the files below:

performance_test.py
run_inference.py
utils.py

You can see the comment in the positions indicating on how you change the code for your own environment.

For users who first running the model, running the command below in your terminal.

$shell python ~/install_nltk_data.py
$shell python ~/utils.py 

This can give you a word list containing all the nouns for further operation.
# Test
For running test, type the command below in you terminal:

$shell python ~/performance_test.py -i inputImage

# Training
Training in this case have two meanings:
1. You want to train the image caption (Google NIC) model with you own data: see the train part in  https://github.com/tensorflow/models/tree/master/research/im2txt for details. You can also get information on how authors train the model by my own data in the project report.
2. You want to modify the SWT model for text detection for better result: Go to https://github.com/aperrau/DetectText and get the code. You can generate your own DetectText to replacr the original one for better performance. 

# FAQs
Some problems faced by authors and the solutions are listed here for convenience.
1.For running the SpaCy model in English, you may need to add 

export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8

in your bashrc or profile file and run command 

$shell source ~/profile 

2. For Errors in python comes in form of 'No modules name ...', you can run command :

$shell sudo pip install ...

to install the corresponding modules in python for this project

For further detail and problems to discuss, you can refer to the project report and contact me by emails: fm2616@ic.ac.uk

