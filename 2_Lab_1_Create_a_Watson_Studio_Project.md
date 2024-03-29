[Back to Syllabus](./README.md#course-syllabus)

- Lab 1 overview
    - In this lab, you will learn how to gather data, which is an important task for generating machine learning models
    - During the machine learning process, data is analyzed and compared to determine correlations and patterns. Without data, you cannot generate a machine learning model, and the data needs to be comparable
    - In the first three labs, you will create a prediction model that is based on the sounds of cats and dogs. During training, the model must be able to compare the audio files that form the training data to determine how to identify a dog barking and a cat purring
    - This lab shows you how the data set that is used to create the Cats and Dogs Sounds prediction model is created. You can follow the instructions to create the data and see how the data was built. However, this is not mandatory for the course because the data set that is created during this lab is available on GitHub, which you can use in Lab 2.
    - Be sure you've installed the prerequisite software and set up accounts that are required for this course. You will need to sign in to Kaggle to download audio files

- Identify a source data set
    - In this section, you learn how the data set for the Cats and Dogs machine learning model was built. To create a machine learning model, each entry in the data set needs to be compared with each other. Consequently, the data used to create the model should have the same fields so that they can be compared
    - Audio files cannot be compared directly. They will be of differing lengths with varying lengths of opening silence before the start of the signature tune or noise. It is difficult to detect the start of the signature noise. It is not just the point at which there is no longer silence. You have no idea of how many bars into the tune the audio recording starts
    - For audio files, you can use signal processing to create a series of numbers which represent each audio track. These numbers can be used to compare the tracks and be used as the basis of a machine learning model
    - In this lab, you use a simplified digital signal processing application to convert the audio track into a table that represents a spectrogram with sound frequency and amplitude as the x and y coordinates. This makes the tracks comparable
    - You can find the application for this lab in GitHub. This application converts the audio files into a comma separated file that contains signal processing profiles for each audio track
    - Open a command or terminal window and create a new directory for the application. For example, on a Mac, use this command: 
        - ```mkdir app```
        - ```cd app```
    - Clone the animal sounds repository:
        - ```git clone https://github.com/ibm-early-programs/animal-sounds```
    - Change to the new animal sounds directory:
        - ```cd animal-sounds```
    - Optional: If you have virtualenv, create a new environment for the application and then activate the environment
    - Find the path by running which or where commands:
        - Windows
            - ```where python```
        - Mac or Linux
            - ```which python```
    - You can then use the path to create your virtual environment
        - ```virtualenv animals -p <path to your installed version of python> ```
    - Activate the environment:
        - Windows
            - ```animals/Script/activate.bat```
        - Mac or Linux
            - ```source animals/bin/activate```
    - If you don’t already have an audio directory, create one for the audio files that you will download from Kaggle:
        - ```mkdir audio```
    - Sign in to Kaggle and download the cats_dogs.zip file. Extract the files and copy them to the audio directory. The zip file contains the test and train subfolders
    - Change to the src directory inside the animal-sounds directory:
        - ```/app/animal-sounds/src```
    - Run the pip install command to install the application requirements, which are the converter and the service application that you'll use in a subsequent lab:
        - ```pip install -r requirements.txt```
    - If you see an SSL certificate error, upgrade pip:
        - ```curl https://bootstrap.pypa.io/get-pip.py | python3```
    - After you upgrade, the requirements installation should succeed
    - Run the converter application that finds the audio files and generates a sound.csv file in the outputs folder:
        - ```python ospconverter.py```
    - The file soundmac.csv is the same file that is opened and saved as a Mac CSV file by using a spreadsheet tool
    - Files on Windows and Macs have different coding for line endings. When you upload the documents to Watson Studio, the line endings are converted to a Linux variant, which might be incorrect if you use the wrong file
    - If you have a spreadsheet application, you can open the file and save it as a .csv file with the appropriate line endings for your operating system
    - Review the generated file
    - Column 1 is the cat and dog classifier, and the remaining columns are the signal processing representation of the related audio tracks
    - You now have the audio files in a representation that can be used to generate a machine learning model

[Go to Next Module](./3_Build_a_Machine_Learning_Model.md)