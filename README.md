# articleGeneratorModel

## About the model

Just provide an title to the model and it will generate a whole article about it (up to 1024 tokens).

## How to try the model

```python
# Install transformers library
!pip install transformers
```

```python
# Load tokenizer and model
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM, TFAutoModelForSeq2SeqLM
model_name = "Seungjun/articleGeneratorV1.0"
tokenizer = AutoTokenizer.from_pretrained("t5-small")
model = TFAutoModelForSeq2SeqLM.from_pretrained(model_name)
```

```python
# Get the article for a given title
from transformers import pipeline
summarizer = pipeline("summarization", model=model, tokenizer=tokenizer, framework="tf")
summarizer(
    "Steve Jobs", # title
    min_length=500,
    max_length=1024,
)
```

## Limitations

As of now 99% of the context generated by the model is not true. 

## How the model was created

The mode was developed by fine-tuning t5-small with a custom dataset. The custom dataset is a csv file with 3 columns and 19K rows. For columns it have id, prompt and article. 


## Example of the training data

| ID      | Prompt               | Article                                                                                                                             |
|---------|----------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| 7751246 | Chesterfield Islands | Chesterfield Islands (îles Chesterfield in French) are a group of uninhabited coral islands located in the Coral Sea, northeast of Australia. They are a territory of ....



## Version Release

