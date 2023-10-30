# Next Word Prediciton

Importing Libraries:

Import TensorFlow and relevant modules, including the Tokenizer, to tokenize text and create input sequences for the model.
Tokenization:

Initialize a Tokenizer.
Fit the Tokenizer on a list containing a single string variable, text, which is expected to contain the training text data.
Determine the vocabulary size (vocab_size) by getting the length of the Tokenizer's word index, which is a dictionary mapping words to integers.
Creating Input Sequences:

Initialize an empty list, input_sequences, to store sequences of tokenized words.
Split the text into sentences using '\n' as the delimiter.
Tokenize each sentence and create input sequences. For each sentence, it keeps extending sequences from 1 word up to the length of the sentence.
Padding Sequences:

Determine the maximum sequence length (max_len) by finding the length of the longest sequence in input_sequences.
Use pad_sequences to pad the input sequences to a fixed length (max_len) by adding zeros to the beginning (since padding='pre').
Preparing Input and Output Data:

Create input data X by excluding the last word from each sequence.
Create output data Y by taking only the last word from each sequence and converting it to one-hot encoded format using to_categorical.
Model Definition:

Create a Sequential model using Keras.
Add an embedding layer with an input vocabulary size (vocab_size), output dimension of 100, and input length of max_len - 1.
Add an LSTM layer with 150 units.
Add a dense layer with an output size of vocab_size and softmax activation.
Compilation and Training:

Compile the model using categorical cross-entropy as the loss function and the Adam optimizer.
Train the model with input data X and output data Y for 100 epochs.
Generating Text:

A loop generates text based on the trained model. It starts with the initial text 'text' and iteratively predicts the next word using the model.
The word with the highest probability is selected, and the process is repeated to extend the generated text.
