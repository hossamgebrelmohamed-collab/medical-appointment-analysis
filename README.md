🏥 Medical Appointment No-Show Prediction


A complete end-to-end Data Science project to predict which patients are likely to miss their medical appointments.




📌 Problem Statement

Hospitals lose significant time and resources when patients don't show up for appointments. This project analyzes 110,527 medical appointments from Brazil to identify patterns behind patient no-shows and build a predictive model to help hospitals take proactive action.

Key Question: Can we predict whether a patient will miss their appointment — before the appointment date?


📊 Dataset


Source: Kaggle - Medical Appointment No Shows
File: KaggleV2-May-2016.csv
Size: 110,527 rows × 14 columns
No missing values


Key Columns

ColumnDescriptionPatientIdUnique patient identifierAppointmentIDUnique appointment identifierGenderPatient gender (M/F)ScheduledDayDate the appointment was bookedAppointmentDayDate of the actual appointmentAgePatient ageNeighbourhoodPatient locationScholarshipWhether patient receives social welfare (0/1)HipertensionHypertension diagnosis (0/1)DiabetesDiabetes diagnosis (0/1)SMS_receivedWhether a reminder SMS was sent (0/1)No-showTarget variable — "Yes" = patient missed appointment


🔍 Key Findings (EDA)

No-Show Rate


79.8% of patients showed up ✅
20.2% of patients missed their appointment ❌ — that's 1 in every 5 patients!


Age vs No-Show


Young adults (15–35) have the highest no-show rate
Elderly patients (60+) are significantly more likely to attend


Waiting Time vs No-Show

GroupAvg. Waiting DaysShowed up14.0 daysMissed appointment16.2 days

→ Longer waiting time = higher chance of no-show


⚙️ Feature Engineering

Created a new feature: WaitingDays — the number of days between booking and the appointment date.

pythondf['WaitingDays'] = (df['AppointmentDay'] - df['ScheduledDay']).dt.days


🤖 Machine Learning Model

Algorithm: Logistic Regression (scikit-learn)

Preprocessing


Converted No_show to binary (0 = showed up, 1 = missed)
Converted Gender to binary (0 = Male, 1 = Female)
Applied StandardScaler for feature normalization
Used class_weight='balanced' to handle the imbalanced dataset (80/20 split)


Results

MetricValueOverall Accuracy55%Recall (No-show detection)57%F1-Score (No-show class)0.42


⚠️ Accuracy was intentionally traded for higher Recall — we want to catch as many no-show patients as possible, even at the cost of some false positives.




📈 Feature Importance

Top 3 factors influencing no-show prediction:


🏆 Age — Younger patients are more likely to miss appointments
⏳ WaitingDays — Longer wait = higher no-show risk
📱 SMS_received — Reminder messages have a measurable impact on attendance



💡 Business Recommendations

Based on the model's insights, hospitals can:


Send extra SMS reminders to patients whose waiting time exceeds 15 days
Target young adult patients (15–35) with proactive follow-up calls
Prioritize reminder campaigns for high-risk patient segments



🛠️ Tools & Libraries


Python 3
pandas — data loading and manipulation
scikit-learn — machine learning
seaborn & matplotlib — data visualization
Google Colab — development environment



🗂️ Project Structure

medical-no-show/
│
├── KaggleV2-May-2016.csv       # Raw dataset
├── medical_noshow_analysis.ipynb  # Main Colab notebook
└── README.md                   # This file


🚀 How to Run


Open Google Colab
Upload KaggleV2-May-2016.csv
Run all cells in medical_noshow_analysis.ipynb



👤 Author

Hosam


<img width="1288" height="816" alt="download" src="https://github.com/user-attachments/assets/d215b8aa-c104-4333-abf9-0ad12c26f06a" />
<img width="990" height="590" alt="download (1)" src="https://github.com/user-attachments/assets/696ff1cd-c70a-4769-8cad-a835762afe7f" />


Data Science Learner | End-to-End Project


📄 License

This project is open source and available under the MIT License.
