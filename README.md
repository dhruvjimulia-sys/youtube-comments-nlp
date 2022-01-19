# Social Media Comment Analysis Tool

## Prerequisites
1. Firstly, in order to run this program, you need to install [Java](https://www.java.com/en/download/manual.jsp) and [Python](https://www.python.org/downloads/). This script was tested on Python version 3.8.10 and Java version 17.0.1.

2. Moreover, the Stanford CoreNLP Parser version 4.2.2 is required for Part-Of-Speech (POS) tagging used in suggestion detection. This parser can be installed by running the `installcorenlp.sh` script in the project pirectory:
   ```
   ./installcorenlp.sh
   ```
   Note: To run this command, `7z` and `wget` should be installed on your machine.

   For more information on Stanford CoreNLP Parser, visit you can visit the [official site for the same](https://stanfordnlp.github.io/CoreNLP/). 

3. Furthermore, this project requires several Python packages. In order to install these packages, activate a relevant Python package manager like Anaconda or a Python virtual environment and run the following command in the project directory:
   ```
   pip install -r requirements.txt
   ```

4. In order to access YouTube comments of specific videos, this project uses the YouTube Data API. Therefore, a YouTube API key will be required to run this project, which can be obtained by following the instructions on the [official YouTube API page](https://developers.google.com/youtube/v3/getting-started). After getting the API key, execute the following command in the project directory, replacing `{API_KEY}` with your own API key.
   ```
   echo "YOUTUBE_API_SECRET_KEY = {API_KEY}" >> .env
   ```
5. Since we will need to compare every comment against every other for semantic similarity in order to segregate similar comments into categories, the computation required to assess the semantic similarity should be fast. In order to do this, we can quantize the pretrained BERT model finetuned on the MRPC semantic textual similarity dataset. The quantized BERT model can be directly installed in the correct directory by running the `installquantizedbert.sh` script in the project directory:
   ```
   ./installquantizedbert.sh
   ```
   Note: Ensure that the pip packages are installed before running this script because this script uses `gdown`, a pip package.
   If you want to quantize the model from scratch, then you can run the command `python3 nlp/semantic_textual_similarity/make_quantized_bert_model.py`. However, this will take time and is not reccomended.

## Getting Started
Start the Stanford CoreNLP Parser by running the following command in the project directory:
```
./runcorenlp.sh
```
In another terminal, run the command below, also in the project directory:
```
python3 main.py
```

## Social Media Comments Analysis TODO
* [x] Sentiment Analysis
* [x] Sematic Textual Similarity
* [x] Question Detection
* [x] Suggestion Detection
* [ ] Language Translation & Transliteration

## Credits
StanfordCoreNLP Parser
MRPC dataset