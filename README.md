# Blue orchid

[site of the project] (https://elbichon.github.io/blue_orchid.github.io/)
###### Blue orchid is a script that when given a language and a subject will extract data from wikipedia, using the section titles as labels and the sentences between two labels as training data. Then, a LSTM classifier will be trained and saved to be re-used later
###### Edit, as LSTM were not very efficient as there was not enough data, I decided to switch to random forest
![alt text](https://theappassembly.com/wp-content/uploads/2016/11/BigDataWordMap-1264x736.jpg)
## Motivation: 
The project is to easily create and serve text classifier in any language on any given subject using the wide open knowledge repository available in wikipedia. Others objectives where also to get a better understanding of LSTM and arg-parse

## Tech/Frameworks used:
- [sklearn](https://keras.io/)
- [spacy](https://scikit-learn.org/stable/)
- [pandas](https://pandas.pydata.org/)
- [beautifull soup](https://www.crummy.com/software/BeautifulSoup/)
- [wikipedia api](https://pypi.org/project/Wikipedia-API/)

## Project Structure:
- blue_orchid.py
- wikipedia.ipynb

## Features:
- [x] Extracting the data from wikipedia and save them as a dataset
- [x] Defining the right machie learning model to train the model
- [x] Saving the model
- [x] Serving the model
- [x] Create an executable that uses argparse, to ask for training or using and then asks for the language and subject or model and sentence to classify
- [x] Adding grid search to fine tune the output model
- [x] Adding a shell script for automatic set up of the system
- [ ] Creating a docker container

## Available languages:
- [x] EN
- [x] DE
- [x] ES
- [x] PT
- [x] FR
- [x] IT
- [x] NL

## Installation
### Docker install
```
TO DO
```
### CLassic install

```
python -m spacy download en
python -m spacy download de
python -m spacy download es
python -m spacy download pt
python -m spacy download fr
python -m spacy download it
python -m spacy download nl
pip install pandas
pip install numpy
pip install scikit-learn
pip install matplotlib
pip install beautifulsoup4
git clone https://github.com/elBichon/unin_classifier.git
```

## Workflow:

*using the model: training a model*
```
python3 blue_orchid.py train <subject> <language>
```
1. Given as input a language, a subject, the ad hoc url will be scrapped
2. An ad hoc dataset is generated containing the paragraph as a label and each sentence as an input
3. A random forest model is fitted to those data

*example: training*
```
python3 blue_orchid.py train polish_hussars en
```
*using the model: in production model*
```
python3 blue_orchid.py predict <subject> <language>
```
1. Given as input a language, a subject and a string to classify
2. The ad hoc model will be selected and loaded
3. The string will go through the network and classify the string 

*example: Using the model*
```
python3 blue_orchid.py predict polish_hussars en
```

https://medium.com/@reuglewiczjeanedouard/how-i-learned-to-stop-worry-and-trust-the-script-f428101ee167
