# cft

## Table of Contents
+ [About](#about)
+ [Getting Started](#getting_started)
+ [Progress](#progress)
+ [Notes](#notes)
+ [Current Questions](#questions)

## About <a name = "about"></a>
This is a repository dedicated to the development of a test for Microsoft Azure Counterfit.

## Getting Started <a name = "getting_started"></a>

### System Info
Windows 10 through WSL ubuntu 

Anaconda3 - Python 3.9 

Microsoft Azure Counterfit version 1.0.0

### Installation
1. Installed WSL through Windows powershell running `wsl --install'. Note that I used the default Linux distribution ubuntu from the installation.
2. Installed Anaconda through WSL by selecting the most recent version in https://repo.anaconda.com/archive/. After selecting the version, I ran `wget https://repo.continuum.io/archive/[YOUR VERSION]` through the terminal. After that, I ran bash on the file.
3. Installed Counterfit by following the intructions on the repo - cloned the repository then created a virtual environment for it

## Progress <a name = "progress"></a>
This is a progress log of work done. Will be kept rather short as the bulk of information will be kept under notes.
+ Before 6/1 - Ran through the demos and took corresponding notes. 
+ 6/1 - Massive update to the github readme. Began work with looking at preexisting targets in more detail and information on already existing attacks was also gathered. Viewed a webinar with a demonstration of the application. Learned more of the basic general functionality of Counterfit.

## Notes <a name = "notes"></a>
These notes are an organization of of all the information collected and gathered. Therefore, each section (or bullet point) will be updated in the future if new relevant information is found.
+ Demo notes - There are a variety of targets, frameworks, and attacks. These are all divided into separate categories of their own. Attacks change the sample in some way, which results in the AI to recognize the result as something else.
+ Targets - Demo includes satellite image detections, credit card fraud, text sentiments, and more. Each target has a corresponding model type, data type, input shape, and samples which can be used as a specific target to attack. A target must be "interacted" with in order to be used. 
+ Frameworks - Specific to the type of attack. These include art, text, and more. This is the "biggest" aspect of Counterfit. 
+ Attacks - Depend on previous selections (target and framework) were. There are many attacks already and can be divided into various categories such as blackbox and whitebox. Furthermore, it is divided based on the type of framework such as attacks on images as opposed to text.


## Current Questions <a name = "questions"></a>
These are current questions that are being pondered upon. All of the questions as of now relate to Counterfit and what it is capable of. Therefore, upon completion of each question, they will be moved to an answered section.

1. What are other possible targets viable with Counterfit? Examples could include songs, clothing, and more.
2. What are other frameworks that can be used in Counterfit? Examples could include video, sound, and more.
4. What kind of machine learning is involved with Counterfit? 
5. Is an access to servers necessary to perform an attack?
