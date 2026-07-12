# Next_Word_Prediction
```markdown
# Text Auto-completion NLP Project using BERT

This project demonstrates a text auto-completion system using a pre-trained BERT model, wrapped in an interactive Gradio interface.

## Project Overview

This project implements a text auto-completion system powered by a pre-trained BERT model. It demonstrates how BERT's masked language modeling capabilities can be leveraged to predict the most probable next words in a given phrase. The system includes text cleaning, custom tokenization, and an interactive web interface built with Gradio for real-time user interaction and next-word suggestions.

## Features

*   **BERT-based Prediction**: Utilizes `bert-base-uncased` for highly accurate next-word prediction.
*   **Custom Tokenization**: Includes a basic custom tokenizer for initial text processing.
*   **Data Cleaning**: Processes raw text data to remove irrelevant sections, convert to lowercase, and eliminate special characters.
*   **Interactive Interface**: A user-friendly web interface powered by Gradio for real-time phrase input and next-word suggestions.

## Setup and Dependencies

To run this project, you'll need the following Python libraries. You can install them using pip:

```bash
pip install gradio transformers datasets torch
```

## Usage

1.  **Prepare the Data**: Ensure you have a text file (e.g., `1661-0.txt` as used in the notebook) in the `/content/` directory or update the `file_path` variable to point to your data.
2.  **Run the Notebook**: Execute all cells in the Jupyter/Colab notebook sequentially.
3.  **Launch Gradio Interface**: Once the BERT model is loaded and the data processed, the last cell will launch the Gradio interface. A public URL will be provided, which you can open in your browser.
4.  **Enter Text**: In the Gradio interface, type a phrase (preferably 3+ words) into the input box.
5.  **Get Predictions**: The model will then suggest the top `k` (default 5) next words, with the top prediction highlighted.

## Model Details

*   **Model**: `bert-base-uncased` from Hugging Face Transformers library.
*   **Tokenizer**: `BertTokenizer` corresponding to the `bert-base-uncased` model.

## Data

The project uses a text file (e.g., Project Gutenberg's 'The Adventures of Sherlock Holmes' in the example). The `load_clean_text` function performs the following steps:

*   Removes Gutenberg-specific headers and footers.
*   Converts all text to lowercase.
*   Removes non-alphabetic characters (keeping only letters and spaces).
*   Normalizes whitespace.

The cleaned text is then custom-tokenized and saved as `tokenized_movie_lines.json`.

## Project Structure

*   `pyyTem7IDnCK`: Installs required libraries.
*   `FTKYskRgD8T1`: Imports necessary Python modules.
*   `ueY5F_pDECks`: Loads the pre-trained `bert-base-uncased` model and tokenizer.
*   `bhdueRpXECq8`: Defines and uses `load_clean_text` to process the input text file.
*   `FQQ44NKLEFsc`: Defines `custom_tokenize` and saves the tokenized corpus to a JSON file.
*   `42WF1a_QEIgU`: Implements `predict_next_words` function using BERT for masked language modeling.
*   `VVfhu1R3EOQ8`: Sets up and launches the Gradio web interface.
```
