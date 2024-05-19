
# BeyondChats Data Processor

## Overview
The `BeyondChats Data Processor` script is designed for efficient retrieval and analysis of data from the BeyondChats API. It focuses on extracting and analyzing citations within textual responses, using advanced natural language processing (NLP) techniques. This document provides a detailed overview of the methodologies, algorithms, and the model used in the script.

## Prerequisites
- Python 3.10
- Libraries: `requests`, `pandas`, `json`, `spacy`
- Access credentials for `https://devapi.beyondchats.com/api/get_message_with_sources`

## Setup Instructions

### Installing Required Libraries
To install the necessary libraries, use the following pip commands:
```bash
pip install requests pandas spacy
```
You will also need to download a spaCy language model that is essential for text processing:
```bash
python -m spacy download en_core_web_md
```

### Environment Configuration
Check your Python version to ensure compatibility:
```bash
python --version
```
If Python 3.10 is not installed, download it from [Python's official website](https://www.python.org/downloads/).

## Execution Instructions

### Obtaining the Script
Clone the source repository:
```bash
git clone <repository-url>
```

### Running the Script
Navigate to the script directory and run:
```bash
python beyondchats_processor.py
```

## Script Functionalities

### Data Retrieval
The script uses the `requests` library to fetch data from the BeyondChats API. It handles pagination by incrementally increasing the page number until all pages are fetched. The script includes robust error handling to manage potential API rate limits through exponential backoff and retry mechanisms.

### Data Storage
Retrieved data is serialized into JSON format and saved locally. This allows for easy data manipulation in subsequent processes.

### Citation Identification
The core of this script lies in its use of the `spacy` library, leveraging the `en_core_web_md` model for natural language processing. Here’s how it works:
- **Tokenization and Text Processing**: The script tokenizes the fetched text data to convert it into a format suitable for NLP operations.
- **Semantic Analysis**: Using the spaCy model, the script performs semantic similarity checks between response texts and potential citation contexts to identify relevant matches.
- **Output Generation**: Identified citations are stored in a structured format, linking each response to its relevant sources based on the analysis.

## Output Files
- `complete_fetched_data.json`: This file contains all the data fetched from the API.
- `citation_results.json`: This file stores the analyzed citations, detailing each response with its corresponding source links.

## Algorithms and Models
The script primarily relies on spaCy's medium-sized English model (`en_core_web_md`) for NLP tasks. This model provides capabilities for part-of-speech tagging, named entity recognition, and real-life trained vectors for semantic similarity calculations among text tokens.

## Support
For more information or support regarding the script or setup, please contact [varunteja98852@gmail.com].
