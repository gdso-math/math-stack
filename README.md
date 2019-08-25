# Math Equation Classifier

Discription
-------
Stack Exchange is a network of question-and-answer websites. You might hear about StackOverflow. It’s one of the most popular sites visited in this network. There are a lot of other communities in this network, each of which covers a specific topic and users can ask and answer questions there. 

In the website, when users want to ask questions, one thing they need to do is to set tags for theirs questions as you can see in the picture. ![Image](https://github.com/gdso-math/math-stack/blob/yishuang/images/StackExchange.png) Users can also save some tags they are interested or good at so that they can answer those questions as soon as possible. So labelling the correct tags become really important to match askers and answers. However, sometimes users find themselves hard to describe their questions in several tags or even label tags incorrectly. So here comes our idea to design an automatic tag recommendation system when users are inputting questions to simplify the question process. This become a text classification problem.

As you can see in the first example, we notice that it only includes words, we can use **bag of words** model to transform each text into a numerical representation and use some machine learning algorithm to achieve that. Like the first question, there are keywords like “organic chemistry” and “geometrical”, so it’s easy for the computer to give a suitable recommendation. But what if we have a question with a lot of equations and very few keywords like the second example? How can we extract the keyword “organic-chemistry”? It motivates us to do the equation classification, which can help StackExchange  improve the tag labeling in the future.

Get started
------
These instructions will get you a copy of the project up and running on your local machine.
- Clone this Github repo into your local machine.
- You will need to have the following packages install: p7zip, gensim
- You need to run the following files and follow the tutorial inside. 
  - ***00_data_extraction.ipynb*** a script to extract data from StackExchange
  - ***01_data_preprocessing.ipynb*** a script to extract equations from body and do some preprocessing
  - ***03_tag_clustering.ipynb*** a script to create sub-labels and regroup data
  - ***04_sequence_clf_cluster_label.ipynb*** our NLP model based on character of LaTeX (GPU)
  - ***05_test_image_generation_cluster.ipynb*** convert LaTeX equations into images and resizing
  - ***05_img_filtering_invalid.ipynb*** filter some failed/invalid images
  - ***05_cv_clf.ipynb our CV model based on images*** (GPU)
  
Other Notebooks
-------
- ***02_exploratory_data_analysis.ipynb*** we want to get some insights of the equations but we failed to find certain pattern.
- ***03_tag_statistics.ipynb*** we calculate the coefficients of two equations and the conditional probability of two equations appear together to get some insights of tag combinations.
- ***03_tag_word2vec.ipynb*** We combine equations and corresponding tags as a sentence, then use the Word2Vec idea to check the similarity of each pair of equations.
- ***04_show_confusion_matrix.ipynb*** Due to different version, when I run ***04_sequence_clf_cluster_label.ipynb*** on GCP, the confusion matrix plotting will always have a problem. So I replot the confusion matrix in my local machine. 

Result
------
- NLP for three subjects: physics, chemistry and biology
![Image](https://github.com/gdso-math/math-stack/blob/yishuang/images/nlp_result.png)
- NLP for five sub-labels: physics-relativity, physics-quantum, chemistry-organic, chemistry-inorganic, biology
![Image](https://github.com/gdso-math/math-stack/blob/yishuang/images/nlp_cluster.png)
- CV accuracy: 0.9 for ResNet-50
