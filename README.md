# E2A5

## Fixing Spacy   
The default version of spacy in colab takes a long time to tokenize. By installing spacy==3, it processes the data instantly.

## Loading Data   
As the data in the .txt file was based on phrases, we used the `pytreebank` module to load the SST dataset. This dataset - once loaded - initializes the dataset with five labels (0 to 4).

## Model  
Almost the same model (but slight changes to the number of layers) as presented in the orginal notebooks was used. 

## Accuracy  
The `binary_accuracy` function was changed to `categorical_accuracy` since unlike the original notebook, here we have a multi-class problem

## Results (without Augmentation)  
I was able to get >>60% on the train dataset. Despite tinkering with the hyperparameters, I wasn't able to get accuracy > 40% in the validation dataset.


## Data Augmentation  
The `translator` function was modified to use the `google_trans_new` module. A helper function was created to augment the data. A new dataset was generated using a custom function, and the model was trained on that dataset. Since the vocabulary (generally) increases, we have to re-create the model.

## Results (with Augmentation)  
Unfortunately, my results were not good. Infact, the model stopped learning.


## Conclusion  
Data augmentation should help with training since we have more data. Unfortunately, that was not the case.

## Sample outcomes
A helper function was created to take 10 examples from the valid dataset and classify the sentences. The actual and predicted labels were printed.  
![Alt text](samples.png?raw=true "Sample Outcomes")
