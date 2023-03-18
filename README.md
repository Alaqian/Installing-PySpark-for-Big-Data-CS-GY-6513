# PySpark for Big Data CS-GY 6513

- [Installing PySpark on your local machine](#Installing-PySpark-on-your-local-machine)
- [Google Colab](#Google-Colab)
  - [Option 1](#Option-1)
  - [Option 2](#Option-2)
- [Dataset used in class](#Dataset-used-in-class)

## Installing PySpark on your local machine

### 1. Install JDK 8

Download link: https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html

You will need to create an account and sign-in in order to download it.

Press start and search for "Edit environment variables for your account"

Click new and add 'JAVA_HOME' with the path for your java jdk folder e.g. C:\Program Files\Java\jdk1.8.0_202 and add 'JRE_HOME' with the path for your java jre folder e.g. C:\Program Files\Java\jre1.8.0_361

![Edit Path Variables](https://user-images.githubusercontent.com/83875912/221330980-8e78f28f-e578-4e6c-b5df-bf34cc241442.png)

### 2. Install JupyterLab Desktop

Download and Install JupyerLab Desktop: [JupyterLab Desktop Installation Guide](https://github.com/jupyterlab/jupyterlab-desktop#installation)

Open the settings dialog from the top right menu. 

![JupyterLab Desktop Settings](https://user-images.githubusercontent.com/83875912/221332625-62128c05-7456-4461-bffc-e50cf4b59731.png)

Go to the `Server` tab and select `Bundled Python environement` or `install Bundled Python environement` if not already installed. Click `Apply & restart`.

![Server](https://user-images.githubusercontent.com/83875912/221332340-96b9c3bf-d7f1-4f34-af85-75d268660388.png)
### 3. Install PySpark
From the launcher on JupyterLab Desktop, click `Terminal`.

PySpark installation using PyPI is as follows:
```cmd
pip install pyspark
pip install pyarrow
```
If you want to install extra dependencies for a specific component, you can install it as below:
```cmd
# Spark SQL
pip install pyspark[sql]
# pandas API on Spark
pip install pyspark[pandas_on_spark] plotly  # to plot your data, you can install plotly together
```
More info about about installing PySpark: [PySpark Installation Guide](https://spark.apache.org/docs/latest/api/python/getting_started/install.html#using-pypi)

### 4. Start Spark Session
Open a new notebook and run the following code to start a new spark session:
```python
import os
import pyspark
import sys
os.environ['PYSPARK_PYTHON'] = sys.executable
os.environ['PYSPARK_DRIVER_PYTHON'] = sys.executable
conf = pyspark.SparkConf()
sc = pyspark.SparkContext(conf=conf)
spark = pyspark.sql.SparkSession(sc)
```

## Google Colab
### Option 1:
Go to https://colab.research.google.com/, open a new notebook and exectue the code belower in a new cell:
```python
"""
Install Dependencies:

1. Java 8
2. Apache Spark with hadoop and
3. Findspark (used to locate the spark in the system)
"""
!apt-get install openjdk-8-jdk-headless -qq > /dev/null
!wget -q http://archive.apache.org/dist/spark/spark-3.1.1/spark-3.1.1-bin-hadoop3.2.tgz
!tar xf spark-3.1.1-bin-hadoop3.2.tgz
!pip install -q findspark

"""
Set Environment Variables:
"""
import os
os.environ["JAVA_HOME"] = "/usr/lib/jvm/java-8-openjdk-amd64"
os.environ["SPARK_HOME"] = "/content/spark-3.1.1-bin-hadoop3.2"

"""
Start a Spark Session
"""
import findspark
findspark.init()
from pyspark.sql import SparkSession
spark = SparkSession.builder.master("local[*]").getOrCreate()
spark.conf.set("spark.sql.repl.eagerEval.enabled", True) # Property used to format output tables better
spark
```
## Option 2

Go to this link, click file and save your own copy and execute the first cell: [Colab PySpark Notebook](https://githubtocolab.com/Alaqian/Installing-PySpark-for-Big-Data-CS-GY-6513/blob/main/Colab%20PySpark%20Notebook.ipynb)

More information on this notebook: [Colab and PySpark](https://colab.research.google.com/drive/1G894WS7ltIUTusWWmsCnF_zQhQqZCDOc#scrollTo=Dd6t0uFzuR4X)
## Dataset used in class

Download dataset used in class: [Electric_Vehicle_Population_Data.csv](https://data.wa.gov/api/views/f6w7-q2d2/rows.csv?accessType=DOWNLOAD) (26.9 MB)

All other datasets used in the class demos and more PySpark resources can be found here: [Spark: The Definitive Guide](https://github.com/databricks/Spark-The-Definitive-Guide)
