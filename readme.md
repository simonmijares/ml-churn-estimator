# Churn ML Estimator
#### by Simón Mijares Pachano

## Project Definition
### Project Overview

Traditionally the base client grow rate was one of the main KPI in a service business, but currently is known that it does not matter if those clients will not stay long enough to develop some fidelity to your services. In fact, acquire a new customer cost five times more than maintain an existing client .
For this reason, monitor your levels of churn (or attrition) is important, more in current times when the pandemic took most people out of their regular routine, struggling with income stability, heath issues among many others. Not only clients are having difficult times, but the companies are also having difficulties in different stages of its own flows. Transport, distribution, or the sole challenge of working remote to name a few examples.
The Telco’s are one case, and it will be the case of study for this project. The possible variables of study are certainly multiples but all orbit around the same concept, technical variables, commercial variables, interaction variables and commitment with the services variables. These will be explained bellow.
As part of this work, I will try to obtain a model in Sagemaker capable of predict when a client will most probably churn, so the company could try to reach him and try to keep him happy.
We will try to compare random forests with a neural networks model since these are popular proved methods to predict churn based on historical data .

### Dataset
•	**Churn**: 1 if customer cancelled service, 0 if not. This will be the variable to predict.

•	**AccountWeeks**: number of weeks customer has had active account. The first weeks after a service installation could imply high call rates to customer services, with the number of week we could identify this case.

•	**ContractRenewal**: 1 if customer recently renewed contract, 0 if not. If the user have a yearly contract, might be tempted to look to a different provider close to the end.

•	**DataPlan**: 1 if customer has data plan, 0 if not. Usually, the pay as you go plans have a quite different behavior compared to user with a data plan.

•	**DataUsage**: gigabytes of monthly data usage. The user might not be using the service or barely using it. This probably will lead to a churned user.

•	**CustServCalls**: number of calls into customer service. The more the user call, the more upset it might be.

•	**DayMins**: average daytime minutes per month. Like the DataUsage, this is a feature to make a profile of the user.

•	**DayCalls**: average number of daytime calls. Another feature to help make a profile of the user.

•	**MonthlyCharge**: average monthly bill. Also, to build a profile of the user based on what the user is been charged. The minimal plan user is quite different to the more premium one.

•	**OverageFee**: largest overage fee in last 12 months. The user might need a different plan to prevent overage.

## Installation

For the project the only packet needed outside the standards 
```bash
!pip install pandas-profiling[notebook]
```

## Dataset adquisition
Based on https://www.analyticsvidhya.com/blog/2021/04/how-to-download-kaggle-datasets-using-jupyter-notebook/

1. First, go to Kaggle and you will land on the Kaggle homepage.

2. Sign up or Sign in with required credentials.

3. Install opendatasets:
```bash
!pip install opendatasets
```

4. Import the module
```python
import opendatasets as od
```

5. Download the package with:

```python
od.download("https://www.kaggle.com/barun2104/telecom-churn")
```
6. On executing the above line, it will prompt for Kaggle username. Kaggle username can be fetched from the Account tab of the My Profile section

7. On entering the username, it will prompt for Kaggle Key. Again, go to the account tab of the My Profile section and click on Create New API Token. This will download a kaggle.json file.

8. On opening this file, you will find the username and key in it. Copy the key and paste it into the prompted Jupyter Notebook cell. The content of the downloaded file would look like this:
```json
{"username":<KAGGLE USERNAME>,"key":"<KAGGLE KEY>"}
```

9. A progress bar will show if the dataset is downloaded completely or not.

10. After successful completion of the download, a folder will be created in the current working directory of your Jupyter Notebook. This folder contains our dataset.

**Note**
If you prefer the kaggle package is also an option:
```python
!pip install kaggle
!kaggle datasets download -d barun2104/telecom-churn
```

**Other libraries**: pandas, numpy, pandas_profiling, os, sklearn.model_selection.train_test_split, boto3, sagemaker, sagemaker.image_uris, sklearn.metrics.accuracy_score, sklearn.metrics.confusion_matrix, sagemaker.LinearLearner, 

## Use
There are two notebooks included, both are almost identically. The only difference is the way the data is partitioned. In one case is identified as 60-20-20 for 60% training, 20% test, 20% validation. The second case will be 80% training, 20% test/validation.

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.