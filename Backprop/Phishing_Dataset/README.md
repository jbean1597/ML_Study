# Phishing Website Predictions 

A model for predicting if a website is a phishing site and the data used are within this folder. A big issue faced with this dataset was the runtime. With just 2 hidden neuron layers with only 1 neuron each the runtime of training the network (with high error in the beginning) was -
```python
CPU times: user 38.5 s, sys: 85.4 ms, total: 38.5 s
Wall time: 38.6 s
```
In an effort to reduce runtime, the netowrk was modified to replace for loops with NumPy matrix operations such as changing the for loop in the activaton function to a ```python np.dot()``` product. This reduced runtime marginally leading me to believe the limitations are model-wide. To bring runtime down significantly the model will likely need to be remade in scikit-learn or another neural network package to migrate more of the mathematical operations to C++.
### Sources

[Kaggle Phishing Dataset](https://www.kaggle.com/datasets/shashwatwork/phishing-dataset-for-machine-learning)
