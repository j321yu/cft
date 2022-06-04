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
+ 6/2 - Continued gathering data. This time with a further focus on attacks. Reminder to look more in-depth at whitebox and blackbox attacks.
+ 6/3 - Continued with 6/2 work. Looked extensively at parameters of attacks. Began to start looking at answers for the questions and finding out what other targets and frameworks Counterfit is compatible with.

## Notes <a name = "notes"></a>
These notes are an organization of of all the information collected and gathered. Therefore, each section (or bullet point) will be updated in the future if new relevant information is found.
+ Demo notes - There are a variety of targets, frameworks, and attacks. These are all divided into separate categories of their own. Attacks change the sample in some way, which results in the AI to recognize the result as something else.
+ Targets - Demo includes satellite image detections, credit card fraud, text sentiments, and more. Each target has a corresponding model type, data type, input shape, and samples which can be used as a specific target to attack. A target must be "interacted" with in order to be used. 
+ Frameworks - Specific to the type of attack. The preexisting frameworks include art (Adversarial Robustness Toolbox), text, and augly. This is the "biggest" aspect of Counterfit. Art is compatible with any data type and supports all machine learning algorithms. This makes it very flexible with what it can be used in. Text refers to attacking text (usually through the changing of words) and can be used in NLP model training. More information regarding that can be found [here](https://github.com/QData/TextAttack). Augly is a data augmentation library that supports audio, image, text, and video. It's purpose lies in its ability to be able to make changes that "normal" users would make. These include things like reposts, screenshots, changing the image format, and more. This tools effectiveness is where it's able to actually mimic what happens to data in the real world, and then chane it as such. This is important as these can be used to test the effectiveness of the algorithms used even in situations where data is not explicitly attacked.
+ Attacks - Depend on previous selections (target and framework) were. There are many attacks already and can be divided into various categories such as blackbox and whitebox. Whitebox meaning that the attack has access to all the parameters of the target. On the other hand, Blackbox attacks do not have access to all the parameters of the target. Furthermore, it is divided based on the type of framework such as attacks on images as opposed to text. With each attack, there are several parameters that can be adjusted which include, but are not limited to sample index selection, iterations, and size. Each attack affects the confidence value associated with the selection. Afterwards, it can be viewed to see if the attack has sufficiently changed it or not. From testing, it appears that the sample chosen drastically affects the difficulty in successfully attacking the target.


## Current Questions <a name = "questions"></a>
These are current questions that are being pondered upon. All of the questions as of now relate to Counterfit and what it is capable of. Therefore, upon completion of answering each question, they will hopefully be moved to an answered section.

+ What are other possible targets viable with Counterfit? Examples could include songs, clothing, and more.
  + As of now, it seems like there is a very wide range of targets possible with Counterfit. As long as the framework used supports the datatype used to express the target, there should be no issue.
+ What are other frameworks that can be used in Counterfit? Examples could include video, sound, and more.
  + The current existing frameworks seem to be very comprehensive already. Art in theory covers all data types, text involves text, and augly also covers audio, image, text, and video. The question then is if the data structures used to store these images can be used by counterfit and if so, the attacking algorithms can be used to attack it.
+ What kind of machine learning is involved with Counterfit? 
+ Is an access to servers necessary to perform an attack?
