 To see the development phase commit: first check "dev-main",
Then "main",
Then "bonus part" branches.

For peer evaluation: check "bonus-part"

Cs412 Final Project


Overview
This project consists of 5 main parts which are, Data processing, Text Vectorization, Feature engineering, Correlations investigation & hyperparameter tuning and Model training. 

In the data processing part, html files parsed into data frames. This data frame was divided prompt by prompt and unlike given in project base conversations not only include roles and text was also decided to divide code provided by chat gpt as well. 
Then the data process continued by removing html tags, non asci cleaning, and invalid chat deletion. On the other hand, scores.csv was also cleaned and prepared to be merged into the main dataframe named df.


In the Text vectorization part,  it has been aimed to match the questions with prompts in the dataframe. In order to do that tf-ıdf vectorizer implemented and cosine similarity of vectors has been investigated in order to match the prompts with questions.


In the feature engineering part, features that provided in base code have been kept. Besides new counted features added which put into code2newfetures so that they can be merged into the main dataframe later. These new features consist of; #_hw_statements , Useful to check if the student mentioned about the tasks are for homework in a Machine Learning course. ChatGPT may act accordingly when she knows the tasks will be presented in the academy, Question_statements, the way the student behaves might affect the responses of ChatGPT. #understand_statements, If a students is eager to learn, it is more likely that she will use verbs like "explain". The more willingness to learn, the more likely to get a high grade. And example statements which checks if students ask chat gpt for examples in order to understand the homework better. Another feature that generated was average code length provided by chat gpt. In this feature it has been assumed that longer the code that chat gpt provides to the student, the grade of the student may be higher. Another assumption is that number of imperative sentences given by the student in this part inorder to understand if the sentence is imperative or not spacy nlp model has been implemented. One of the features implemented was similarity of the chat gpt conversation of the student with the students who got 100 from this homework. It can be said that Chats of the students who got 100 from the homework assumed as ground truth and their mean vector calculated by implementing a another tf-ıdf vectorizer. And calculated the cosine similarity between the mean vector of students who got 100  and the student to be checked. This approach also tried with word2vec model however it has been decided to use tf-ıdf model due to its better performance and wider outcome deviation. TF-IDF based similarity  model has been applied to booth prompts and code provided by chat gpt. Furthermore, errors given to chat gpt are , average sentences counted in order to used as new features to dataset. Also we believe that chat gpt would understand the assignment better if the some part of the data set given or explained therefore we checked for some keywords to understand if the student have provided the dataset to chat gpt. Finally we used a little trick specific to one question in homework and we  checked if the student found information gain negative or not and added it as a feature as well.
In  Correlations investigation & hyperparameter tuning part it has applied the knowledge gained in assignment 1 and generated a heatmap and printed the target correlations to observe which features are highly correlated and which ones are not. Inorder to tune hyperparameters gridsearchCV implemented while its basic execution also can be found in the notebook we implemented a bruteforce approach and make sure that GridSearchCV tried each hyper parameter combinations and each scoring method that can be applied to DecisionTreeRegressor. In model training, similar to DecisionTreeRegressor, Gradient Boost and Elastic Net models were tried with different hyperparameters and most suitable ones were selected for training. 



Methodology


1. Data Processing
* Parsing HTML Files:
   * HTML files were parsed into data frames to facilitate further analysis.
   * The data frame was structured to include both roles and text, dividing code provided by ChatGPT along with the prompts.
* Data Cleaning:
   * HTML tags, non-ASCII characters, and invalid chat data were removed during the data processing stage.
   * The scores.csv file was cleaned and prepared for merging with the main data frame, named df.
2. Text Vectorization
* Question-Prompt Matching:
   * The aim was to match questions with prompts in the data frame.
   * Implemented TF-IDF vectorizer to transform text data into numerical vectors.
   * Cosine similarity of vectors was calculated to identify and match prompts with questions effectively.
3. Feature Engineering
* Retaining Base Features:
   * Features provided in the base code were retained for analysis.
* New Features:
   * Additional features were created and stored in code2newfeatures for later merging into the main dataframe.
   * Examples of new features include #_hw_statements, Question_statements, #understand_statements, and average code length.
   * A similarity feature was introduced by comparing the student's conversation with those who scored 100 in the homework, utilizing TF-IDF vectorization.
4. Correlations Investigation & Hyperparameter Tuning
* Correlation Analysis:
   * A heatmap was generated to visually represent the correlations between features.
   * Target correlations were printed to identify highly correlated and less correlated features.
* Hyperparameter Tuning:
   * Applied knowledge from assignment 1 to optimize model performance.
   * Implemented GridSearchCV for DecisionTreeRegressor with a brute-force approach, exploring various hyperparameter combinations and scoring methods.
5. Model Training
* Model Selection:
   * DecisionTreeRegressor, Gradient Boost, and Elastic Net models were considered for training.
* Hyperparameter Optimization:
   * Different hyperparameter combinations were tested for each model.
   * The most suitable hyperparameters were selected based on performance metrics.
* Training Process:
   * The final models were trained using the selected hyperparameters.




Results


Decision Tree
Mean Squared Error: 68.08264977255797
R-squared: -0.4069453811615107











Team Contribution


Ceren Arkaç:
- Contributed at steps: HTML extraction, HTML files dataset preprocessing, scores dataset preprocessing, feature engineering, hyperparameter tuning, model training, PCA,  troubleshooting
Minel Sena Sakarya:
-Contributed at feature engineering and extraction
-Contributed model training and hyperparameter tuning of the models
Ege Sezginer:
-implementation of code2newfetures
-implementation of Correlations investigation & hyperparameter tuning part
-İmplementation of finding the similarity between the prompts of the students who got 100, with            tf-idf approach and with word2vec approach.  
Ahmethan Özcan: 
* HTML extraction
* HTML files preprocessing
* Frequency mapping by word2vec 
* Troubleshooting


Mustafa Kepenek: Attended on the meetings and made research on target variable transformations, implemented normalization
