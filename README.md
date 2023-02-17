# Data_science
# Import pandas so you can read the Excel file.
import pandas as pd
#Use below command to read the Excel
df = pd.read_excel("Acct Statement_XX3609_16022023 (1).xls")
#Fillna is used to make all NaN values to 0.
df = df.fillna(0)
#print Dataframe
print(df)

