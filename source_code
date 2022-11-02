import numpy as np
import pandas as pd

#import data from the web
df = pd.read_csv('https://covid19.who.int/WHO-COVID-19-global-data.csv')
new_cases = df['New_cases'].tolist() 
country_code = df['Country_code'].tolist()

VN = [] #this array stores weekly new COVID-19 cases in Vietnam from 01/01/2020 to 01/11/2022

days = 1036  #caculate data of 1036 days, from 01/01/2020 to 01/11/2022
leng = len(country_code) 

#import data to 'VN' array
index = 0 #pointer to 'country_code' array
current_day = 0 
r,sum = 0,0 #used to check new cases in a week

while index < leng and current_day <= days:
    if country_code[index] == 'VN':
        current_day += 1
        r += 1
        sum += new_cases[index]
    if r == 7:
        r = 0
        VN.append(sum)
        sum = 0
    index += 1

#assign label to the data
labels = []
for i in range(len(VN)):
    if VN[i] < 20000:
        labels.append(0)
    elif VN[i] < 50000:
        labels.append(1)
    elif VN[i] < 150000:
        labels.append(2)
    else:
        labels.append(3)

#transition frequency table
fre_table = [[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]]
for i in range(1,len(VN)):
    row = labels[i-1]
    column = labels[i]
    fre_table[row][column] += 1
    
for i in range(4): 
    for j in range(4):
        print(fre_table[i][j],end=' ')
    print("\n")
