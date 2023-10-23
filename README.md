# Similarity search with FAISS
As part of the preparation in the Workshop, the task of comparing and searching for the most similar products was set. Matching is one of the basic tasks of machine learning, which is found in information retrieval, computer vision, recommendation systems, etc.
As part of the task, the following steps have been completed:

preparation and research of initial data;
selection of the ranking model and its optimal parameters;
evaluation of the model by the accuracy@5 metric;
creating and preparing data for the ml model;
selection of the optimal machine learning model in order to improve the prediction quality of the ranking model;
evaluation of results after the introduction of a machine learning model into the algorithm for searching for similar products.

For the Faiss ranking model, the parameters were selected and the model correctly matched one of the five candidates with an accuracy of 70.9%. At the same time, the time for marking and matching candidates is adequate. When using the Flat index, you can slightly improve the result, but at the same time, the search time for candidates will greatly increase, due to the fact that the model will compare with each candidate in the database separately and with an increase in the database (and they sometimes reach tens and hundreds of GB), the search speed will increase.

Another way to improve the result is to select more candidates. For example, among 100 candidates, the metric will increase to 76.9%, and at 200 it is already 78.3%, then an increase in the number of candidates will cause such an increase as a result. This method is convenient to use with a classification model if the model predicts correctly in more than 90.5% of cases.

The XGBoost classification model was used as such a model. Optimal hyperparameters have been selected for it using the Optuna library. With these hyperparameters, a model of 200 candidates outputs with a probability of 59.8% out of 5 candidates suggests the correct one. With a probability of 65.8% out of 10 candidates chooses 5 with one correct one. Unfortunately, with the existing configuration of the model, the result of the metric deteriorates and there is no point in launching the implementation.
