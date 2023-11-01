# DAC_PHASE4
COVID-19 CASES ANALYSIS
import pandas as pd
import matplotlib.pyplot as plt

# Replace with the URL of the COVID-19 dataset you want to analyze
url = "https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv"

# Load the data into a DataFrame
df = pd.read_csv(url)

# Group data by country/region
grouped = df.groupby('Country/Region').sum()
grouped = grouped.drop(columns=['Lat', 'Long'])

# Transpose the DataFrame for easier plotting
grouped = grouped.transpose()

# Plot COVID-19 cases for specific countries
countries_to_plot = ['US', 'India', 'Brazil', 'United Kingdom']
grouped[countries_to_plot].plot()
plt.title("COVID-19 Cases Over Time")
plt.xlabel("Date")
plt.ylabel("Number of Cases")
plt.legend(countries_to_plot)
plt.grid()
plt.show()
