# Learning Log

---

## 2026-10-27
Loaded the csv to the pandas dataframe. Analzye the data shapes. There is almost 73% of customer stayed and 26% chrun. I have checked for the missing value of the dataset for standard data cleaning and pre-process strategy need to be applied. I cleaned the data fix the data type issue and missing value. And turn our target var "churn" to 1 and 0 for model training.

## 2026-10-28
From the EDA section the histogram clearly show that it have lot of new customers. They charges with monthly and some are charges lot, most customers have paid under $2,000 in total.A newer customer on a month-to-month contract, with fiber internet, paying by electronic check, without tech support, and with a higher monthly bill. For preparing data I make a another copy and merge the redundant categories into "No". Then I have eparate the inputs (X) from the answer (y). Spliting the dataset in 80% train and 20% test. For baseline model as I use LR which is vulnarable for high numerical diffrence of scale so StandardScaling is need. From the actual result as LR model well fited but 51% precision. I think as I was used class_weight="balanced", which told the model missing a churner is worse than a false alarm.That is why recall is high and precision is lower

## 2026-10-29
I have tested three models, logistic regression, random forest, and gradient boosting. All three scored almost the same (AUC about 0.845), so none is clearly better. I used gradient boosting to find the most important features because it provides a built-in importance score. Logistic regression is still a good choice when it is needed for a simple, easy-to-explain model.Random forest and gradient boosting performed no better than logistic regression (AUC 0.844-0.847 vs 0.845), so the simpler, more interpretable model is preferred. Customers who are new, on a month-to-month contract, using fiber internet and paying by electronic check are the most likely to leave. A simple model can find these customers reasonably well (AUC about 0.84). The company should focus retention efforts on this group, for example by encouraging longer contracts and automatic payment.