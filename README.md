Datasets contains text based comments and the labels associated with it
Model it as a supervised learning problem

DATAFLOW :
1)Inputs
    Series of comments
    eg :- I hate you, You suck I'm coming for you
    Labels attached to the comments are multi output
    eg :- moderately toxic, sevearly toxic, threat, racists etc
    multi binary label :- [1,0,0,0 ; 0,1,1,0]

2)Preprocessing phase
    Tokenization :- We are gonna use TextVectorization in keras --> A preprocessing layer which maps text features to integer sequences.
    https://keras.io/api/layers/preprocessing_layers/text/text_vectorization/

    The processing of each example contains the following steps:
        Standardize each example (usually lowercasing + punctuation stripping)
        Split each example into substrings (usually words)
        Recombine substrings into tokens (usually ngrams)
        Index tokens (associate a unique int value with each token)
        Transform each example using this index, either into a vector of ints or a dense float vector.

    

    eg:- Tokenization is one of the first steps in NLP, and it’s the task of splitting a sequence of text into units with semantic meaning
    https://towardsdatascience.com/overview-of-nlp-tokenization-algorithms-c41a7d5ec4f9
 

    

3)Deep NN
    RNN(Intution) --> https://www.youtube.com/watch?v=AsNTP8Kwu80

    1st Layer --> Embedding :- Representing the attributes about the words(in vector)
                    Learn what words are positive, negative or whether or not something is objective or subjective
    Consists of a number of LSTM layers, we have chosen them because these layers are particularly good when it comes to sequences
    LSTM(Intution) --> https://www.youtube.com/watch?v=YCzL96nL7j0 , https://youtu.be/b61DPVFX03I
    The first stage in a LSTM unit determines what percentage of the long term memory is remembered(Forget Gate)
    
    The output of the NN will be a series of multiple binary outcomes
    Once we get the outcomes we are going to serialize it (H5 format)
    H5 format -> Allows us to save our trained Deep NN onto our disk(Hard drive)
    https://docs.fileformat.com/misc/h5/

4)Gradio App https://gradio.app/quickstart/
    Take the H5 model and integrate with Gradio App(UI for ML models)
    Pass comment through are Gradio App and will return a series of output
    See and test our model
