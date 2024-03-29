# Sentiment analysis tool for Tagit 

## Description
This tool is used to analyze the sentiment of the comments to apps made by tagit on the play store and app store. It uses the llama index library to communicate with openai servers to generate embeddings of tokens in the comments and uses a tokenised form of your prompt to generate relevant analysis of the comments in natural language forms.

This folder consists of 3 files:
1. Scraper-AppStore.py: This is used to scrape the app store for relevant comments. It uses the app store api to get the comments and stores them in a pdf format with the relevant data.
2. Scraper-PlayStore.py: This is used to scrape the play store for relevant comments. It uses the play store api to get the comments and stores them in a pdf format with the relevant data.
3. Embeddings.py: This is used to generate relevant embeddings of the comments. It uses the llama index library to communicate with openai servers to generate embeddings of tokens in the comments.


## Installation
Install the required libraries using the following command:
```zsh
pip install -r requirements.txt
```

## Usage
Do not run the embeddings.py file until you have scraped data from the app store and play store. 

### Play store scraper
To use the play store scraper, run the following command within this directory:
```zsh
python Scraper-PlayStore.py -c COUNTRYCODEHERE -n APPNAMEHERE
```
The Country code and app name can be found in the url of the app you are attempting to scrape. For example, the url for the app "Instagram" in the US is https://play.google.com/store/apps/details?id=com.instagram.android&hl=en_US&gl=US. The country code is the "US" and the app name is "com.instagram.android".

An output with all the comments will be saved in the same directory you ran the script from in the formatComments-app_store-APPNAME.pdf.

### App store scraper

To use the app store scraper, run the following command within this directory:
```zsh
python Scraper-AppStore.py -c COUNTRYCODEHERE -n APPNAMEHERE -i APPIDHERE
```
The Country code and app name can be found in the url of the app you are attempting to scrape. For example, the url for the app "Instagram" in the US is https://apps.apple.com/us/app/instagram/id389801252. The country code is the "us" and the app name is "instagram" and the app id is "389801252".

### Embeddings

Run the embeddings.py file after you have scraped data from the app store and play store only. Otherwise, the script will not work.

To use the embeddings.py file, run the following command within this directory:
```zsh
python embeddings.py -p PROMPTHERE -n APPNAMEHERE -s STORENAMEHERE
```
The prompt is the prompt you want to use to generate the analysis. The app name is the name of the app you are analyzing and the store name is either "app_store" or "play_store" depending on which store you are analyzing.

A store file with all the embedding indices will be saved in the name of the app in the same directory you ran the script from under a folder in the format "Storage-STORENAMEHERE-APPNAMEHERE".
