# CAP5771FinalProject
Repo for the Fall 2024 Text and Data Mining course at Florida Polytechnic University.

Christian Crosser
Contents:

    -- Datasets:

        -- nfr.csv: Dataset of software requirements(requirements) and their classified label(reqLabel)

    -- Preprocessing.py:

        -- Description: Contains the preprocessing functions that can be used in other modules for preprocessing functions. Functions split by ### Function Title ### comments.
                        Includes all needed imports for each function when using function in a program.

    -- multipleMLModels.py:

        -- Description: Same functionality as singleSVMModel but with multiple models for comparison.
        
        Models Compared:

                - Random Forest

                - Multinomial Naive Bayes

                - Logistic Regression

                - Support Vector Machine

        Possible Enhancements: Metrics and analysis of comparison between model performance.

    -- singleSVMModel:

        -- Description: Single Support Vector Machine model being trained and tested on a set of requirements with two columns, requirements and reqLabel. 

        Steps:
            - Data Preprocessing:
                - The CSV file containing the software requirements data is read into a DataFrame (df).
                - The 'requirement' column is extracted as features (X) and the 'reqLabel' column as   labels (y).

            - Data Augmentation:
                - Function synonym_replacement is defined to perform synonym replacement data augmentation on requirements data.
                - The get_synonyms function retrieves synonyms for a given word from WordNet.
                - The minority class is identified in the labels (y) to perform data augmentation only on the minority class.
                - For each text sample in the minority class, synonyms are replaced to generate augmented samples.
                - Augmented features (X) and labels (y) are updated with the augmented data.

            - Feature Extraction:
                - The TF-IDF vectorizer is initialized (tfidf_vectorizer) with a maximum of 1000 features.
                - Text features (X) are transformed into TF-IDF feature vectors (X_tfidf).

            - Train/Test Split:
                - The dataset is split into training and testing sets using a 80-20 split ratio.
                - The training set (X_train, y_train) and testing set (X_test, y_test) are obtained.

            - Model Training and Evaluation:
                - An SVM classifier (svm_classifier) with a linear kernel is initialized and trained on the training data.
                - The trained classifier is used to make predictions on the testing data.
                - The classification report, including precision, recall, and F1-score, is printed to evaluate the classifier's performance.

            - Prediction Example:
                - New requirements are defined as a list (new_requirements).
                - Each requirement undergoes synonym replacement data augmentation to create augmented requirements.
                - The TF-IDF vectorizer transforms the augmented requirements into TF-IDF feature vectors.
                - The SVM classifier predicts the labels for the augmented requirements.
                - The original requirements along with their predicted labels are printed.

    -- ResultsComparison.py
        
        -- Description: Used to compare two data sets and give similarity scores. Used as additional validation and testing for the NLP models accuracy.

