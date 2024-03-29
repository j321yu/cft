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
+ 6/6 - Looked at the actual code for Counterfit to develop a deeper understanding. Also looked at the code to get an idea of the machine learning and look at ways to potentially improve it.
+ 6/7 - Continued to look at information relating to the machine learning involved, but did not find out much yet. Looked a lot at documentation with other related functionality such as creating own targets, frameworks, etc,. Started to look at a what the demo should include and contain.
+ 6/8 - Began design of the tree. First focused on a few layers. Tree was designed primarily by looking at each target. Then, for each of the three targets, what about it can be done. Note - Tree is on actual paper, not digital.
+ 6/9 - Finished tree to a decent amount. May consider adding more to it later. Resumed work on demo and what it should have.
+ 6/10 - Finished demo. Began to read and amass information on Machine Learning and Cybersecurity as a whole to improve general knowledge on the subject.
+ 6/13 - Completed and reorganized tree. Modified demo to reflect the changed tree.
+ 6/14 - Recorded and sent demo for viewing. Started to look at the ML Model thaht Counterfit uses.
+ 7/6-8 - Began looking at OpenCV and Amazon Polly services for considering whether or not video can be used in Counterfit. First started by using Ubuntu on my own and trying to manually try extracting images from videos and text from the audio in videos.
+ 7/11-15 - Experienced power outage in this time period which caused some delays. Besides that, managed to succeed in extracting images from videos frame by frame. Looked more into Amazon Polly and succeeded in setting it up on WSL2 Ubuntu.
+ 7/18-20 - Started with looking at integration into Counterfit. First steps seem to be with making a new framework that will hold all the code and development. 
+ 7/21-22, 25-29 - Finalized plans with using videos as an integration idea. At the start I considered having a video file directly directly convert into an npz file that a target can use. However, ultimately after discussion with Dr. Wang, it seemed more realistic to process the video beforehand and select frames every so often, as videos tend to not change very often within a few frames.
+ 8/1-8/5 - This week was spent trying to make an ML model work. Through consulting online sources, I managed to get one to work. This was where I got the chance to see the process of training an image recognition model.
+ 8/8-8/12 - Last week, the data used to train the model was not related to road images. Therefore, a lot of this week was spent trying to get relevant datasets that would work for my goal of road images. I found some, but the idea was to be able to have a video frame, and then have the model define it as something "important" or "not important". Therefore, the data I found had to be able to do that. The issue, however, was that the model was very unreliable once I created it.
+ 8/15-8/19 - This time, I got the model to integrate into Counterfit with a bit of difficulty. However, the issue of the unreliable model predictions was still an issue. Therefore, I had to spend time to fix that. The idea is that the labels and dataset somewhat to more accurately reflect moments in video frames, so that the model would be trained with images that are a closer match.

## Notes <a name = "notes"></a>
These notes are an organization of of all the information collected and gathered. Therefore, each section (or bullet point) will be updated in the future if new relevant information is found.
+ Demo notes - There are a variety of targets, frameworks, and attacks. These are all divided into separate categories of their own. Attacks change the sample in some way, which results in the AI to recognize the result as something else.
+ Targets - Demo includes satellite image detections, credit card fraud, text sentiments, and more. Each target has a corresponding model type, data type, input shape, and samples which can be used as a specific target to attack. A target must be "interacted" with in order to be used. 
+ Frameworks - Specific to the type of attack. The preexisting frameworks include art (Adversarial Robustness Toolbox), text, and augly. This is the "biggest" aspect of Counterfit. Art is compatible with any data type and supports all machine learning algorithms. This makes it very flexible with what it can be used in. Text refers to attacking text (usually through the changing of words) and can be used in NLP model training. More information regarding that can be found [here](https://github.com/QData/TextAttack). Augly is a data augmentation library that supports audio, image, text, and video. It's purpose lies in its ability to be able to make changes that "normal" users would make. These include things like reposts, screenshots, changing the image format, and more. This tools effectiveness is where it's able to actually mimic what happens to data in the real world, and then chane it as such. This is important as these can be used to test the effectiveness of the algorithms used even in situations where data is not explicitly attacked.
+ Attacks - Depend on previous selections (target and framework) were. There are many attacks already and can be divided into various categories such as blackbox and whitebox. Whitebox meaning that the attack has access to all the parameters of the target. On the other hand, Blackbox attacks do not have access to all the parameters of the target. Furthermore, it is divided based on the type of framework such as attacks on images as opposed to text. With each attack, there are several parameters that can be adjusted which include, but are not limited to sample index selection, iterations, and size. Each attack affects the confidence value associated with the selection. Afterwards, it can be viewed to see if the attack has sufficiently changed it or not. From testing, it appears that the sample chosen drastically affects the difficulty in successfully attacking the target. The way the code checks for the success of each attack is by comparing the initial labels to the output labels. It then sees if it changes or not. If it does, then it is a success otherwise it is a failure.
+ Code - Divided into 6 folders: commands, core, frameworks, logging, report, targets.
  + Commands - Consists of all the terminal commands and their functionality (what is printed, returned, and such).
  + Core - The majority and most important code. Most of the files import from the other folders. This helps bring together the functionality of the other folders. Of note is the "state.py" file as it is where the class is actually created. This is also where the attacks are actually ran and results processed.
  + Frameworks - Contains the framework code of art, augly, and textattack. Each of these also have the corresponding attacks for the frameworks. 
  + Logging - Logs the queries for each of the attack.
  + Report - Has report printing functionality for each time an attack is ran. This includes confidence levels, queries, index the attack ran at, time taken, and more.
  + Targets - Currently contains all the demo targets. Each target has a classifier, type, and so on which is used to determine compatibility with certain frameworks and attacks. There are also output classes which indicate what the targets can be potentially recognized as. Then, each of the targets has a specific data structure that it is represented with. This is what is modified in the attacks.
  
This is information regarding the progress made towards video implementation in Counterfit.
+ Image - This can be gained from either DirectX or OpenCV. For my case, I will be using OpenCV as image extraction functionality seems to be better supported for my use cases. The goal is to be able to from a video, get a series of images that correspond to that video. This seems to be done best by extracting each frame inside a video. After getting the frames, only every few hundred frames were saved. This was to help increase the likelihood that a completely different image was saved each time, as opposed to having thousands of similar images. This is even more important when considering that a recorded video of driving will have various instances of paused moments such as stoplights.
+ Audio - This can be done through Amazon Polly. This allows for text to be processed into an audio file. A concern is that this doesn't necessarily allow the reverse, however it seems that this can be used to generate data that the ML model can use to train and test itself with. If seeking to extract text through audio, pre-existing Python packages seem to be capable. Ultimately, this was no longer pursued because it seems rather difficult for Counterfit to support two datatypes in the same target. To implement this and images, it would take a lot of extra work which was deemed unnecessary.
+ Model Training - The way that the training was done was by using images. Initially, any sort of image that had something "important" that a person would need to take note of such as signs or stoplights were all put under an "important" label. Then, typical roads that were quite bare and had little on it were considered "plain". However, the issue with that seems to be the model had a very low confidence score, but put most things as "important". Therefore, when training again, it seems that it was necessary to have more specialized labels that would make it more obvious to the model what the images are supposed to represent. For instance, considering an image as one with a "car" as opposed to without a car in it. A car is something that human drivers need to take note of, and likewise so would the model.
+ Implementation - Following the guide in the docs on Counterfit's Github page, I was able to create a skeleton of the target rather quickly. However, there were some issues. The first issue I encountered was the shape of the images. This was somewhat quickly resolved when I made sure that the npz file images were saved with the right sizing that the shape was supposed to represent. Afterwards, there were some issues with the predictions and how I wanted them returned. The issue was that I had forgotten that the predictions were not an "all-or-nothing" situation, but rather that the predictions had a certain confidence level for each label. Therefore, the problem was that I was trying to return a single value for each image, when there would be multiple.


## Current Questions <a name = "questions"></a>
These are current questions that are being pondered upon. All of the questions as of now relate to Counterfit and what it is capable of. Therefore, upon completion of answering each question, they will hopefully be moved to an answered section.

+ What are other possible targets viable with Counterfit? Examples could include songs, clothing, and more.
  + As of now, it seems like there is a very wide range of targets possible with Counterfit. As long as the framework used supports the datatype used to express the target, there should be no issue. Important to note is that Counterfit supports the development of new targets. This can be developed inside the program itself, and then all the changes made within it can be reflected in real-time through "reload --target".
+ What are other frameworks that can be used in Counterfit? Examples could include video, sound, and more.
  + The current existing frameworks seem to be very comprehensive already. Art in theory covers all data types, text involves text, and augly also covers audio, image, text, and video. The question then is if the data structures used to store these images can be used by counterfit and if so, the attacking algorithms can be used to attack it. One key point is to recognize that frameworks are simply containers for attack algorithms.
+ What kind of machine learning is involved with Counterfit?
  + Currently, from looking at the code in the frameworks, it seems as though neural networks and tensorflow is involved. More investigation is still needed to discover the exact types used, as it could vary from framework to framework.
+ Is an access to servers necessary to perform an attack?
  + Given that the quite a few of the attacks are blackbox, this seems to indicate more support towards not needing an access. However, some whitebox is supported, so it may be that an access is not completely mandatory.
+ How do queries relate to the success of an attack? 
  + Simply put, more queries tend to increase the success rate of an attack. However, more queries also indicates more resource usage in the attack as well.
+ When a video is broken down into images and text, is there a way to revert the video back? 
  + This can potentially be important to verify the validity and accuracy of the image/audio extract from the video.
