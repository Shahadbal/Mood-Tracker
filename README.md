# Mood-Tracker

## Purpose
This project is a mood tracker application that allows users to log their daily experiences in various languages, classify their mood based on their text entries, and receive motivational messages. The project utilizes a combination of [Hugging Face pipelines](https://huggingface.co/models), [OpenAI GPT-3.5-turbo API](https://beta.openai.com/docs/models/gpt-3-5), and [Gradio](https://gradio.app/) for a seamless and interactive user interface.

## Main Files and Their Functions
- **Classifier**: This component uses the `SamLowe/roberta-base-go_emotions` model from Hugging Face's text-classification pipeline to classify the user’s input into various emotional categories. [Hugging Face Model Details](https://huggingface.co/SamLowe/roberta-base-go_emotions)
- **Translator**: To handle non-English input, the `facebook/nllb-200-distilled-600M` model from Hugging Face's translation pipeline is used to translate the user’s text to English before classification. [Hugging Face Translation Model](https://huggingface.co/facebook/nllb-200-distilled-600M)
- **OpenAI GPT-3.5 API**: After mood classification, the OpenAI API generates a message based on the detected mood, offering personalized feedback or advice. [OpenAI GPT-3.5-turbo API Documentation](https://beta.openai.com/docs/models/gpt-3-5)
- **Gradio Interface**: This provides the user interface to input the date, language, and journal entry. It displays the classified mood and generates a motivational message. [Gradio Documentation](https://gradio.app/docs/)
- **Data Storage and Analysis**: User entries (date, text, mood) are stored in a pandas DataFrame for analysis. A function to visualize mood trends over time is provided, generating a plot that displays the frequency of moods over the week.

## Hugging Face Text-to-Text Pipeline

This project utilizes two Hugging Face pipelines:
1. **Text Classification**: The text-classification pipeline is powered by a pre-trained RoBERTa model (`SamLowe/roberta-base-go_emotions`), which classifies input text into one of several emotional labels. The pipeline returns the most likely emotion along with its confidence score. [Hugging Face Text Classification](https://huggingface.co/models?pipeline_tag=text-classification)
2. **Translation**: For multilingual support, the translation pipeline is used. The `facebook/nllb-200-distilled-600M` model translates user inputs from non-English languages to English. The translation task is specified using source and target language codes (e.g., from Arabic to English: `arb_Arab -> eng_Latn`). [Hugging Face Translation Pipeline](https://huggingface.co/models?pipeline_tag=translation)

The system first translates non-English text to English before passing it to the classifier, ensuring all text is analyzed in a uniform language.

## Instructions to Run the Code

### Expected Output from Gradio Interface
- **Input:**
  - Date: e.g., "2024-09-12"
  - Language: e.g., "French"
  - Text: e.g., "Je me sens fatigué aujourd'hui."
- **Outputs:**
  - Mood Classification: e.g., "Today you're feeling sadness"
  - Message: e.g., "It's okay to feel down sometimes, but remember that better days are ahead."
- **Mood Analysis:** When clicking the "Generate" button, a bar chart representing the distribution of moods will be displayed along with a table of the user’s data.

## Authors
- **[Shahad Albalawi]**
- **[Nojood Alnahdi]**
