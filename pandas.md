---
title: 'Data Manipulation in Pandas and Python'
cover title: Pandas
description: 'In this workshop, we are going to learn some basic commands in Pandas, an expansive Python library for working with tabular data like CSV files. You can think of Pandas as a more powerful version of Excel that operates within the Python environment, where you can wrangle, clean, analyze, and visualize data. Knowing how to use Pandas is important if you plan on working with datasets that include qualitative and/or quantitative data points.'

programming_language: 'jupyter'

learning objectives:
    - Import Pandas and read in a CSV file as a DataFrame
    - Explore your data, including displaying and sampling the data
    - Clean your data, including checking for duplicates and converting data types
    - Filter your data, including renaming, selecting, dropping, and adding columns
    - Analyze your data by sorting columns, grouping columns, and counting values
    - Visualize your data with basic bar charts, pie charts, and time series
    - Write a DataFrame to a CSV file
    - Build your Pandas skills with the Pandas documentation and other resources

estimated time:
    - 3 hours

prerequisites:
    - python:
        description: (required) This workshop relies heavily on concepts from the Intro to Python workshop, and having a basic understanding of how to use the commands discussed in the workshop will be central for anyone who wants to learn about data analysis with Python and Pandas.
        required: true
    - command-line:
        description: (recommended) This workshop makes some reference to concepts from the Command Line workshop, and having basic knowledge about how to use the command line will be central for anyone who wants to learn about text analysis with Python and Pandas.
        recommended: true
    - data ethics: 
        description: Data Ethics (Recommended) This workshop will give you a basis for thinking through the ethical considerations of your programming projects.
        recommended: true

instructors: 
    - 'Rebecca Krisel'

authors:
    - 'Rebecca Krisel'

Editors:
    - 'Stephen Zweibel'

readings:
    - This workshop uses Jupyter Notebooks to process the Python commands in a clear and visual way. Read this very short introduction to how to use Notebooks [A Beginner’s Tutorial to Jupyter Notebooks](https://towardsdatascience.com/a-beginners-tutorial-to-jupyter-notebooks-1b2f8705888a)
    - "[Short Introduction to Jupyter Notebooks](https://curriculum.dhinstitutes.org/insights/short-introduction-to-jupyter-notebooks/)"
    - "[Guide To Data Cleaning: Definition, Benefits, Components, And How To Clean Your Data](https://www.tableau.com/learn/articles/what-is-data-cleaning)"

ethical considerations:
    - The dataset we are using for this workshop is from the [U.S. Refugee Arrivals Data](https://github.com/BuzzFeedNews/2015-11-refugees-in-the-united-states/blob/master/data/WRAPS-arrivals-by-destination-2005-2015-clean.csv). This dataset contains data about refugee arrivals to the United States between 2005 and 2015 and was originally compiled from the Department of State’s Refugee Processing Center by Jeremy Singer-Vine for his BuzzFeed article [“Where U.S. Refugees Come From — And Go — In Charts.”](https://www.buzzfeednews.com/article/jsvine/where-us-refugees-come-from-and-go-in-charts#.vooNwy74jO) 
    - As with any dataset, responsible data analysis requires more than just technical tools like Pandas. We also need to interrogate the data. Who collected this data? How and why is this data being collected? What assumptions are baked into this data? What consequences does this data have in the world? What does this data tell us about our world? When exploring this dataset, we can consider the meaning of the status of refugee, who has a right to claim that status, and which refugees are considered eligible to legally resettle in the U.S.. We could also think about who may not be represented in this data, including asylum seekers who migrate to the U.S. and become undocumented immigrants while waiting for their asylum claims to be processed.

projects:
    - The Simplest Data Science Project Using Pandas & Matplotlib:
        description: Further deepen your Pandas skills while making beautiful data visualizations in Matplolib using a dataset (from Kaggle) of forest fires in Brazil.
        link: https://towardsdatascience.com/the-simplest-data-science-project-using-pandas-matplotlib-9d7042e7ce6f
    - Make a Gradebook With Python & pandas:
        description: Learn how you can automate the process of calculating grades at the end of the semester using Pandas
        link: https://realpython.com/pandas-project-gradebook/

resources:
    - Jupyter Notebook shortcuts, tips and tricks:
        description: Here are some of the keyboard shortcuts and text snippets to help you program faster!
        link: http://maxmelnick.com/2016/04/19/python-beginner-tips-and-tricks.html

---
# Jupyter & JupyterLite
In this workshop, we are going to use JupyterLite as our Python environment, which is a lightweight version of Jupyter Notebooks.

You can think of **Jupyter Notebooks** as a comprehensive toolset for interactive computing and data exploration. It's like a fully equipped research laboratory where you can seamlessly blend narrative text, code, and visualizations. **JupyterLite** is a streamlined, lightweight version of this toolset, offering a more agile and accessible environment.

Jupyter Notebooks - Full Research Lab:
- Versatility: Jupyter Notebooks are like a fully equipped research lab. They support various programming languages, allowing you to conduct diverse computational experiments.
- Interactivity: Much like a lab where you can actively engage with your experiments, Jupyter Notebooks let you interactively run code cells, observe results, and refine your analyses on the fly.
- Rich Outputs: Visualizations, graphs, and other dynamic outputs enrich your narrative, creating a comprehensive and visually engaging research document.


JupyterLite - Portable Research Kit:
- Simplicity: JupyterLite is a simplified, more portable version. It's akin to having a compact research kit that allows you to conduct essential experiments without the full complexity of the lab.
- Accessibility: When you need a quick, accessible environment for coding and exploration, JupyterLite provides a more straightforward setup. It's like having your essential tools ready without the need for a fully equipped lab.


Learning and On-the-Go:
- Educational Tool: JupyterLite is often used for educational purposes or quick experiments. It serves as a friendly entry point for those learning about interactive computing without overwhelming them with the extensive features of the full Jupyter Notebooks.
- Portability: JupyterLite is convenient for situations where the full-scale Jupyter environment might be impractical or unnecessary. It's like having a research companion that fits into your backpack.


In essence, JupyterLite is a more nimble version of Jupyter Notebooks, suitable for scenarios where a lighter computational environment is sufficient. It shares the same core principles of interactive computing but in a more accessible and portable form, making it a valuable tool for quick experiments, learning, and situations where resource constraints or simplicity are paramount.


# Preparing your workspace and folders

Keeping all your files for a particular project in a designated file directory will keep your project organized and will make it easier to read in your files. 

Let’s create a “pandas_workshop” folder in our JupyterLite code editor workspace: 
- Click on "Open Code Editor" in the top right corner of this browser window. 
- In the folders toolbar, click the icon for the folder with the '+' on it. This will create a new "Untitled Folder." 
- To rename the folder, click on the folder name while  pressing the "control" key on your keyboard at the same time (MacOS) or right-clicking on your mousepad (Windows), and selecting "Rename" from the drop-down menu. 
- Rename the folder: “pandas_workshop”.

Next, we will need to first download our dataset and then upload it to your new “pandas_workshop” folder: 
- Click this button to download the dataset to your computer: <Download files='refugee-arrivals-by-destination.csv>
- Locate the file on your personal computer. Next, go back to the code editor and double-click into your “pandas_workshop.” 
- Click the upward facing arrow symbol to upload your refugee-arrivals-by-destination.csv file. 
- Once it's in that folder, you should be all set! 

We’ve also saved all of the code for this section in a [Jupyter Notebook file](https://github.com/GCDigitalFellows/intro-pandas-dri-2022/blob/main/PandasWorkshop.ipynb). You should download it and save it in your “pandas_workshop” folder on your Desktop. In this file you will find all of the workshop commands and the expected outputs. If you ever feel stuck or can’t seem to be able to advance in the workshop, you can open this file and see how we did it. 

For the best possible experience, we suggest/encourage you to:
* Create an .ipynb file and follow the workshop typing all the code yourself.
* Avoid copying/pasting the code. Much of learning has to do with you typing yourself.
* Only check the PandasWorkshop.ipynb file if you get lost or if you are not able to get the right output. Before opening it, put some time trying to figure out by yourself why it isn’t working. A big part of coding is learning to identify what we are doing wrong.
* I would also caution you against working with both files open at the same time. It is easy to get confused and start modifying the wrong one. But those are only suggestions. Maybe they will work for you, maybe they won’t, so feel free to do what suits you best. You are in charge here!


# Getting started with Pandas

* Pandas is a Python software library
* The name is derived from the term "panel data", an econometrics term for data sets that include observations over multiple time periods for the same individuals
* You can think of it as a FREE equivalent to Stata or SPSS for data manipulation and analysis. It is also more powerful than Excel
* Knowing how to use Pandas is important if you plan on working with data organized in spreadsheets (either quantitative or qualitative)


## Import Pandas

In the first blank cell, type the following command to import the Pandas library into our Jupyter Notebook. To run the command, you can click the “Run” button in the top toolbar, or you can click shift + return. 




```python
import pandas as pd
```

This import statement not only imports the Pandas library but also gives it the alias “pd.” Using this alias will save us from having to type out the entire word “Pandas” each time we need to use it. Libraries are sets of instructions that Python can use to perform specialized functions. 


If you don’t see an error when you run the notebook—that is, if there is no output—you can move on to the next step. It is not rare in programming that when you do things right, the result will be nothing happening. This is what we like to call a silent success.


## Read in a CSV file as a DataFrame

Next, we will read in our dataset saved as a CSV file. We will specifically work with the refugee-arrivals-by-destination.csv dataset, which contains data about refugee arrivals to the United States between 2005 and 2015, including the number of refugees who arrived in each U.S. city and state, the year that they arrived, and the country from which they arrived.

You want to make sure you save the dataset in the same location as your Jupyter Notebook, in this case the pandas_workshop folder. 


```python
refugee_df = pd.read_csv('refugee-arrivals-by-destination.csv', delimiter=",", encoding='utf-8')
```

- With this command, we are creating a **Pandas DataFrame** object, which is a 2-dimensional labeled data structure with columns of different types. You can think of it like a spreadsheet or SQL table, or a dictionary of Series objects. 
- It is common practice to abbreviate DataFrame with “df”, as in refugee_df.  
- When reading in the CSV file, we also specified the encoding and delimiter. The delimiter specifies the character that separates or “delimits” the columns in our dataset. For CSV files, the delimiter is usually a comma but it can also be a tab. 
- UTF is “Unicode Transformation Format”, and ‘8’ means 8-bit values are used in the encoding. It is one of the most efficient and convenient encoding formats. In Python, strings are by default in utf-8 format which means each alphabet corresponds to a unique code point. Setting the encoding format ensures our strings are uniform.


# Data exploration
In the following section we will learn how to view the DataFrame in addition to viewing smaller sections of it. 

## Display the Dataframe

To display the DataFrame, we can run a cell with the variable name of the DataFrame:


```python
refugee_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>dest_state</th>
      <th>dest_city</th>
      <th>arrivals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2005</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2006</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2007</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2008</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2009</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>5</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>121240</th>
      <td>2011</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121241</th>
      <td>2012</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>4</td>
    </tr>
    <tr>
      <th>121242</th>
      <td>2013</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>2</td>
    </tr>
    <tr>
      <th>121243</th>
      <td>2014</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121244</th>
      <td>2015</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>121245 rows × 5 columns</p>
</div>



Let’s take a look at a few elements in this DataFame: 



* Index
    * The bolded ascending numbers in the very left-hand column of the DataFrame is called the Pandas Index. You can select rows based on the Index.
    * By default, the Index is a sequence of numbers starting with zero. However, you can change the Index to something else, such as one of the columns in your dataset.
    * The default index is a Unique ID - that being said, the index does not have to be a Unique ID. You can set your index to be any column in your Dataframe
* Truncation
    * The DataFrame is truncated, signaled by the ellipses in the middle … of every column.
    * The DataFrame is truncated because by default, Pandas will display 60 rows and 20 columns. You can change these default settings see [documentation](https://pandas.pydata.org/pandas-docs/stable/user_guide/options.html)
* Rows x Columns
    * Pandas reports how many rows and columns are in this dataset at the bottom of the output. Our DataFrame has 121,245 rows × 5 columns.
* NAN
    * NaN is the Pandas value for any missing data. 


## Display a selection of the Dataframe
We can also display the first 2 rows of the DataFrame with the `.head()` method


```python
refugee_df.head(2)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>dest_state</th>
      <th>dest_city</th>
      <th>arrivals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2005</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2006</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




We can accomplish the same task using a slice instead:


```python
refugee_df[:2]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>dest_state</th>
      <th>dest_city</th>
      <th>arrivals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2005</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2006</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




We can also display the last 10 rows of the DataFrame with the `.tail()` method


```python
refugee_df.tail(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>dest_state</th>
      <th>dest_city</th>
      <th>arrivals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>121235</th>
      <td>2006</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>5</td>
    </tr>
    <tr>
      <th>121236</th>
      <td>2007</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>18</td>
    </tr>
    <tr>
      <th>121237</th>
      <td>2008</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>12</td>
    </tr>
    <tr>
      <th>121238</th>
      <td>2009</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>4</td>
    </tr>
    <tr>
      <th>121239</th>
      <td>2010</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>7</td>
    </tr>
    <tr>
      <th>121240</th>
      <td>2011</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121241</th>
      <td>2012</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>4</td>
    </tr>
    <tr>
      <th>121242</th>
      <td>2013</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>2</td>
    </tr>
    <tr>
      <th>121243</th>
      <td>2014</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121244</th>
      <td>2015</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




We can accomplish the same task using a slice instead:


```python
refugee_df[-10:]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>dest_state</th>
      <th>dest_city</th>
      <th>arrivals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>121235</th>
      <td>2006</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>5</td>
    </tr>
    <tr>
      <th>121236</th>
      <td>2007</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>18</td>
    </tr>
    <tr>
      <th>121237</th>
      <td>2008</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>12</td>
    </tr>
    <tr>
      <th>121238</th>
      <td>2009</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>4</td>
    </tr>
    <tr>
      <th>121239</th>
      <td>2010</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>7</td>
    </tr>
    <tr>
      <th>121240</th>
      <td>2011</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121241</th>
      <td>2012</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>4</td>
    </tr>
    <tr>
      <th>121242</th>
      <td>2013</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>2</td>
    </tr>
    <tr>
      <th>121243</th>
      <td>2014</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121244</th>
      <td>2015</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




## Display a random sample of the Dataframe

We can also look at a random sample of data with the `.sample()` method


```python
refugee_df.sample(15)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>dest_state</th>
      <th>dest_city</th>
      <th>arrivals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>102329</th>
      <td>2009</td>
      <td>Dem. Rep. Congo</td>
      <td>Texas</td>
      <td>Cedar Park</td>
      <td>0</td>
    </tr>
    <tr>
      <th>40110</th>
      <td>2006</td>
      <td>Ukraine</td>
      <td>Illinois</td>
      <td>Woodridge</td>
      <td>0</td>
    </tr>
    <tr>
      <th>45485</th>
      <td>2013</td>
      <td>Cuba</td>
      <td>Louisiana</td>
      <td>Avondale</td>
      <td>2</td>
    </tr>
    <tr>
      <th>62900</th>
      <td>2015</td>
      <td>Liberia</td>
      <td>Minnesota</td>
      <td>Brooklyn Center</td>
      <td>1</td>
    </tr>
    <tr>
      <th>46604</th>
      <td>2010</td>
      <td>Iraq</td>
      <td>Maine</td>
      <td>Norway</td>
      <td>10</td>
    </tr>
    <tr>
      <th>116748</th>
      <td>2007</td>
      <td>Latvia</td>
      <td>Washington</td>
      <td>Lynnwood</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5039</th>
      <td>2014</td>
      <td>Burma</td>
      <td>California</td>
      <td>Chula Vista</td>
      <td>0</td>
    </tr>
    <tr>
      <th>66487</th>
      <td>2005</td>
      <td>Iraq</td>
      <td>Missouri</td>
      <td>Saint Louis</td>
      <td>0</td>
    </tr>
    <tr>
      <th>108591</th>
      <td>2012</td>
      <td>Iraq</td>
      <td>Vermont</td>
      <td>Essex Junction</td>
      <td>0</td>
    </tr>
    <tr>
      <th>94980</th>
      <td>2008</td>
      <td>Russia</td>
      <td>Pennsylvania</td>
      <td>Warminster</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4690</th>
      <td>2006</td>
      <td>Bhutan</td>
      <td>California</td>
      <td>Alameda</td>
      <td>0</td>
    </tr>
    <tr>
      <th>72042</th>
      <td>2005</td>
      <td>Liberia</td>
      <td>New Jersey</td>
      <td>Englewood</td>
      <td>0</td>
    </tr>
    <tr>
      <th>66931</th>
      <td>2009</td>
      <td>Somalia</td>
      <td>Missouri</td>
      <td>Kansas City</td>
      <td>141</td>
    </tr>
    <tr>
      <th>91265</th>
      <td>2011</td>
      <td>Belarus</td>
      <td>Pennsylvania</td>
      <td>Millersburg</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2077</th>
      <td>2011</td>
      <td>Iraq</td>
      <td>Arizona</td>
      <td>Goodyear</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



We can tell it's a random sample since the index numbers are completly disorganized. 

# Basic data cleaning
In the following sections we will review some basic data cleaning steps including checking and converting our data types in addition to checking and removing duplicate rows. 
## Data Types

We can get information about the columns in the DataFrame by using the `.info()` method.


```python
refugee_df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 121245 entries, 0 to 121244
    Data columns (total 5 columns):
     #   Column      Non-Null Count   Dtype 
    ---  ------      --------------   ----- 
     0   year        121245 non-null  int64 
     1   origin      121245 non-null  object
     2   dest_state  121245 non-null  object
     3   dest_city   121245 non-null  object
     4   arrivals    121245 non-null  int64 
    dtypes: int64(2), object(3)
    memory usage: 4.6+ MB


This report tells us how many non-null, or non-blank, values are in each column, as well as what type of data is in each column. 

Pandas uses a different lexicon to describe data types from those we learned in our intro to Python curriculum. Below is a table that explains what each data type means:


<table>
  <tr>
   <td><strong>Pandas data types</strong>
   </td>
   <td><strong>Python data types</strong>
   </td>
   <td><strong>Usage</strong>
   </td>
  </tr>
  <tr>
   <td>object
   </td>
   <td>String or mixed
   </td>
   <td>Text or mixed numeric and non-numeric values
   </td>
  </tr>
  <tr>
   <td>float64
   </td>
   <td>float
   </td>
   <td>Floating point numbers
   </td>
  </tr>
  <tr>
   <td>int64
   </td>
   <td>integer
   </td>
   <td>Integer numbers
   </td>
  </tr>
  <tr>
   <td>datetime64
   </td>
   <td>NA
   </td>
   <td>Date and time values
   </td>
  </tr>
</table>





## Converting data types

Keeping this in mind, it looks as though the data type for the year column is a “int64” instead of being “datetime64.” 


```python
refugee_df['year'] = pd.to_datetime(refugee_df['year'], format="%Y")
```

This command translates to: for the “year” column in the “refugee_df” DataFrame, use the `to_datetime` method in the Pandas library to convert the values in the “year” column in the “refugee_df” DataFrame to datetime data types. We specify the format as `%Y` since this is the format of our data. 


We can then check to see if the data type was properly converted using the `.dtypes` object, which is similar to the `.info()` method, except it only provides information on data types.


```python
refugee_df.dtypes
```




    year          datetime64[ns]
    origin                object
    dest_state            object
    dest_city             object
    arrivals               int64
    dtype: object



As we can see, the data in the “year” column was successfully transformed into the datetime64 data type.

## Check for duplicate rows

As part of our data cleaning process, we want to check for duplicate rows. We can do this by using the `.duplicated()` method inside a filter to isolate only the rows in the DataFrame that are exact duplicates. Filtering data by certain values is similar to selecting columns. We add the parameter `keep=False`, which will display all the duplicated values in the dataset — rather than just the first duplicated value keep='first' or the last duplicated value keep='last'.


```python
refugee_df[refugee_df.duplicated(keep=False)]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>dest_state</th>
      <th>dest_city</th>
      <th>arrivals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>13</th>
      <td>2007-01-01</td>
      <td>Burma</td>
      <td>Alabama</td>
      <td>Auburn</td>
      <td>0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>2008-01-01</td>
      <td>Burma</td>
      <td>Alabama</td>
      <td>Auburn</td>
      <td>0</td>
    </tr>
    <tr>
      <th>15</th>
      <td>2009-01-01</td>
      <td>Burma</td>
      <td>Alabama</td>
      <td>Auburn</td>
      <td>0</td>
    </tr>
    <tr>
      <th>16</th>
      <td>2010-01-01</td>
      <td>Burma</td>
      <td>Alabama</td>
      <td>Auburn</td>
      <td>0</td>
    </tr>
    <tr>
      <th>17</th>
      <td>2007-01-01</td>
      <td>Burma</td>
      <td>Alabama</td>
      <td>Auburn</td>
      <td>0</td>
    </tr>
    <tr>
      <th>18</th>
      <td>2008-01-01</td>
      <td>Burma</td>
      <td>Alabama</td>
      <td>Auburn</td>
      <td>0</td>
    </tr>
    <tr>
      <th>19</th>
      <td>2009-01-01</td>
      <td>Burma</td>
      <td>Alabama</td>
      <td>Auburn</td>
      <td>0</td>
    </tr>
    <tr>
      <th>20</th>
      <td>2010-01-01</td>
      <td>Burma</td>
      <td>Alabama</td>
      <td>Auburn</td>
      <td>0</td>
    </tr>
    <tr>
      <th>155</th>
      <td>2013-01-01</td>
      <td>Cuba</td>
      <td>Alabama</td>
      <td>Russellville</td>
      <td>0</td>
    </tr>
    <tr>
      <th>156</th>
      <td>2014-01-01</td>
      <td>Cuba</td>
      <td>Alabama</td>
      <td>Russellville</td>
      <td>0</td>
    </tr>
    <tr>
      <th>157</th>
      <td>2015-01-01</td>
      <td>Cuba</td>
      <td>Alabama</td>
      <td>Russellville</td>
      <td>0</td>
    </tr>
    <tr>
      <th>158</th>
      <td>2005-01-01</td>
      <td>Cuba</td>
      <td>Alabama</td>
      <td>Theodore</td>
      <td>0</td>
    </tr>
    <tr>
      <th>159</th>
      <td>2006-01-01</td>
      <td>Cuba</td>
      <td>Alabama</td>
      <td>Theodore</td>
      <td>0</td>
    </tr>
    <tr>
      <th>160</th>
      <td>2013-01-01</td>
      <td>Cuba</td>
      <td>Alabama</td>
      <td>Russellville</td>
      <td>0</td>
    </tr>
    <tr>
      <th>161</th>
      <td>2014-01-01</td>
      <td>Cuba</td>
      <td>Alabama</td>
      <td>Russellville</td>
      <td>0</td>
    </tr>
    <tr>
      <th>162</th>
      <td>2015-01-01</td>
      <td>Cuba</td>
      <td>Alabama</td>
      <td>Russellville</td>
      <td>0</td>
    </tr>
    <tr>
      <th>163</th>
      <td>2005-01-01</td>
      <td>Cuba</td>
      <td>Alabama</td>
      <td>Theodore</td>
      <td>0</td>
    </tr>
    <tr>
      <th>164</th>
      <td>2006-01-01</td>
      <td>Cuba</td>
      <td>Alabama</td>
      <td>Theodore</td>
      <td>0</td>
    </tr>
    <tr>
      <th>236</th>
      <td>2012-01-01</td>
      <td>Iran</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>1</td>
    </tr>
    <tr>
      <th>237</th>
      <td>2013-01-01</td>
      <td>Iran</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>6</td>
    </tr>
    <tr>
      <th>238</th>
      <td>2014-01-01</td>
      <td>Iran</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>3</td>
    </tr>
    <tr>
      <th>239</th>
      <td>2015-01-01</td>
      <td>Iran</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>5</td>
    </tr>
    <tr>
      <th>240</th>
      <td>2005-01-01</td>
      <td>Iran</td>
      <td>Alabama</td>
      <td>Pelham</td>
      <td>0</td>
    </tr>
    <tr>
      <th>247</th>
      <td>2012-01-01</td>
      <td>Iran</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>1</td>
    </tr>
    <tr>
      <th>248</th>
      <td>2013-01-01</td>
      <td>Iran</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>6</td>
    </tr>
    <tr>
      <th>249</th>
      <td>2014-01-01</td>
      <td>Iran</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>3</td>
    </tr>
    <tr>
      <th>250</th>
      <td>2015-01-01</td>
      <td>Iran</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>5</td>
    </tr>
    <tr>
      <th>251</th>
      <td>2005-01-01</td>
      <td>Iran</td>
      <td>Alabama</td>
      <td>Pelham</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



Looks like we have a few duplicate rows in our dataset. 

To remove those duplicates, we can use the `.drop_duplicates()` method to drop duplicates from the DataFrame and select to keep the first instance of the duplicate or the last instance:


```python
refugee_df = refugee_df.drop_duplicates(keep='first')
```

We can check to see if the command got rid of the duplicate rows by running the .duplicated() method again: 


```python
refugee_df[refugee_df.duplicated(keep=False)]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>dest_state</th>
      <th>dest_city</th>
      <th>arrivals</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>



Great news! We successfully removed our duplicate rows!

# Rename, select, drop, filter and add new columns
In the following section we will learn how to rename, select, drop, filter and add new columns
## See list of columns

To see a full list of the columns in our DataFrame, we can run the following command:


```python
refugee_df.columns
```




    Index(['year', 'origin', 'dest_state', 'dest_city', 'arrivals'], dtype='object')



Our DataFrame has relatively few columns, so seeing the full list is not absolutely necessary in our case. This step becomes important when you are working with DataFrames with many columns. 

## Rename columns

To improve the readability of our dataset, we can rename columns. In our case, let’s rename “dest_state” as “state” and “dest_city” as “city”. We will use the `.rename()` method and the columns= parameter. Note that in this case we are setting the DataFrame equal to the returned value of the method so as to save the results into the DataFrame.


```python
refugee_df=refugee_df.rename(columns={'dest_state': 'state','dest_city':'city' })
refugee_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>state</th>
      <th>city</th>
      <th>arrivals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2005-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2006-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2007-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2008-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2009-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>5</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>121240</th>
      <td>2011-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121241</th>
      <td>2012-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>4</td>
    </tr>
    <tr>
      <th>121242</th>
      <td>2013-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>2</td>
    </tr>
    <tr>
      <th>121243</th>
      <td>2014-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121244</th>
      <td>2015-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>121231 rows × 5 columns</p>
</div>



## Select columns

Let’s say we wanted to view data from just one column in the DataFrame. To do this, we could run the following command:


```python
refugee_df[['state']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>state</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alabama</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Alabama</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Alabama</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Alabama</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Alabama</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>121240</th>
      <td>Wisconsin</td>
    </tr>
    <tr>
      <th>121241</th>
      <td>Wisconsin</td>
    </tr>
    <tr>
      <th>121242</th>
      <td>Wisconsin</td>
    </tr>
    <tr>
      <th>121243</th>
      <td>Wisconsin</td>
    </tr>
    <tr>
      <th>121244</th>
      <td>Wisconsin</td>
    </tr>
  </tbody>
</table>
<p>121231 rows × 1 columns</p>
</div>



Here we use double brackets around the column name to transform the column from a Series object into a DataFrame. Basically, the interior brackets are for lists, and the outside brackets are indexing operators. If you are curious to see the difference, try the following command instead: refugee_df['state']. 

To view additional columns at the same time, you can add them to the list within the square brackets, separated by a comma. However, you can’t select multiple columns as a Series (try: refugee_df['state','city'])


```python
refugee_df[['state','city']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>state</th>
      <th>city</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alabama</td>
      <td>Mobile</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Alabama</td>
      <td>Mobile</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Alabama</td>
      <td>Mobile</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Alabama</td>
      <td>Mobile</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Alabama</td>
      <td>Mobile</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>121240</th>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
    </tr>
    <tr>
      <th>121241</th>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
    </tr>
    <tr>
      <th>121242</th>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
    </tr>
    <tr>
      <th>121243</th>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
    </tr>
    <tr>
      <th>121244</th>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
    </tr>
  </tbody>
</table>
<p>121231 rows × 2 columns</p>
</div>



## Drop columns

To remove a column from the DataFrame, we can use the `.drop()` method and include the column name. In our case, we could drop the “city” column and save the result as a new DataFrame “refugee_drop_df” so we don’t override our original DataFrame. 


```python
refugee_drop_city_df = refugee_df.drop(columns="city")
```


```python
refugee_drop_city_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>state</th>
      <th>arrivals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2005-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2006-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2007-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2008-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2009-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>5</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>121240</th>
      <td>2011-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121241</th>
      <td>2012-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>4</td>
    </tr>
    <tr>
      <th>121242</th>
      <td>2013-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>2</td>
    </tr>
    <tr>
      <th>121243</th>
      <td>2014-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121244</th>
      <td>2015-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>121231 rows × 4 columns</p>
</div>



## Filter columns

We can filter a Pandas DataFrame to select only certain values. Filtering data by certain values is similar to selecting columns.

We type the name of the DataFrame followed by square brackets and then, instead of inserting a column name, we insert a True/False condition. For example, to select only rows that contain the value “Iraq”, we could run the following command:


```python
refugee_iraq_df = refugee_df[refugee_df['origin'] == 'Iraq']
```


```python
refugee_iraq_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>state</th>
      <th>city</th>
      <th>arrivals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>267</th>
      <td>2005-01-01</td>
      <td>Iraq</td>
      <td>Alabama</td>
      <td>Birmingham</td>
      <td>0</td>
    </tr>
    <tr>
      <th>268</th>
      <td>2006-01-01</td>
      <td>Iraq</td>
      <td>Alabama</td>
      <td>Birmingham</td>
      <td>0</td>
    </tr>
    <tr>
      <th>269</th>
      <td>2007-01-01</td>
      <td>Iraq</td>
      <td>Alabama</td>
      <td>Birmingham</td>
      <td>0</td>
    </tr>
    <tr>
      <th>270</th>
      <td>2008-01-01</td>
      <td>Iraq</td>
      <td>Alabama</td>
      <td>Birmingham</td>
      <td>6</td>
    </tr>
    <tr>
      <th>271</th>
      <td>2009-01-01</td>
      <td>Iraq</td>
      <td>Alabama</td>
      <td>Birmingham</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>120503</th>
      <td>2011-01-01</td>
      <td>Iraq</td>
      <td>Wisconsin</td>
      <td>Wauwatosa</td>
      <td>0</td>
    </tr>
    <tr>
      <th>120504</th>
      <td>2012-01-01</td>
      <td>Iraq</td>
      <td>Wisconsin</td>
      <td>Wauwatosa</td>
      <td>0</td>
    </tr>
    <tr>
      <th>120505</th>
      <td>2013-01-01</td>
      <td>Iraq</td>
      <td>Wisconsin</td>
      <td>Wauwatosa</td>
      <td>2</td>
    </tr>
    <tr>
      <th>120506</th>
      <td>2014-01-01</td>
      <td>Iraq</td>
      <td>Wisconsin</td>
      <td>Wauwatosa</td>
      <td>0</td>
    </tr>
    <tr>
      <th>120507</th>
      <td>2015-01-01</td>
      <td>Iraq</td>
      <td>Wisconsin</td>
      <td>Wauwatosa</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
<p>18205 rows × 5 columns</p>
</div>



We stored our results in a new variable `refugee_iraq_df`

## Drop Rows
If we wanted to exclude all rows containing the value “Iraq”, we could run the following command:


```python
refugee_drop_iraq_df = refugee_df[refugee_df['origin'] != 'Iraq']
```


```python
refugee_drop_iraq_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>state</th>
      <th>city</th>
      <th>arrivals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2005-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2006-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2007-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2008-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2009-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>5</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>121240</th>
      <td>2011-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121241</th>
      <td>2012-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>4</td>
    </tr>
    <tr>
      <th>121242</th>
      <td>2013-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>2</td>
    </tr>
    <tr>
      <th>121243</th>
      <td>2014-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
    <tr>
      <th>121244</th>
      <td>2015-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>103026 rows × 5 columns</p>
</div>



## Add columns

We can also add columns to the DataFrame. For example, we can add a `percent_total` column to calculate the percentage of total refugee arrivals for each row.   


```python
refugee_df['percent_total'] = (refugee_df['arrivals'] / refugee_df['arrivals'].sum())*100
```


```python
refugee_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>state</th>
      <th>city</th>
      <th>arrivals</th>
      <th>percent_total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2005-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2006-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2007-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2008-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>0</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2009-01-01</td>
      <td>Afghanistan</td>
      <td>Alabama</td>
      <td>Mobile</td>
      <td>5</td>
      <td>0.000743</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>121240</th>
      <td>2011-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>121241</th>
      <td>2012-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>4</td>
      <td>0.000595</td>
    </tr>
    <tr>
      <th>121242</th>
      <td>2013-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>2</td>
      <td>0.000297</td>
    </tr>
    <tr>
      <th>121243</th>
      <td>2014-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>121244</th>
      <td>2015-01-01</td>
      <td>Vietnam</td>
      <td>Wisconsin</td>
      <td>Milwaukee</td>
      <td>0</td>
      <td>0.000000</td>
    </tr>
  </tbody>
</table>
<p>121231 rows × 6 columns</p>
</div>



*_Note: `refugee_df['arrivals'].sum()` calculates the sum of all the values in the arrivals column._ 



You can read the command we just ran as: create a new column that calculates the number of arrivals in a row divided by the total number of arrivals in the dataset, times 100. The result of this calculation will equal the percentage of total refugee arrivals for each row.

# Sort Columns, Groupby Columns, & Calculations
In the following section we will learn how to sort and group columns in order to perform calculations.  

## Stacking requests

In this lesson, we will be using commands that stack various requests such as methods, parameters, operators, and more to define the command. Pandas encourages this kind of stacking, but it can seem overwhelming at first to beginners. For example, as we will see below, a command could include two or more methods that stack on top of each other, and end with a slice operator to view only the top N rows of the results. In addition, a command can include specific parameters to call out a particular column or to sort the data in descending order. 

We will move slowly through each of the following commands to break them down. 

## Sort columns

To sort a DataFrame, we can use the `.sort_values()` method with the parameter by= and including the name of the column we want to sort by written in quotation marks. 

For example, we can sort the DataFrame by the arrivals column:


```python
refugee_df.sort_values(by='arrivals', ascending=False)[:15]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>origin</th>
      <th>state</th>
      <th>city</th>
      <th>arrivals</th>
      <th>percent_total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>11359</th>
      <td>2009-01-01</td>
      <td>Iraq</td>
      <td>California</td>
      <td>El Cajon</td>
      <td>2813</td>
      <td>0.418279</td>
    </tr>
    <tr>
      <th>8718</th>
      <td>2008-01-01</td>
      <td>Iran</td>
      <td>California</td>
      <td>Glendale</td>
      <td>2025</td>
      <td>0.301107</td>
    </tr>
    <tr>
      <th>11360</th>
      <td>2010-01-01</td>
      <td>Iraq</td>
      <td>California</td>
      <td>El Cajon</td>
      <td>1811</td>
      <td>0.269286</td>
    </tr>
    <tr>
      <th>8719</th>
      <td>2009-01-01</td>
      <td>Iran</td>
      <td>California</td>
      <td>Glendale</td>
      <td>1722</td>
      <td>0.256053</td>
    </tr>
    <tr>
      <th>58761</th>
      <td>2012-01-01</td>
      <td>Iraq</td>
      <td>Michigan</td>
      <td>Southfield</td>
      <td>1720</td>
      <td>0.255755</td>
    </tr>
    <tr>
      <th>11362</th>
      <td>2012-01-01</td>
      <td>Iraq</td>
      <td>California</td>
      <td>El Cajon</td>
      <td>1698</td>
      <td>0.252484</td>
    </tr>
    <tr>
      <th>8717</th>
      <td>2007-01-01</td>
      <td>Iran</td>
      <td>California</td>
      <td>Glendale</td>
      <td>1637</td>
      <td>0.243414</td>
    </tr>
    <tr>
      <th>64090</th>
      <td>2006-01-01</td>
      <td>Somalia</td>
      <td>Minnesota</td>
      <td>Minneapolis</td>
      <td>1586</td>
      <td>0.235830</td>
    </tr>
    <tr>
      <th>11358</th>
      <td>2008-01-01</td>
      <td>Iraq</td>
      <td>California</td>
      <td>El Cajon</td>
      <td>1569</td>
      <td>0.233302</td>
    </tr>
    <tr>
      <th>25699</th>
      <td>2005-01-01</td>
      <td>Cuba</td>
      <td>Florida</td>
      <td>Miami</td>
      <td>1537</td>
      <td>0.228544</td>
    </tr>
    <tr>
      <th>87927</th>
      <td>2006-01-01</td>
      <td>Somalia</td>
      <td>Ohio</td>
      <td>Columbus</td>
      <td>1319</td>
      <td>0.196129</td>
    </tr>
    <tr>
      <th>11363</th>
      <td>2013-01-01</td>
      <td>Iraq</td>
      <td>California</td>
      <td>El Cajon</td>
      <td>1238</td>
      <td>0.184084</td>
    </tr>
    <tr>
      <th>40503</th>
      <td>2014-01-01</td>
      <td>Burma</td>
      <td>Indiana</td>
      <td>Indianapolis</td>
      <td>1211</td>
      <td>0.180070</td>
    </tr>
    <tr>
      <th>25704</th>
      <td>2010-01-01</td>
      <td>Cuba</td>
      <td>Florida</td>
      <td>Miami</td>
      <td>1151</td>
      <td>0.171148</td>
    </tr>
    <tr>
      <th>58829</th>
      <td>2014-01-01</td>
      <td>Iraq</td>
      <td>Michigan</td>
      <td>Troy</td>
      <td>1095</td>
      <td>0.162821</td>
    </tr>
  </tbody>
</table>
</div>



Note: In the command above, we used the `by=` parameter to specify that the data be sorted according to the `arrivals` column and we added the `ascending=False` parameter in order to request that the data be displayed with the highest number first. By default, Pandas will sort in `ascending` order, meaning from the smallest value to the largest value. We also added a Python list slice (i.e., [:15]) to view just the top 15 rows.

## Groupby Columns

We can group data and perform calculations on the groups using the `.groupby()` method. For example, to see the breakdown of the number of arrivals by country of origin, we can use the following command:


```python
refugee_df.groupby('origin')
```




    <pandas.core.groupby.generic.DataFrameGroupBy object at 0x7f9b81ebc100>



This command created a Groupby object—grouped data that we can use to perform calculations such as counting the number of non-blank values in each column for each arrival by country of origin.

Next, we will use the following command to sum the number of refugee arrivals by country of origin, with the output showing the top twenty rows sorted by descending order:


```python
refugee_df.groupby('origin')['arrivals'].sum().sort_values(ascending=False)[:20]
```




    origin
    Burma              151875
    Iraq               127326
    Bhutan              85316
    Somalia             71120
    Cuba                39946
    Iran                36683
    Dem. Rep. Congo     25493
    Russia              15656
    Eritrea             14645
    Sudan               12636
    Ukraine             11727
    Burundi             11152
    Vietnam             10769
    Liberia              9424
    Ethiopia             8487
    Afghanistan          6751
    Laos                 6609
    Moldova              4482
    Syria                2359
    Colombia             1956
    Name: arrivals, dtype: int64



These results show us the total number of arrivals by country of origin across the 2005-2015 period, in descending order, sliced for the top 20 results. 

Let’s unpack the command to better understand these results: 



* We have three stacked methods here: .groupby(), .count(), and .sort_values(). 
* groupby('origin')['arrivals']: For the Groupby object we defined in the previous step, groupby(‘origin’), we are isolating the “arrivals” column. Basically, we are asking to view the number of refugee arrivals by country of origin. 
* .sum(): This method adds non-blank cells for each column or row. The results we see in the output show the total number of refugee arrivals by country of origin. 
* .sort_values(ascending=False): This method specifies how we want our output to be sorted. We include the ascending=False parameter in order to request that the data be displayed with the highest percentage first.
* [:20]: This Python slide specifies that we just want to see the top 20 rows.

## Convert Series Object to Dataframe
You will notice that our output is not a Dataframe. Instead, it's a Series Object, which doesn't allow us to select data or make further calculations on the data. We can convert it to a Dataframe by first storing the command above in a new variable and stacking two extra commands" `to_frame` and `reset_index`:


```python
ref_sum_df=refugee_df.groupby('origin')['arrivals'].sum().sort_values(ascending=False)[:20]
ref_sum_df = ref_sum_df.to_frame().reset_index()
ref_sum_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>origin</th>
      <th>arrivals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Burma</td>
      <td>151875</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Iraq</td>
      <td>127326</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Bhutan</td>
      <td>85316</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Somalia</td>
      <td>71120</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Cuba</td>
      <td>39946</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Iran</td>
      <td>36683</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Dem. Rep. Congo</td>
      <td>25493</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Russia</td>
      <td>15656</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Eritrea</td>
      <td>14645</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Sudan</td>
      <td>12636</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Ukraine</td>
      <td>11727</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Burundi</td>
      <td>11152</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Vietnam</td>
      <td>10769</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Liberia</td>
      <td>9424</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Ethiopia</td>
      <td>8487</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Afghanistan</td>
      <td>6751</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Laos</td>
      <td>6609</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Moldova</td>
      <td>4482</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Syria</td>
      <td>2359</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Colombia</td>
      <td>1956</td>
    </tr>
  </tbody>
</table>
</div>



# Basic data visualizations

To create plots and data visualization in Pandas, we can add the .plot() method to any DataFrame or Series object that has appropriate numeric data.

We can specify the title with the title= parameter and the kind of plot by altering the kind= parameter:



* ‘bar’ or ‘barh’ for bar plots (h is for horizontal)
* ‘hist’ for histogram
* ‘box’ for boxplot
* ‘kde’ or ‘density’ for density plots
* ‘area’ for area plots
* ‘scatter’ for scatter plots
* ‘hexbin’ for hexagonal bin plots
* ‘pie’ for pie plots

## Bar Charts
For example, we can visualize the data we got from our Groupby command looking at the total number of refugees by country of arrival as a bar chart:


```python
ref_sum_df.plot(kind='bar', x= 'origin', y='arrivals', 
                title='Total number of refugee arrivals in the U.S. \n by country of origin')
```




    <Axes: title={'center': 'Total number of refugee arrivals in the U.S. \n by country of origin'}, xlabel='origin'>




    
![png](images/output_68_1.png)
    


Let’s unpack the command to better understand these results:

* ref_sum_df: This is the variable we created in the previous lesson summing the number of refugee arrivals by country of origin, with the output showing the top twenty rows sorted by descending order
* .plot(kind='bar', x= 'origin', y='arrivals', title='Total number of refugee arrivals in the U.S. \n by country of origin'):
    * Here we are using the .plot() method to create a visualization, and we are specifying that we want a bar chart with the “kind=’bar’” parameter. 
    * We also specify the values for the x axis (orgin) and y axis (arrivals)
    * We are also giving the chart a title with the “title='Total number of refugee arrivals in the U.S. \n by country of origin'” parameter. 
        * Note: By adding “\n” in the title text, we signify that the text that follows should be on a new line. 

## Pie Charts
We can also visualize the data as a pie chart:


```python
ref_sum_df.set_index('origin')[:10].plot(kind='pie', y='arrivals', 
                                         title='Refugee arrivals in the U.S.')
```




    <Axes: title={'center': 'Refugee arrivals in the U.S.'}, ylabel='arrivals'>




    
![png](images/output_70_1.png)
    


- We start by setting the index of the dataframe to the `origin` column. This ensures that our legend will show the country names. 
- We slice our results to show just the top 10 countries. This makes our chart more legible. 
- Next, we use the `.plot()` method, specifying `pie` as the type of plot
- We also specify the y values - in our case `arrivals`




## Time Series

We can also create time series using the Groupby method. For example, if we wanted to visualize the total number of refugees resettled in the U.S. across the 2005-2015 period, we would first create a Groupby object based on the “year” column (refer back to lesson 7 for more on Groupby objects). 




```python
refugee_df.groupby('year')
```




    <pandas.core.groupby.generic.DataFrameGroupBy object at 0x7f9bd6807e80>



Next, we can create a new variable calculating the average number of refugees being resettled over time. 


```python
total_arrivals_by_year = refugee_df.groupby('year')['arrivals'].sum()
```

Let’s break this command down:



* We have two stacked methods here: .groupby() and .sum()
* groupby('year')['arrivals']: For the Groupby object, groupby(year), we are isolating the “arrivals” column. Basically, we are asking to view the number of refugee arrivals by year. 
* .sum(): This method returns the sum of the values over the requested axis. In our case, it will calculate the total number of refugee arrivals per year.
* We store our results in the `total_arrivals_by_year` variable

Finally, we can add the .plot() method to create a line chart. 


```python
total_arrivals_by_year.plot(kind='line', title="Total Number of Refugee Arrivals by Year")
```




    <Axes: title={'center': 'Total Number of Refugee Arrivals by Year'}, xlabel='year'>




    
![png](images/output_76_1.png)
    


In this command, we are adding the .plot() method to request a chart, and specifying that we want a line graph with the “kind=line” parameter. We are also giving the chart a title with the “title='Total Number of Refugee Arrivals by Year'” parameter. 



# Write to CSV

To output a new CSV file, we can use the .to_csv method with a name for the file in quotation marks. For example, since we added the percent_total column to the refugee_df DataFrame, we may want to download the updated DataFrame as a CSV file to use it with other programs.  


```python
refugee_df.to_csv("new_refugee.csv", encoding='utf-8', index=False)
```

In addition to a filename, we’re also specifying that the encoding is utf-8 and that the Index (the bolded left-most column) is not included in the CSV file.

 

# Building your Pandas skills with the Pandas documentation and other resources

Learning how to ask the right questions in a search engine like Google in order to find the solution to what you are trying to accomplish is the name of the game when you are just starting out with Python. Since Pandas is a popular and well documented Python package, you are bound to find myriads of resources that can help you get where you are going. 

A good first place to start when you are searching for answers with Pandas is to look at the Pandas documentation, which is fairly accessible to beginners, and is an incredible resource when you want to learn how to use a new command. It also offers a [User Guide](https://pandas.pydata.org/pandas-docs/stable/user_guide/index.html) for beginners with some fun exercises to deepen your learning.  

Let’s say you wanted to find out more about the .sort_values method we used in lesson 7 and understand the different parameters the method accepts:



* You could first search for .sort_values on the Pandas documentation website ([https://pandas.pydata.org](https://pandas.pydata.org)) and navigate to the “[pandas.DataFrame.sort_values](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sort_values.html?highlight=sort_values#pandas-dataframe-sort-values)” documentation page.
* Scroll through the page for the info, and look at the second section for examples of how to use the method and its various parameters. 






* If you don’t find an answer that makes sense to you on the Pandas documentation page, then look on Google for other resources. Some of our go-to websites for help are [Stack Overflow](https://stackoverflow.com/), [Geeks for Geeks](https://www.geeksforgeeks.org/), and [Data to Fish](https://datatofish.com/). 

## Other Resources



* This workshop owes a huge debt to Melanie Walsh’s _[Introduction to Cultural Analytics & Python](https://melaniewalsh.github.io/Intro-Cultural-Analytics/welcome.html)_. This easy to use and understand textbook provides additional support for using Pandas. This is a great place to start if you want to continue building your Pandas skills. 