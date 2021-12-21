# CCOM-Final-project
This will be our final proyect for the data science class, in which we will analyze data collected from a high conflict platform-mediated avoidance assay.

# Purpose
For this proyect, our aim was to create a code that could reorganize, clean and plot data obtained from a behavioral experiment. In this experiment, mice were exposed to an aversive and a rewarding stimulus simultaneously, and a program measured how long it took for them to mount a platform. With this code we wanted to be able reduce the time-consuming and error-prone nature of manual data analysis, and be able to manipulate an extensive data set with ease.

Since we didn't get to the point in which we could plot with the regular excel document, we created a simpler version for the plotting, but wrote the code with the original version in mind. 

# Code for plotting:
### First import the necessary packages
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import matplotlib as mpl
import scipy.stats


### Then load files and creat the dataframes; necessary files are: Wildtypebehx1.3.xlsx and WILDTYPE BEHAVIOR
newxl=pd.ExcelFile(r'C:\Users\Chris\Documents\Wildtypebehx1.3.xlsx')
All=pd.read_excel(newxl,index_col='Time')
Alldf=pd.DataFrame(All)
Alldf

### Afterwards create new dataframes with the columns of interest using df.iloc
Example:
lo=All.iloc[:,0:10]
hi=All.iloc[:,10:20]

### Then pick the rows of interest using df.loc
Example:
lon=lo.loc[-4.966617:25.033083]
hin=hi.loc[-4.966617:25.033083]

### Drop the rows with NaN values as index again using .loc in conjuction with dropna()
Example:
lonf=lon.loc[lon.index.dropna()]
hinf=hin.loc[hin.index.dropna()]

### Create lists of colors for our plots
g=("lightgrey",'lightgray','silver','darkgrey','darkgray','grey','gray','dimgrey','dimgray','black')
m=("lightblue","cyan","darkcyan")
f=("lightpink","pink","crimson")

# And finally create the linegraphs to visualize the data
lonf.plot(xlabel='Time(s)',ylabel="Time on platform",title="Low conflict training",color=g)
hinf.plot(xlabel='Time(s)',ylabel="Time on platform",title="High conflict training", color=g)

ax = himnf.plot(color=m)

hifnf.plot(xlabel='Time(s)',ylabel="Time on platform",title="Males vs Females in conflict training",ax=ax, color=f)
scipy.stats.ttest_ind(himnf['Hi10m'], hifnf['Hi10f'], equal_var=False)
axs = Tmnf.plot(color=m)

Tfnf.plot(xlabel='Time(s)',ylabel="Time on platform",title="Males vs Females in conflict testing",ax=axs, color=f)
scipy.stats.ttest_ind(Tmnf['TM5'], Tfnf['TF5'], equal_var=False)

# Google collab
The code in google collab looks a little bit different near the end, but it's still the same code. For collab remember to 1) load the files and 2) change the file paths to the file names.

# Link to video explaining the project and code
Google drive: 
