---
# Description of project
Couldn't access our team presentation? Click this [Google Slide](https://docs.google.com/presentation/d/1T8tc1z_T1wPLYJXC9lYaAKBECdGPwBIS/edit?slide=id.p13#slide=id.p13) link.

### Business problem and context
This is a part of the Practice Project Capston class IS6812 at the University of Utah, David Eccles School of Business. This is my personal notebook for the project, but my team also include Linh Do, Ali Ladha and Sudeeptha Sivarajan. 

This competition originated from [Kaggle](https://www.kaggle.com/competitions/home-credit-default-risk/data). Home Credit is a well-established lender operating primarily in the Southeast Asia region. While the region is developing rapidly, the personal loan market still lags behind that of more developed countries. This gap is largely due to a lack of formal credit history. In many cases, credit has been culturally overlooked or limited to informal arrangements between acquaintances or low-tier individual lenders. This pose as a lucrative market for many large credit lenders, that said if they could solve the problem of managing credit risk.

### Our solution?
This is where our team comes in. With limited data points on borrowers’ credit history, we clean, train, and test a machine learning models that allows Home Credit to reliably expand its services to new borrowers and proactively manage its risk appetite.

### My contribution
I cleaned the application_train, application_test, and previous_application tables by leveraging the cleaning functions developed during our team's EDA work, which made the process much more efficient. I also contributed to creating and using a cross-validation function that allowed us to quickly test various scikit-learn models for accuracy, eliminating the need for the time-consuming process of manually training and testing each model.

---
# The process
### Datasets
<img width="707" alt="image" src="https://github.com/user-attachments/assets/c82e88f9-8293-431d-8a99-b3494e76ad4f" />
The competition provided seven datasets, but for the purpose of our modeling and to optimize both training time and simplicity, we chose to focus on just two: application_train.csv and previous_application.csv.

### Project obstacles
- One of the challenges we encountered was the time-consuming EDA process.
With more than 200 attributes across all tables, we spent a lot of time feature engineering and manipulating each attribute without performing any feature selection. This really slowed down the team's momentum and introduced a lot of noise — non-useful information that made it harder to predict whether a borrower would default.

- Another challenge we faced was the way we handled aggregation before joining tables.
We started by joining from the furthest datasets back into the main table, application_train. After multiple rounds of aggregation and changes to primary keys, the data became increasingly watered down, resulting in an unfocused master table filled with obscure noise and missing rows. This significantly increased training time, aggregation time, and overall complexity, yet provided almost no predictive power — accuracy on downsampled data hovered around 50%. Then we switched up our strategy, started with the main table (application_train) and then gradually introduced additional tables only when necessary. This have minimized noise and allowed us to stop adding more data once accuracy improvements became negligible.

---
# Future Analysis and outcome
### Outcome
Our champion model is a CatBoost classifier, which achieved an accuracy of 70% on the training dataset and a Kaggle score of approximately 70.

### Future Analysis
- More data points to consider?
Although using only two datasets was part of our strategy, I’d love to take this project further for Home Credit. Rather than stopping at a machine learning model that predicts default risk for new customers, I envision expanding it to include models tailored for existing customers and those with established credit histories. These next models could be seamlessly integrated into every credit application and become an inseparable part of Home Credit’s lending process.
 
- Leverage different metrics for success?
Even though accuracy was acceptable and easy to explain, I couldn’t help but envision using other metrics that better reflect the true goal of the competition: identifying default borrowers. In this context, metrics like precision, recall, or a balanced metric such as the F1-score would more effectively capture the business objective. Additionally, I’d be interested in exploring metrics like ROC-AUC, which offer deeper insight into the model's performance across various classification thresholds.

### Learned from this?
- Function, function, function!
When I first started this competition, I barely used functions in my notebook. This made my EDA process and the application of models to the test set inconsistent, difficult to manage and overall a nightmare for anyone who try to make sense of my code. However, in this final notebook, embracing the use of functions made managing datasets and training workflows much smoother. Going forward, I plan to take full advantage of this modularity by building reusable function files that can be easily applied to future projects.

- I didn't loved cross validation enough!
Back in my original notebook, I was training each machine learning model manually—one at a time—then testing each on the test set with hand-picked parameters. It was time-consuming, and honestly, the results sometimes felt random. Each model could take hours, and doing this repeatedly really slowed me down. To make things more efficient, I created a cross-validation function that could work with any model from the sklearn library. This made it much easier to train and test consistently, all in one place. It also gave me more confidence in my results, knowing they were based on cross-validation instead of just a single train-test split.

 
