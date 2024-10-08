# Project Overview:
A system that automates the process of generating relevant questions from website content.

## Special Thanks to-
* Overlayy
* RedBull-Basement
* OOSC
providing us the opportunity to create such a great project in just 12-hours!

# PROJECT STRUCTURE
'dataSet' contains the scraped data of different websites.
'output' contains the output of the corresponding datasets
### main.ipynb
It contains the core part of our project, question generation, and most relevant top 5 link and title generation
### Helper Files
* scrapper.py : used for scrapping data from the required websites
* automater.py: tests the generated output with the required parameters

### CREATED BY:
* Joel Bansal
* Manas Jain Kuniya
* Pranav Krishna
* Yash Pandit
* Nischay Agarwal

## Dependencies
To run this project, you need the following Python libraries:

* semantic-split
* nltk
* beautifulsoup4
* unsloth
* transformers
* torch
* sklearn
* sentence-transformers
* numpy
* requests

### Requirements
```
!pip install semantic-split nltk beautifulsoup4 unsloth sentence-transformers transformers torch sklearn numpy requests
!pip install selenium webdriver-manager
!pip install bs4
```

### How to run?
First set the url in the scrapper.py file to the site-link you want to scrape, then run
```
python scrapper.py
```
after scrapping, change the path of the data.json file created in main.ipynb file,
and run the main.ipynb file block by block
finally you will recieve a output.json file in your Present Working Directory.


# Scrape function

The Scrap function navigates to a given URL using Chrome WebDriver, parses the webpage content, and extracts text and links


### Example Use:
```
from scrape_module import Scrap

# Example URL to scrape
url = "https://example.com"
scraped_data = Scrap(url)
print(scraped_data)

```

## Output

The function returns a dictionary containing:

1. relevant_link: A list of dictionaries with URLs and their respective page titles.
2. data: A string concatenating all extracted text and interactive elements' information from the webpage.

## Example Output:
```
{
    "relevant_link": [
        {
            "url": "https://example.com/page1",
            "title": "Page 1 Title"
        },
        {
            "url": "https://example.com/page2",
            "title": "Page 2 Title"
        }
    ],
    "data": "h1: Example Heading p: This is an example paragraph. links to: https://example.com/page1 ..."
}
```

__________________________________________________________________________________________________________________

# Semantic Chunking and Question Generation with Llama 3.1 8B Instruct
This project leverages various NLP techniques, including semantic chunking, question generation, and clustering, to process textual data and generate relevant questions. The goal is to produce meaningful questions that focus on the most important parts of the content provided.

```
==((====))==  Unsloth 2024.8: Fast Llama patching. Transformers = 4.44.2.
   \\   /|    GPU: Tesla T4. Max memory: 14.748 GB. Platform = Linux.
O^O/ \_/ \    Pytorch: 2.3.1+cu121. CUDA = 7.5. CUDA Toolkit = 12.1.
\        /    Bfloat16 = FALSE. FA [Xformers = 0.0.26.post1. FA2 = False]
 "-____-"     Free Apache license: http://github.com/unslothai/unsloth
```

## Workflow
1. Data Loading: The content is loaded from a JSON file and a webpage is scraped for data.
2. Semantic Chunking: The text data is split into smaller, meaningful chunks using sentence similarity techniques.
3. Question Generation: Questions are generated based on the chunked text, focusing on various aspects such as general understanding, specific details, and critical thinking.
4. Clustering: The questions are grouped into clusters to identify the most representative questions.
5. Link Identification: The most relevant online resources are identified based on the generated questions.
5. Validation: The relevance of the questions is validated by comparing them with the original text using cosine similarity.

# Output
* Questions: A list of generated questions focusing on different aspects of the content.
* Relevant Links: Top 5 matching links from the provided resources based on the generated questions.
* Cosine Similarity Score: A score indicating how closely the generated questions match the original content.

### Automation and Validation:
1. After creating the output.json, run
```
python automator.py
```
it will verify that each webpage has exactly 10 questions, each under 80 characters, and that each entry includes 5 relevant links and topics.
2. We can also evaluate the performance of the question generation and using Cosine Similarity in the last code block.

![image](https://github.com/user-attachments/assets/29b4beec-dcf4-4dcf-b787-1fb92f668c28)

# Acknowledgements
* Llama 3.1 8B Instruct: For question generation.
* Semantic-Split: For text chunking.
* K-means Clustering: For grouping similar questions.
* Sentence Transformers: For link identification based on sentence embeddings.
