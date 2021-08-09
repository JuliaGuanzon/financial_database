# Financial Database

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

[PyViz](https://pyviz.org/) - Tools for data visualizations


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

As we are using Mapbox API to aid in creating an interactive map, you will need to use your MapBox API key to pull in map details. Be sure to have your *.env* file around to use this application.

```
!pip install python-dotenv
```



---

## Usage and Examples

To use the proptech application, the repository will need to be cloned from GitHub and into a local repository.

Enter into the dev environment by commanding: 

```
 conda activate dev
```

Please open the 'proptech_application' folder using Jupyter Notebook, and use the code:

```
jupyter notebook
```
to access the information in the folder.

![image](https://user-images.githubusercontent.com/84649228/127964512-e48b05c7-55bc-4377-ba7c-732093fe47f7.png)

Open the 'san_francisco_housing.ipynb' file.

When using the file, each line of code must be individually ran to capture the data. This ensures any data that needs to be pulled gets included in future calculations as we start to build out formulas for analysis. It is important that we do not miss a line of code.

To quickly execute the code, use the keyboard shortcut: Shift + Enter.

The most important piece of code we need to run is the imports. Without these, information may not get pulled correctly.






---

## Contributors

[Julia Guanzon](www.linkedin.com/in/julia-guanzon)

## License

MIT License
