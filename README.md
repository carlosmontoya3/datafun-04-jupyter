# datafun-04-jupyter
## How to Install and Run the Project
python3 -m pip install jupyterlab numpy pandas matplotlib seaborn scipy
python3 -m pip freeze > requirements.txt

## Project-4-Carlos
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns

# Load the Iris dataset into DataFrame
df = sns.load_dataset('iris')

# Inspect first rows of the DataFrame
print(df.head(10))
print(df.shape)
print(df.dtypes)

print(df.describe())

# Inspect histogram by numerical column
df['petal_width'].hist()

# Inspect histograms for all numerical columns
df.hist()

# Show all plots
plt.show()

# Inspect value counts by categorical column
df['species'].value_counts()

# Inspect value counts for all categorical columns
for col in df.select_dtypes(include=['object', 'category']).columns:
    # Display count plot
    sns.countplot(x=col, data=df)
    plt.title(f'Distribution of {col}')
    plt.show()

# Show all plots
plt.show()

# Renaming a column
df.rename(columns={'sepal_length': 'Sepal Length'}, inplace=True)
df.rename(columns={'sepal_width': 'Sepal Width'}, inplace=True)
df.rename(columns={'petal_length': 'Petal Length'}, inplace=True)
df.rename(columns={'petal_width': 'Petal Width'}, inplace=True)
df.rename(columns={'species': 'Species'}, inplace=True)

# Adding a new column
df['Sepal Area'] = df['Sepal Length'] * df['Sepal Width']
df['Petal Area'] = df['Petal Length'] * df['Petal Width']

sns.pairplot(df, hue='species')
plt.show()

