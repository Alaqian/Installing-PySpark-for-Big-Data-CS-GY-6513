# Installing PySpark for Big Data CS-GY 6513 (on your local machine)

## 1. Install JDK 8

Download link: https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html

You will need to create and account and sign-in in order to download it.

Press start and search for "Edit environment variables for your account"

Click new and add 'JAVA_HOME' with the path for your java folder e.g. C:\Program Files\Java\jdk1.8.0_202 and jre folder 'JRE_HOME' with the path for your java folder e.g. C:\Program Files\Java\jre1.8.0_361

![Edit Path Variables](https://user-images.githubusercontent.com/83875912/221330980-8e78f28f-e578-4e6c-b5df-bf34cc241442.png)

## 2. Install JupyterLab Desktop

Download and Install JupyerLab Desktop: [JupyterLab Desktop Installation Guide](https://github.com/jupyterlab/jupyterlab-desktop#installation)

Open the settings dialog from the to right menu. 

![JupyterLab Desktop Settings](https://user-images.githubusercontent.com/83875912/221332625-62128c05-7456-4461-bffc-e50cf4b59731.png)

Go to `Server` tab and select or install Bundled Python environement (if not already installed). Click `Apply & Restart`.

![Server](https://user-images.githubusercontent.com/83875912/221332340-96b9c3bf-d7f1-4f34-af85-75d268660388.png)
## 3. Install PySpark
[PySpark Installation Guide](https://spark.apache.org/docs/latest/api/python/getting_started/install.html#using-pypi)

From the launcher, click `Terminal` to start a new session.

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
## 4. Start Spark Session
Open a new notebook and run the following code to start a new spark session:
```python
import os
import pyspark
conf = pyspark.SparkConf()
sc = pyspark.SparkContext(conf=conf)
spark = pyspark.sql.SparkSession(sc)
```
