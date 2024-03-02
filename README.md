# P8451_HW7_ML

In class today, we worked on a Group Exercise to sketch out an analytic pipeline to predict readmission for myocardial infarction. In the assignment, you will implement your pipeline (or a simplified version of it) using a sample dataset.

The dataset (mi.data.final) consists of  an ID variable, 14 features describing clinical tests and comorbidities, and an indicator for whether the individual was readmitted to the hospital within 30 days of discharge.

The variables are as follows:

ID: identifier

Age: age at initial MI (years)

Sex: Reported by patient 0-Male, 1-Female, 2-Non-binary/Other

sodium: serum sodium (mmol/L)

ALT: liver enzymes (IU/L)

WBC: white blood cell count (billions/L)

ESR: erythrocyte sedimentation rate

SBP: systolic blood pressure at intake (mmHg)

DBP: diastolic blood pressure at intake (mmHg)

Pulm.adema: Pulmonary adema (1=Yes, 0=No)

FC: functional class of angina pectoris in the last year

1: there is no angina pectoris 
2: I FC 
3: II FC 
4: III FC 
5: IV FC 
Arrythmia: Presence of arrythmia (1=Yes, 0=No)

Diab: Presence of diabetes (1=Yes, 0=No)

Obesity: Presence of obesity (1=Yes, 0=No)

Asthma: Presence of asthma (1=Yes, 0=No)

readmission: Readmitted to hospital within 30 days (1=Yes, 0=No)

For this assignment, you will implement the pipeline you sketched out with your group. As a reminder, your pipeline should include tasks for data preparation, any partitioning or resampling you deem necessary, any tuning of hyperparameters, and explicit evaluation metrics you will examine in order to choose your optimal algorithm. You can choose to examine different algorithms than elastic net and random forest, but you must compare at least two algorithms and one should be an ensemble algorithm.

You will turn in a knit document that shows both code and output for your pipeline. This should include the evaluation metrics used to compare algorithms,  the final evaluation metrics used to report performance of the final model and any generated output detailing the features most important for the prediction. You can continue to work together in groups, but each individual must turn in their own knit document.









mi = mi |> mutate(
  sex = recode(sex,"0" = "Male", "1" = "Female", "2" = "Non-binary/Other"),
  pulm_adema = recode(pulm_adema, "1" = "Yes", "0" = "No"),
  fc = recode(fc, "0" = "there is no angina pectoris","1" = "I FC", "2" = "II FC", "3" = "III FC", "4"= "IV FC"),
  arry = recode(arr, "1" = "Yes", "0" = "No"),
  diab = recode(diab, "1" = "Yes", "0" = "No"),
  obesity = recode(obesity, "1" = "Yes", "0" = "No"),
  asthma = recode(asthma, "1" = "Yes", "0" = "No"),
  readmission = recode(readmission, "1" = "Yes", "0" = "No"))