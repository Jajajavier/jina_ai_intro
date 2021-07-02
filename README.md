# Jina 2.0 beginners guide

For this guide we are using the repositories from **alexcg1** cloned on July 2, 2021:
 - [Search frontend with Streamlit](https://github.com/alexcg1/jina-meme-search-frontend)
 - [Search backend using Jina](https://github.com/alexcg1/jina-meme-search-image-backend)

This steps were tested on Linux (Ubuntu 20.04), this may work the same for Mac, for Windows 10 it is supposed to work on WSL or Docker but my experience dealing with configurations alone was painful and out of the scope for developing with Jina.

## Requirements
 - Working installation of **virtualenv**
 - Git

## Steps to test or develop applications

### Open Terminal at project folder

## Clone repository and cd into it
    git clone https://github.com/alexcg1/jina-meme-search-image-backend
    cd jina-meme-search-image-backend

### Create and activate virtual environment
    virtualenv env --python=python3.8
    source env/bin/activate

### Install requirements.txt
    pip install -r requirements.txt

### Get models with shell scripting
    sh get_models.sh

### Get json with images metadata
    sh get_data.sh

### :warning: Check on folder data that your memes.json file is more than 70 MB, if it isn't replace with file from [Kaggle](https://www.kaggle.com/abhishtagatya/imgflipscraped-memes-caption-dataset)

### Get images with python script, the parameter is the number of images you want to download minus 1
    python get_images.py 101

### Launch indexing, check flows/index.yml which has good comments about what each line does
    python app.py -t index -n 100

### Launch search endpoint, keep this Terminal alive
    python app.py -t query_restful

### For the front end, open a new Terminal at your base project folder, cd into it, create and activate virtual environment, install the requierements and launch the Streamlit application
    git clone https://github.com/alexcg1/jina-meme-search-frontend
    cd jina-meme-search-frontend
    virtualenv env --python=python3.8
    source env/bin/activate
    pip install -r requirements.txt
    streamlit run app.py

### If it is your first time running streamlit it may prompt for an email, just press Enter.
## Now you can see Jina in action:
 - Open a web browser with your streamlit URL
 - Select the Image radio button
 - Expand Settings, set your endpoint to the one your Jina service is using, i.e. http://localhost:45680/search and hit Enter
 - Click Browse files and select an image to search (one from the data folder or others could be used for testing)
 - Click **Search**

### For better understanding of how Jina works check the repository [Readme](https://github.com/jina-ai/jina) and take a look at the [cookbooks](https://github.com/jina-ai/jina/tree/master/.github/2.0/cookbooks)


