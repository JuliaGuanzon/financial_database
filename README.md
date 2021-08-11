# Financial Database

Researching individual stocks takes time and a great amount of financial knowledge to be confident in making the right investment. For this reason, exchange-traded fund portfolios are great investments. With an ETF, you invest your money in a diverse portfolio, which means less risk than just investing in individual stocks. It can also bring security to an investor, as this group of stocks have been grouped together for their quality of returns. This financial database application will assist in analyzing an EFT and its cumulative returns. The user will be able to extract data for one individual stock in the ETF to gain an understanding of how that stock contributes to that porfolio. 

---

## Technologies

In order for this program to run, this application must be used in Jupyter Notebook, as it uses the Pandas/Python language. To run the program, it is essential to have JupyterLab installed. To ensure the code works, please open the file in a dev environment using python. It is also necessary to install Pandas in order to read/run the code.

The operating systems and program versions are mentioned below and are highly recommended when running the program.

**Systems**

[conda 4.10.3](https://docs.anaconda.com/anaconda/install/index.html) - Package manager, Environment Manager

python 3.7 - included in Anaconda

JupyterLab - included in Python 

Pandas - included in Python

**Other Installations**

[Numpy](https://numpy.org/doc/stable/) - included in Python

[PyViz](https://pyviz.org/) - tools for data visualizations

[SQLAlchemy](https://docs.sqlalchemy.org/en/14/core/engines.html) - helps communicate with and create databases

[Voila](https://github.com/voila-dashboards/voila)-turns Jupyter Notebook into a web application

---

## Installation Guide

As mentioned above, to ensure that there are no errors when running this application, the user or programmer must use Jupyter Notebook to access the application file. 

Additional installs are needed before running the program. Please install in terminal, in a dev environment:

```JupyterLab
conda active dev
python -m ipykernel install --user --name dev
conda install -c conda-forge nodejs
conda deactivate

```
Once installed you should be able to open Jupyter Notebook by the following code:

```
conda activate dev
jupyter notebook
```

To exit out of Jupyter Notebook hit: Ctrl + C

It is important to also install Pandas as the majority of code used is using language from Pandas.

```Pandas
conda activate dev
conda install pandas -y
conda deactive
```
Numpy:
```
pip install numpy
```

PyViz will help build interactive visual modules that will showcase our data.

```
conda install -c plotly plotly=4.13.
conda install -c pyviz hvplot
conda install -c conda-forge nodejs=12
```
The code below will install Jupyterlab dependencies.

```
conda install -c conda-forge jupyterlab=2
jupyter labextension install jupyterlab-plotly@4.13.0 --no-build
jupyter labextension install @jupyter-widgets/jupyterlab-manager plotlywidget@4.13.0 --no-build
jupyter labextension install @pyviz/jupyterlab_pyviz --no-build
jupyter lab build
```
SQLAlchemy will assist in building SQL databases that will host the data that's needed.
```
pip install sqlalchemy
```
This last install will help create a web application from the Jupyter Notebook.
```
conda install -c conda-forge voila -y
```
---

## Usage and Examples

To use the financial database, the repository will need to be cloned from GitHub and into a local repository.

Enter into the dev environment by commanding: 

```
 conda activate dev
```

Please open the 'financial_database' folder using Jupyter Notebook, and use the code:

```
jupyter notebook
```
to access the information in the folder.

![open_repo](https://user-images.githubusercontent.com/84649228/128933869-f6c3af63-2c8e-4a91-812d-ef945949f927.png)

Open the 'etf_analyzer.ipynb' file.

When using the file, each line of code must be individually ran to capture the data. This ensures any data that needs to be pulled gets included in future calculations as we start to build out formulas for analysis. It is important that we do not miss a line of code.

To quickly execute the code, use the keyboard shortcut: Shift + Enter.

The most important piece of code we need to run is the imports. Without these, information may not get pulled correctly.

![imports](https://user-images.githubusercontent.com/84649228/128933908-df85026b-3d05-4083-9125-7deaad04c9eb.png)

In order to start analyzing ETFs, we need to pull in the 'etf.db' as a temporary database using SQLite and creating an engine to interact with the database.

```
database_connection_string = 'sqlite:///etf.db'
engine = sqlalchemy.create_engine(database_connection_string)
```

In this application, we sampled the PayPal (PYPL) data. We called the data using
```
query = """
SELECT * FROM PYPL
"""

pypl_dataframe = pd.read_sql_query(query,con=engine)
```
and by putting it into a Pandas DataFrame, we are able to read the data.

![reading the data](https://user-images.githubusercontent.com/84649228/128934011-5464b18f-f31c-421e-8304-2997c9ed6fc1.png)

To view the data, we create an interactive visualization showcasing the PYPL daily returns.
![PYPL Daily Returns](https://user-images.githubusercontent.com/84649228/128934038-fc6e6e25-9a1d-4dcd-a61d-2cdf72423a2e.png)


Then, we create another visualization to show the cumulative returns for this asset.
![PYPL Cumulative Returns](https://user-images.githubusercontent.com/84649228/128934051-8051deaa-f3df-4a81-ab7b-eb45cab4dd6e.png)


**Optimize Data Access**

In this section, we test how we can access the data and test two ways of pulling data we need using SQL.

The first test is to access the closing prices for PYPL that are greater than 200.
![image](https://user-images.githubusercontent.com/84649228/128934402-18532bf1-b348-4a4b-b67f-e5de4d542503.png)

The second test is to find the top 10 daily returns for PYPL.
![image](https://user-images.githubusercontent.com/84649228/128934440-614e6c2d-8acd-4e96-99f3-c1fb53c2d847.png)


**Analyzing the ETF Porfolio**

In order to analyze the entire portfolio, we need to join each of the four assets in the ETF portfolio into one DataFrame. To do this, we code the following to inner join the tables by the column 'time': 

```
query = """
SELECT * FROM GDOT
INNER JOIN GS ON GDOT.time = GS.time
INNER JOIN PYPL ON GDOT.time = PYPL.time
INNER JOIN SQ ON GDOT.time = SQ.time
"""
```
Next, we analyze the annualized returns and used those returns to calculate the cumulative returns of the ETF portfolio. To showcase the data, we develop a hvPlot to visualized the cumulative return values of the ETF portfolio.
![ETF Portfolio cumulative return](https://user-images.githubusercontent.com/84649228/128933839-dc8809f9-2f11-4964-b0f1-70418c26aaf3.png)


**Deploying a Web Application**

We use Voila to deploy the notebook as a web application. This can be done by doing the following:
![terminal_voila_executed](https://user-images.githubusercontent.com/84649228/128933705-211dc431-42a8-4513-8a04-88cf664cbb62.png)

When the code runs, it will open the notebook as a web application as seen below:
![screenshot_of_voila](https://user-images.githubusercontent.com/84649228/128933795-3b7192f4-ba91-4248-9868-2cb0173ac8ea.png)


---

## Contributors

[Julia Guanzon](www.linkedin.com/in/julia-guanzon)

## License

MIT License
