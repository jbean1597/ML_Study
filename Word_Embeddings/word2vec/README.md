# Word Embeddings with Word2Vec - CBOW 
In this project, a word2vec model was built in PyTorch with a CBOW (Continuous Bag-of-Words) approach to be trained on The Great Gatsby. The model incorporated a typical PyTorch development with ```torch.utils.data.Dataset``` and ```orch.utils.data.DataLoader``` and a word2vec neural network class. The word2vec class initializes a network consisting of 1 embedding layer, that initializes with the size of the vocab (6251) and embedding dimensions, and 2 linear layers, applying a linear transformation to the input data (input = the embedding layer). Within the ```forward()``` method the network completes a forward pass when it is called with inputs (inputs = tensors of context pairs). The methods ```f_predict()``` and ```predict()``` deal with the prediction of the network. ```f_predict()``` is implemented to solve shape errors that came up when passing a single context pair into a forward pass that expects a shape of ```(batch_size, -1)``` where -1 infers as many columns needed to make ```num_rows = batch_size```. The ```predict()``` method transforms the result of the forward pass from a tensor of the word's index to the word itself and returns the word as a prediction for what comes next given the context input into the method.

## End Result of Model
With hyperparameters set as: 
```python

CONTEXT_SIZE = 2
embed_dims = 10
vocab_size = len(vocab) # 6251
BATCH_SIZE = 128
lr = 0.1
```
The model ran through 400 epochs, training for ~48 minutes, and returned monotonic reduction in error and a large reduction in error produced epoch from start to finish (64% reduction). The model as of now still needs some improvements - fixing dataset issue disallowing num_workers in DataLoader, optimizing hyperparameters and activation/loss function choices, and possibly removing words that don't meet a certain frequency threshold. Even still, as the model stands it predicts target words well; it has proudced results such as:
```python
Context:['Daisy', 'is'] Prediction: ['desire']
Context:['Gatsbys', 'house'] Prediction: ['enormous'] and ['largest']
Context:['the', 'party'] Prediction: ['quartet'] # referencing a line/group in the book
```

##### Ways to Improve Model
* Larger amount of epochs
* Optimization of activation/loss functions
* Remove least frequent words
* Change ```predict()``` to take any amount of context words

### Data and Sources
[Full text of The Great Gatsby from Project Gutenberg](https://www.gutenberg.org/ebooks/64317)

#### Size of Dataset
Before Cleaning: ```(268151) # 268151 characters,``` <br>
After Cleaning and Processing: ```(257952)```<br>
After Tokenization and Embedding Dims Applied: ```(6251, , 10) # 6251 unique words, 10 embedding dimensions for each word``` <br>
Ngrams ([context1, context2], target) pairs: ```(49748)```<br>
