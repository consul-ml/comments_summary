# Comments summarisation

For general information about this project visit: https://github.com/consul-ml/consul-ml

This repository contains the **Natural Language Processing** scripts to summarise comments for the Consul platform. Experiments using this code and a description of the techniques implemented are detailed in https://arxiv.org/abs/2103.00508

This code can be used for the Citizen proposals and/or the Participatory Budgeting features of Consul. Independent scripts are provided for each feature.

The scripts generate for each citizen proposal / budget project:

* Summary of all the comments.

All the comments of each proposal are analysed, and a summary is created with the most relevant sentences of those comments. 

The technique used here is TextRank, applying GloVe embeddings to represent the texts (details in the article at the top).

## How to install this code

The AI/Machine Learning module of Consul is included by default in the installation of Consul, but needs to be activated to use it. In order to do so, please follow the instructions in the module [Administration interface -> AI/Machine Learning -> Help]

To use this "comments summary" code:

1) Copy the corresponding .py files (proposals and/or budgets) to the `public/machine_learning/scripts/` folder of your server.

2) Copy the corresponding .ini files to the `public/machine_learning/data/` folder of your server.

3) Install the Python requirements needed by running "`pip -i requirements.txt`" on the server.

4) If the comments are in English, download the following file https://nlp.stanford.edu/data/glove.6B.zip (e.g. by running `wget https://nlp.stanford.edu/data/glove.6B.zip` in your server) to the `public/machine_learning/scripts/` folder. Once downloaded, the file needs to be unzipped (e.g. `gunzip glove.6B.zip` or `unzip glove.6B.zip`). If the comments are in Spanish the file to download and uncompress is http://dcc.uchile.cl/~jperez/word-embeddings/glove-sbwc.i25.vec.gz (e.g. `wget http://dcc.uchile.cl/~jperez/word-embeddings/glove-sbwc.i25.vec.gz`). The server needs around 3Gb for any of the cases. 


## Settings

The settings of the code can be changed by modifying the `.ini` files. Open the file with a text editor and change any of the settings. Remember to upload the modified version to your server.

Next is presented the most relevant option:
* `max_size_of_summaries = 50` / This setting defines how large should be each summary (max number of words)

## Using the code

To use the code (after following the instructions in the section "How to install this code") open the Administration interface of Consul and click in the "AI / Machine Learning " tab on the bottom left of the menu.

The module will display by default the "Execute script" tab. Select the script to be executed and press the button. It will take some time to run depending on the amount of content on the platform. Once finished it will show a message "The script has been executed successfully." (you will need to refresh the page to see the message). 

Proceed to the "Settings / Generated content" tab. If the execution was successful you will see a button under the corresponding section "Comments summary". Just click on the button to activate the generated content in the platform. All the contents can be deactivated just by clicking on the same button.

In the Help tab you can find more information about the module and how to use it.
