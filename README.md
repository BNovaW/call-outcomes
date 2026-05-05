# call-outcomes
This is code created for a class project focused on public data analysis.

## Required libraries
- pandas
- glob
- seaborn
- matplotlib
- sklearn

## *Step 1 Data Cleaning*

For this step there are multiple csv files loaded in and cleaned and concatinated in different ways (see Cleaning.ipynb).

### File Path
├── MCSLC.xlsx
├── SPD Close Codes.csv
├── SPD Designator Notes.csv
├── 2015-2025 Calls for Service/
│   ├── 2015 SPD Calls for Service.csv
│   ├── ...
│   └── 2025 SPD Calls for Service.csv
├── 2015-2025 Responding Units/
│   ├── 2015-2025 SPD Responding Units.xlsx - 2015.csv
│   ├── ...
│   └── 2015-2025 SPD Responding Units.xlsx - 2025.csv
├── 2015-2025 SPD Calls with Close Codes/
│   ├── 2015-2025 SPD Calls with Close Codes.xlsx - 2015.csv
│   ├── ...
│   └── 2015-2025 SPD Calls with Close Codes.xlsx - 2025.csv
└── Eugene_CAD_data_noloc/
    ├── EugeneCAD2015noloc.csv
    ├── ...
    └── EugeneCAD2025noloc.csv

Steps:
- load data files
- subsection dataframes to necessary columns only 
- rename/update values in columns to be consistant
- Do the above steps for MCSLC, Eugene, and Springfield data then combine MCSLC with the Eugene and Springfile data finishing with dataframes "eugene" and "springfield".


## *Step 2 Analysis*

*pt 1) Exploratory analysis:*

Using pandas compute general frequencies of each variable in the closed_as column. Specifically focus on hospital transportations and arrests as well as splitting frequencies by agency and normalizing those counts. Finally, compare change over time of hospital and arrest outcomes.  It’s important to mark at least roughly where MCSLC started activities in Eugene and when CAHOOTS stopped services because these are our main points of interest in time to measure if there has been a difference between agencies.

  Input: eugene and springfield dataframes
  Output: printed statements for the time range and how many counts of HOSPITAL or ARREST in the "closed_as" column occured by year. Also has graphs to visualize the change in counts between agencied by year. 

*pt 2) Logistic Regression*

necessary packages
- from sklearn.linear_model import LogisticRegression
- from sklearn.model_selection import train_test_split
- from sklearn.metrics import accuracy_score

- Fit a logistic regression model to estimate how agency (EPD, SPD, MCSLC, CAHOOTS) influences the likelihood of an outcome (arrest vs hospital). It is important to control for time (year/month).
- Then, extract the odds ratio per agency, p-value and confidence interval of agency effects, and change in predicted probability by agency
- Also, evaluate the models performance using classification accuracy, a confision matrix, and ROC-AUC score.

*pt 3) work in progress...*

...

*pt 4) differences in differences*
- use the springfield data as a control against the eugene data to see if there is a statistical significance between CAHOOTS being active or not in Eugene. 
