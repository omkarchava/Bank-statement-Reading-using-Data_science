# Data_science
#Use Anaconda and use Jupyter extension to run this code

####################################################################################
# Import pandas so you can read the Excel file.
import pandas as pd

#Use below command to read the Excel

df = pd.read_excel("Acct Statement_XX3609_16022023 (1).xls")
#Fillna is used to make all NaN values to 0.

df = df.fillna(0)
#print Dataframe

print(df)

######################################################################################

#Intilize the values in order to get sum of them.

Debited=0
credited=0
EMI=0
Below_100=0
Between_100_to_300=0
Between_300_to_500=0
Between_500_to_1000=0

# Iterate all rows using DataFrame.iterrows()

for index, row in df.iterrows():

    # To print all the row values 
    print (index,row["Withdrawal Amt."],row["Deposit Amt."])
    
    #Calculate total Credidted and Debidted amount and Saving.
    Debited=Debited+(row["Withdrawal Amt."])
    credited=credited+(row["Deposit Amt."])
    saving=(credited-Debited)
    
    #calculate EMI amount with exact monthly EMI amount.
    if row["Withdrawal Amt."]==12842.11:
        EMI=EMI+row["Withdrawal Amt."]
        
    #Calculate perticular amount of Expenses.
    if row["Withdrawal Amt."]<=1000 and row["Withdrawal Amt."]>500 :
        Between_500_to_1000+=row["Withdrawal Amt."]
    if row["Withdrawal Amt."]<=500 and  row["Withdrawal Amt."]>300:
        Between_300_to_500+=row["Withdrawal Amt."]
    if row["Withdrawal Amt."]<=300 and row["Withdrawal Amt."]>100:
        Between_100_to_300+=row["Withdrawal Amt."]
    if row["Withdrawal Amt."]<=100:
        Below_100+=row["Withdrawal Amt."]
    
    
    
        
        
#Printing all the claculated values
print("Debited",Debited)
print("credited",credited)
print("EMI",EMI)
print("Below_100",Below_100)
print("Between_100_to_300",Between_100_to_300)
print("Between_300_to_500",Between_300_to_500)
print("Between_500_to_1000",Between_500_to_1000)
Unwanted_expenses =Below_100+Between_100_to_300+Between_300_to_500+Between_500_to_1000

#Negative Values will not be handled in Pie chart so we need to check the saving. if saving is negative then make it positive.
if saving<0:
    saving=-(credited-Debited)
    print("Total Saving "+"Rs."+str(saving)+"/-")
    
#################################################################################################################################
#Import matplotlib with pyplot extension

import matplotlib.pyplot as plt
#for jupyter use below function.
%matplotlib inline


##################################################################################################################################
#In sizes array give the values that we calculated as X axis and in labels give the name as Y axis.
sizes = [Debited, credited, saving,EMI,Below_100,Between_100_to_300,Between_300_to_500,Between_500_to_1000]
labels = 'Debited', 'credited', 'Saving','EMI',"Below_100","Between_100_to_300","Between_300_to_500","Between_500_to_1000"

#Use below commands to Highlight the labels in pie chart
plt.pie(sizes,labels = labels)
plt.pie(sizes, autopct='%1.1f%%')

#Headline of the Pie chart
plt.title('Survival from 2nd of November to 31st of January')
plt.axis('equal')

# Show the pie chart
plt.show()
 #print all the values below pie chart
print("Debited "+"Rs."+str(Debited)+"/-")
print("credited "+"Rs."+str(credited)+"/-")
print("EMI "+"Rs."+str(EMI)+"/-")
print("Below_100 "+"Rs."+str(Below_100)+"/-")
print("Between_100_to_300 "+"Rs."+str(Between_100_to_300)+"/-")
print("Between_300_to_500 "+"Rs."+str(Between_300_to_500)+"/-")
print("Between_500_to_1000 "+"Rs."+str(Between_500_to_1000)+"/-")
print("Unwanted_expenses "+"Rs."+str(Unwanted_expenses)+"/-")
if saving<0:
    saving=-(credited-Debited)
print("Total Saving "+"Rs."+str(saving)+"/-")























