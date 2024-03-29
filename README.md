﻿# complaintsML
This repository contains ipynb notebook for text classification of consumer complaints [dataset](https://catalog.data.gov/dataset/consumer-complaint-database)

Text classification is done based on the text data provided as Consumer complaint narrative into 4 categories
```
0 Credit reporting, repair, or other
1 Debt collection
2 Consumer Loan
3 Mortgage
```

# EDA
The target column has 21 classes
![image](https://github.com/vinayak5002/complaintsML/assets/82216732/eac7d8d5-fd81-4787-80e9-29d93a3a0dd3)

We have to makes all these into 4 classes
![image](https://github.com/vinayak5002/complaintsML/assets/82216732/c2969e65-0858-4118-812a-9a3a8e38130d)

Since the distribution is highly imbalnce, we can downsample majority classt to make the distribution more balanced
![image](https://github.com/vinayak5002/complaintsML/assets/82216732/539bb057-3b8f-4af5-a764-8f5af71cc895)

# Feature extraction
We can use bag of words approach. Generate TF-IDF vectors to generate features for supervised learning
```
vectorizer = TfidfVectorizer()
X = vectorizer.fit_transform(X)
```

# Model selection and evaluation
## Multinomial Navie bayes
![image](https://github.com/vinayak5002/complaintsML/assets/82216732/ae7f9788-2575-4f0c-a1a3-619265ddc811)
Overall inference:
- Good performance for class 0
- Decent performance for class 1
- Class 2: Model predicts as class 2 many times but some of the times, its wrong
- Class 3: Same as class 2 but number of times model is wrong is less

Overall decent performance

There is imbalance between precision and recalls of class 2 and 3

## Random forest classifier
![image](https://github.com/vinayak5002/complaintsML/assets/82216732/72473edb-8256-4238-b12d-abeeeebbb9ee)
Overall inference:
- Similar to previous model, high precision and reasonable recall
- Decent performance for class 1, but precision reduces a little
- Class 2: Model predicts as class 2 many times but some of the times, its wrong
- Class 3: Same as class 2 but number of times model is wrong is less, but better balance between precision and recall

Overall decent perfomance

There is imbalance between precision and recalls of class 2 and 3. But imbalance has improved a little bit

## Support Vector Machine
![image](https://github.com/vinayak5002/complaintsML/assets/82216732/f2af270e-d494-40d0-92b8-6397b643185b)
Overall inference:
- Good performance for class 0
- Better performance for class 1
- Class 2: Model predicts as class 2 many times but some of the times, its wrong
    - Overall performance increased, but still imbalance is there
- Class 3: high f1 score with good balance between precision and recall
    - Best among all 3 models

Overall all classes except class 2 have good overall score

SVM has significantly better performance on class 3 among other models

Class 2 accuracy is improved but still imbalnced precision and recall
