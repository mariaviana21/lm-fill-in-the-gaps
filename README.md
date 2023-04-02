# Language Models to fill in the gaps
Based on the work of Chris Donahue et al. (https://github.com/chrisdonahue/ilm) I've made an approximate approach to their main idea. For that I did a fine-tuning for spanish in the spanish Bert and a fine-tuning for German in german distilbert. The results for both fine-tunings are available in HF (https://huggingface.co/mariav/bert-base-spanish-wwm-cased-finetuned-tweets; https://huggingface.co/mariav/distilbert-base-german-cased-finetuned-amazon-reviews). After that process I manage to create my own fill-in-the-blank prompts using my own tokenizer and model. I create a context (such as 'La ___ es azul') related to the domain of my dataset, tokenize it using my own tokenizer, replace the blank (s) with special token(s) that my model recognizes as placeholders, and then pass the resulting tokens through my model to generate predictions for the missing word (s).

For this I used two different approaches for both models:
- Generating only one [MASK] in the sentence.
- Generating two [MASK] in the sentence.

For the first one I use the context, and for the second one I don't, just to prove the importance of giving a context, because it really changes the results.

For more information check out my report and the colab notebook available in this repository.
