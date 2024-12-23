# Parallel Book Creation: "Кичинекей ханзада" (Antoine de Saint-Exupéry)

This project demonstrates how to create a parallel book to facilitate language learning. The book aligns sentences between Kyrgyz and English, allowing readers to compare corresponding sentences side by side. The alignment relies on machine learning models and pre-processing techniques.

---

## Key Features
- **Parallel Sentence Alignment:** Each sentence in Kyrgyz is matched with its corresponding English sentence.
- **Machine Learning Models:** Uses advanced sentence embedding models for alignment.
- **Customizable Inputs:** Users can provide their texts to create their parallel book.

---

## Installation
Install the required dependencies using pip:

```bash
pip install -U lingtrain-aligner==0.4.3
pip install razdel dateparser sentence_transformers
```

---

## Tools and Libraries
This project utilizes the following tools and models:
1. **Lingtrain Aligner**
   - Library for parallel sentence alignment.
   - [Documentation](https://github.com/lingtrain/lingtrain-aligner)
2. **Machine Learning Models:**
   - `sentence_transformer_multilingual`
   - `sentence_transformer_multilingual_labse`
   
   **References:**
   - [Making Monolingual Sentence Embeddings Multilingual using Knowledge Distillation](https://arxiv.org/abs/2004.09813)
   - [Language-agnostic BERT Sentence Embedding](https://arxiv.org/abs/2007.01852)

---

## Workflow
### Step 1: Prepare Inputs
Provide the Kyrgyz and English texts for alignment:

- **Kyrgyz Text Example:**

```
Антуан де Сент-Экзюпери%%%%%author.
Кичинекей ханзада%%%%%title.
...
```

- **English Text Example:**

```
The Little Prince%%%%%title.
by Antoine de Saint Exupéry%%%%%author.
...
```

### Step 2: Preprocessing
Add paragraph markers for alignment:

```python
from lingtrain_aligner import preprocessor

text1_prepared = preprocessor.mark_paragraphs(text1)
text2_prepared = preprocessor.mark_paragraphs(text2)
```

### Step 3: Align Sentences
Define languages and models:

```python
lang_from = "kg"
lang_to = "en"
models = ["sentence_transformer_multilingual", "sentence_transformer_multilingual_labse"]
model_name = models[0]
```

Process alignment:

```python
from lingtrain_aligner import aligner
aligned_sentences = aligner.align_sentences(text1_prepared, text2_prepared, lang_from, lang_to, model_name)
```

---

## Output
The final output is a parallel book where sentences are aligned for easy comparison. This format is ideal for language learners.

---

## Additional Resources
- **Editor for Parallel Corpora:** Tools to manually review and adjust alignments.
- **Visualization Helper:** Display alignments visually for better understanding.

---

## Example Output
**Kyrgyz:**
```
Менин досум Францияда жашайт, азыр аякта суук, ачарчылык.
```

**English:**
```
My friend lives in France, where it is cold and he is hungry.
```

---

## Notes
- Ensure the input texts are properly formatted for best results.
- Supported languages depend on the selected model.

---

Happy learning and enjoy your parallel book!
