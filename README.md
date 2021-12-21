# CCOM-Final-proyect
This will be our final proyect for the data science class, in which we will analyze data collected from a high conflict platform=mediated avoidance assay.

# Purpose
For this proyect, our aim was to create a code that could reorganize, clean and plot data obtained from a behavioral experiment. In this experiment, mice were exposed to an aversive and a rewarding stimulus simultaneously, and a program measured how long it took for them to mount a platform. With this code we wanted to be able reduce the time-consuming and error-prone nature of manual data analysis, and be able to manipulate an extensive data set with ease.

Since we didn't get to the point in which we could plot with the regular excel document, we created a simpler version for the plotting, but wrote the code with the original version in mind. 

# Code for plotting:
### First we imported the necessary packages
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import matplotlib as mpl
import scipy.stats
%matplotlib inline

### Then we imported the file and created the dataframe
newxl=pd.ExcelFile(r'C:\Users\Chris\Documents\Wildtypebehx1.3.xlsx')
All=pd.read_excel(newxl,index_col='Time')
Alldf=pd.DataFrame(All)
Alldf

### Afterwards we create new dataframes with the columns of interest
lo=All.iloc[:,0:10]
hi=All.iloc[:,10:20]
test=All.iloc[:,20:25]
Him=All.iloc[:,25:28]
Hif=All.iloc[:,28:31]
Tm=All.iloc[:,31:34]
Tf=All.iloc[:,34:37]

### Then we picked the rows of interest
lon=lo.loc[-4.966617:25.033083]
hin=hi.loc[-4.966617:25.033083]
testn=test.loc[-4.966617:25.033083]
Himn=Him.loc[-4.966617:25.033083]
Hifn=Hif.loc[-4.966617:25.033083]
Tmn=Tm.loc[-4.966617:25.033083]
Tfn=Tf.loc[-4.966617:25.033083]

### We drop the rows with NaN values as index
lonf=lon.loc[lon.index.dropna()]
hinf=hin.loc[hin.index.dropna()]
testnf=testn.loc[testn.index.dropna()]
himnf=Him.loc[hin.index.dropna()]
hifnf=Hif.loc[hin.index.dropna()]
Tmnf=Tmn.loc[Tmn.index.dropna()]
Tfnf=Tfn.loc[Tfn.index.dropna()]

### And we create lists of colors for our plots
g=("lightgrey",'lightgray','silver','darkgrey','darkgray','grey','gray','dimgrey','dimgray','black')
m=("lightblue","cyan","darkcyan")
f=("lightpink","pink","crimson")

# And we finally create the linegraphs to visualize the data
lonf.plot(xlabel='Time(s)',ylabel="Time on platform",title="Low conflict training",color=g)
hinf.plot(xlabel='Time(s)',ylabel="Time on platform",title="High conflict training", color=g)
testnf.plot(xlabel='Time(s)',ylabel="Time on platform",title="Conflict testing")
himnf.plot(xlabel='Time(s)',ylabel="Time on platform",title="Males in high conflict", color=m)
hifnf.plot(xlabel='Time(s)',ylabel="Time on platform",title="Females in high conflict ",color=f)
ax = himnf.plot(color=m)

hifnf.plot(xlabel='Time(s)',ylabel="Time on platform",title="Males vs Females in conflict training",ax=ax, color=f)
scipy.stats.ttest_ind(himnf['Hi10m'], hifnf['Hi10f'], equal_var=False)
axs = Tmnf.plot(color=m)

Tfnf.plot(xlabel='Time(s)',ylabel="Time on platform",title="Males vs Females in conflict testing",ax=axs, color=f)
scipy.stats.ttest_ind(Tmnf['TM5'], Tfnf['TF5'], equal_var=False)
