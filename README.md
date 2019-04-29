# Language-Identification
Language identification at sentence as well as word level in both monolingual as well as code-mixed bilingual texts.

## Task-1 ##
- Our task was focussed on developing a model for Language Identification service that returns the language code of the language in which the text is written. We had datsets from three languages 
Spanish (ES), Portuguese (PT) and English (EN) and had to predict sample texts in the mention 3 languages.

## Data ##
- We had 3 datasets (en, es, pt) with 2.6Mn lines in each file.
- We cannot process such a large file at once hence we used random sampler and got 20,000 sampes from all the three files. (**command: shuf -n 20000 input_file > output_file**)
- We gave languaegs ID's as {En: 0, Es: 1, Pt: 2} respectively.
- Please contact us for accessing the data.

----------------------------------------------------------------------

## Pre-Processing ##
- All the texts were converted to lower case.
- Removal of punctuations.
- All the digits were removed from the text sentences.
- Series of contiguous white spaces were replaced by single space.
- Removal of hyperlinks

#### Representation ####
- We used **TfidfVectorizer** for representing the text in our corpus.
-----------------------------------------------------------------------

## Data split ##
- We splitted the data into 80/20 for trianing and testing at the same time keeping in mind to have similar number of instances for all the three langauges in test too.
- **Train dataset**: {En: 14197, Es: 15279, Pt: 15550}
- **Test dataset**: {En: 4178, Es: 3503, Pt: 3576}

-----------------------------------------------------------------------

## ML Model ##
- Used sklearn for importing the models.
- We have used **LogisticRegression** algorithm for our classification with **solver='lbfgs'**.

------------------------------------------------------------------------

## Results ##

- Our system achieved an accuracy of **93%**.
- The confusion matrix for the result is as below:

    |     |  0  |  1  |  2  |
    |-----|--------|:------:|:------:|
    |  **0**  | 3620    |  299   |  259   |
    |  **1**  | 38    |   3388  | 77    |
    |  **2**  |   22  | 71    | 3483    |



- The Classification report is as below:

    |      | precision | recall | f1-score | support |
    | ---- |:---------:|:------:|:--------:|:-------:|
    |  **En**  |     0.98  |    0.87|      0.92|      4178|
    |  **Es**  |     0.90  |    0.97|      0.93|      3503|
    |  **Pt**  |     0.91  |    0.97|      0.94|      3576|
   
   ------------------------------------------------------------------- 
    
## Running the script and results ##

- To run our model the command is as below:
- **python3 script_task1.py data.en data.es data.pt langid.test**
- In the above command 1st agument should be english data file, 2nd as spanish 3rd as potruguese and 4th as the testing file.
- **test_results.txt** will contain the language label predicted for the **langid.test** file once ran on our model.
- test_results.txt above contains the output on the langid.tets file provided for us to test.
- Tags here are numerical **0: en, 1: es, 2: pt**

---------------------------------------------------------------------

